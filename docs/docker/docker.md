#### 2020-04-03

###### Spring Cloud Alibaba

```
拉取容器：
～ % docker pull nacos/nacos-server

创建容器：
～ % docker run --env MODE=standalone --name dev-nacos -d -p 8848:8848 nacos/nacos-server
~ % docker  run \
--name dev-nacos -d \
-p 8848:8848 \
--privileged=true \
--restart=always \
-e JVM_XMS=256m \
-e JVM_XMX=256m \
-e MODE=standalone \
-e PREFER_HOST_MODE=hostname \
-v /Users/ligang/devtools/docker/nacos/logs:/home/nacos/logs \
nacos/nacos-server
```



#### 2020-04-02

###### Docker 安装

```
拉取镜像

创建容器：
~ % docker run -d \
    --name dev-postgres \
    -e POSTGRES_PASSWORD=123456 \
    -e PGDATA=/var/lib/postgresql/data/pgdata \
    -v /Users/ligang/devtools/docker/postgres:/var/lib/postgresql/data \
    -p 5432:5432 \
    postgres
```



#### 2020-01-18

Docker 安装 rabbitmq

```
第一种安装（无管理界面）：
拉去image：
~ % docker pull rabbitmq

创建容器：
~ % docker run -d --hostname my-rabbit --name dev-rabbit -p 5672:5672 -p 15672:15672 -v /Users/ligang/devtools/docker/rabbitmq:/var/lib/rabbitmq -e RABBITMQ_DEFAULT_VHOST=my_vhost -e RABBITMQ_DEFAULT_USER=admin -e RABBITMQ_DEFAULT_PASS=123456 rabbitmq:latest

第二种安装（有管理界面）：
~ % docker pull rabbitmq:management

创建容器：
~ % docker run -d --hostname my-rabbit --name dev-rabbit -p 5672:5672 -p 15672:15672 -v /Users/ligang/devtools/docker/rabbitmq:/var/lib/rabbitmq -e RABBITMQ_DEFAULT_VHOST=my_vhost -e RABBITMQ_DEFAULT_USER=admin -e RABBITMQ_DEFAULT_PASS=123456 rabbitmq:management
```



#### 2019-11-05

###### Docker 安装 oracle database

```
拉取image：
~ % docker pull store/oracle/database-enterprise:12.2.0.1

创建容器：
第一种创建oracle容器的方法：
~ % docker run -d -it --name dev-oracle -p 1521:1521 -p 5500:5500  -v /Users/ligang/devtools/docker/oracle/data:/ORCL --env-file /Users/ligang/devtools/docker/oracle/conf/ora.conf store/oracle/database-enterprise:12.2.0.1

第二种创建oracle容器的方法(已经连接成功)：
~ % docker login
~ % docker run -d -it --name dev-oracle -p 1521:1521 -p 5500:5500  -v /Users/ligang/devtools/docker/oracle/data:/ORCL store/oracle/database-enterprise:12.2.0.1

~ % docker exec -it dev-oracle bash -c "source /home/oracle/.bashrc; sqlplus /nolog"
~ % sqlplus sys/Oradoc_db1@ORCLCDB as sysdba

oracle 默认密码： Oradoc_db1
```



#### 2019-03-21

###### 容器命令：

```
docker ps：查看容器

docker ps -a：查看所有容器

docker start [container id]：启动容器

docker restart [container id]：重启容器

docker stop [container id]：停止容器

docker rm [container name]：删除容器

docker rm -f [container name]：删除运行中的容器
```



###### Docker 运行 mysql：

```
# 第一种
$ docker run -d -v /Users/ligang/devtools/docker/mysql/:/var/lib/mysql -p 3306:3306 --name dev-mysql -e MYSQL_ROOT_PASSWORD=123456 docker.io/mysql

# 第二种（查询忽略表名大小写）
$ docker run --name dev-mysql -v /Users/ligang/devtools/docker/mysql:/var/lib/mysql -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123456 -d docker.io/mysql --lower_case_table_names=1

$ docker run --name dev-mysql-5nd -v /Users/ligang/devtools/docker/mysql_5nd:/var/lib/mysql -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123456 -d docker.io/mysql:5.7.28 --lower_case_table_names=1

# 第三种（设置字符集为utf8mb4）
$ docker run --name dev-mysql -v /Users/ligang/devtools/docker/mysql:/var/lib/mysql -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123456 -d docker.io/mysql --lower_case_table_names=1 --character-set-server=utf8mb4 --collation-server=utf8mb4_unicode_ci

```

-p 3306:3306->把容器的mysql端口3306映射到宿主机的3306端口，这样想访问mysql就可以直接访问宿主机的3306端口。
-v /opt/data/mysql:/var/lib/mysql->把宿主机/opt/data/mysql/目录映射到容器的/var/lib/mysql目录



###### Docker 运行 redis：

```
$ docker run -v /Users/ligang/devtools/docker/redis/data:/data  -p 6379:6379 --name dev-redis -d redis:latest redis-server --appendonly yes --requirepass "123456"

$ docker exec -it finance-redis redis-cli -h 192.168.74.128 -p 6379
```



###### Docker 运行 mongo：

```
$ docker run --name dev-mongo -p 27017:27017 -v /Users/ligang/devtools/docker/mongo/data/configdb:/data/configdb/ -v /Users/ligang/devtools/docker/mongo/data/db/:/data/db/ -d mongo --auth

挂载配置文件：-v /Users/ligang/devtools/docker/mongo/data/configdb:/data/configdb/
挂载数据文件：-v /Users/ligang/devtools/docker/mongo/data/db/:/data/db/
设置mongo需要登陆验证：--auth

docker run --name work-mongo -p 27017:27017 -v /Users/ligang/devtools/docker/work/mongo/data/configdb:/data/configdb/ -v /Users/ligang/devtools/docker/work/mongo/data/db/:/data/db/ -d mongo
```

创建mongo用户

```
# 进入mongo容器
$  docker exec -it dev-mongo mongo admin

# 创建数据库及账号
> db.createUser({ user: 'admin', pwd: '123456', roles: [ { role: "userAdminAnyDatabase", db: "admin" } ] });

```



Docker 运行 zookeeper

```
$ docker run -d -p 2181:2181 -v /Users/ligang/devtools/docker/zookeeper/data/:/data/ --name=learn-zookeeper --privileged zookeeper

$ docker exec -it [zookeeper容器id] /bin/bash 
	进入docker的zookeeper容器，找到zkCli.sh，执行./zkCli.sh
```

