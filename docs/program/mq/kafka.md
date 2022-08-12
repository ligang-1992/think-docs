##### 脚本启动kafka

> 启动命令：./xxx.sh start 
>
> 停止命令：./xxx.sh stop 
>
> ./xxx.sh 帮助命令：help 

```sh
#!/bin/bash

#export KAFKA_HOME=$PATH
export KAFKA_HOME=/Users/luffy/devtools/kafka/kafka_2.13-3.1.0

case $1 in
    start)
        $KAFKA_HOME/bin/zookeeper-server-start.sh -daemon $KAFKA_HOME/config/zookeeper.properties
        $KAFKA_HOME/bin/kafka-server-start.sh -daemon $KAFKA_HOME/config/server.properties
        echo "-- Successfully started --"
    ;;

    stop)
        $KAFKA_HOME/bin/zookeeper-server-stop.sh
        $KAFKA_HOME/bin/kafka-server-stop.sh
        echo "-- Successfully stopped --"
    ;;

    help)
        echo "require start|stop" ;;
esac
```



### Using the Command Line

In this example, we will create a Apache Kafka client instance that will connect to the server instance that is running on the same docker network as the client.

#### Step 1: Create a network

```sh
$ docker network create dev-env --driver bridge
```

#### Step 2: Launch the Zookeeper server instance

Use the `--network app-tier` argument to the `docker run` command to attach the Zookeeper container to the `app-tier` network.

```sh
$ docker run -d -p 2181:2181 --name zookeeper-server \
    --restart always \
    --network dev-env \
    -e ALLOW_ANONYMOUS_LOGIN=yes \
    -e ZOO_LOG4J_PROP="INFO,ROLLINGFILE" \
    -e JVMFLAGS="-Dzookeeper.serverCnxnFactory=org.apache.zookeeper.server.NettyServerCnxnFactory" \
    -v /Users/luffy/Docker/zookeeper/conf/zoo.cfg:/conf/zoo.cfg \
    -v /Users/luffy/Docker/zookeeper/logs:/logs/zookeeper.log \
    zookeeper:3.8.0
```

#### Step 2: Launch the Apache Kafka server instance

Use the `--network app-tier` argument to the `docker run` command to attach the Apache Kafka container to the `app-tier` network.

```sh
$ docker run -d -p 9092:9092 --name kafka-server \
    --network dev-env \
    -e ALLOW_PLAINTEXT_LISTENER=yes \
    -e KAFKA_CFG_ZOOKEEPER_CONNECT=zookeeper-server:2181 \
    bitnami/kafka:3.1.1
```

#### Step 3: Launch your Apache Kafka client instance

Finally we create a new container instance to launch the Apache Kafka client and connect to the server created in the previous step:

```sh
$ docker run -it --rm \
    --network dev-env \
    -e KAFKA_CFG_ZOOKEEPER_CONNECT=zookeeper-server:2181 \
    bitnami/kafka:3.1.1 \
    kafka-topics.sh --list --bootstrap-server kafka-server:9092
```

