#### Docker 容器中创建文件

```shell
# 以root权限进入容器
~ % docker exec -it --user root dev-oracle /bin/bash
# 创建文件
~ % mkdir xxx.xx
```



#### Nginx 安装

##### 1、拉取镜像

```
~ % docker pull nginx
```

##### 2、创建容器

```shell
# 方法1
~ % docker run -d -p 9870:80 --name dev-nginx -v /Users/ligang/devtools/docker/nginx/conf/nginx.conf:/etc/nginx/nginx.conf:ro -v /Users/ligang/devtools/docker/nginx/content:/usr/share/nginx/html:ro -v /Users/ligang/devtools/docker/nginx/cache:/var/cache/nginx -v /Users/ligang/devtools/docker/nginx/logs:/var/log/nginx nginx:1.18.0

# 方法2
~ % docker run -d -p 8081:80 --name dev-nginx -v /Users/ligang/devtools/docker/nginx/conf/nginx.conf:/etc/nginx/nginx.conf:ro -v /Users/ligang/devtools/docker/nginx/content:/usr/share/nginx/html:ro nginx:1.18.0
```



#### Elasticsearch 安装

##### 1、拉取镜像
```shell
~ % docker pull elasticsearch:7.6.2
```

##### 2、创建容器

```shell
# 方法1
~ % docker run -p 9200:9200 -p 9300:9300 --name dev-elk -e "discovery.type=single-node" -e "cluster.name=elasticsearch" -v /Users/ligang/devtools/docker/elk/elasticsearch/plugins:/usr/share/elasticsearch/plugins -v /Users/ligang/devtools/docker/elk/elasticsearch/data:/usr/share/elasticsearch/data -d elasticsearch:7.6.2 

# 方法2 官方版
~ % docker run -d --name elasticsearch --net somenetwork -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" elasticsearch:tag
```

##### 3、安装插件

```shell
# 安装插件
# 1、进入容器
~ % docker exec -it contain-id /bin/bash
# 2、安装插件
~ % ./bin/elasticsearch-plugin install analysis-icu(插件名称)
```



#### Kibana 安装

```
# 第一种 官方
~ % $ docker run -d --name kibana --net somenetwork -p 5601:5601 kibana:tag

# 第二种 详细配置安装
~ % docker run -d --name dev-kibana -p 5601:5601 --restart=always --log-driver json-file --log-opt max-size=100m --log-opt max-file=2 -v /Users/ligang/devtools/docker/elk/kibana/config/kibana.yml:/usr/share/kibana/config/kibana.yml kibana:7.6.2
```



#### Rocket MQ 安装

##### 1、拉取镜像

```shell
～ % docker pull apacherocketmq/rocketmq
```

##### 2、创建容器

```shell
# 1：创建mqnamesrv
～ % docker run -d -p 9876:9876 -v /Users/ligang/devtools/docker/rocketmq/data/namesrv/logs:/root/logs -v /Users/ligang/devtools/docker/rocketmq/data/namesrv/store:/root/store --name rmqnamesrv -e "MAX_POSSIBLE_HEAP=100000000" apacherocketmq/rocketmq:4.5.0 sh mqnamesrv

# 2：创建broker
～ % docker run -d -p 10911:10911 -p 10909:10909 -v /Users/ligang/devtools/docker/rocketmq/data/broker/logs:/root/logs -v /Users/ligang/devtools/docker/rocketmq/data/broker/store:/root/store -v /Users/ligang/devtools/docker/rocketmq/data/broker/conf/broker.conf:/home/rocketmq/rocketmq-4.5.0/conf/broker.conf --name rmqbroker --link rmqnamesrv:namesrv -e "NAMESRV_ADDR=namesrv:9876" -e "MAX_POSSIBLE_HEAP=200000000" apacherocketmq/rocketmq:4.5.0 sh mqbroker


```



#### Spring Cloud Alibaba

##### 1：拉取容器

```shell
# 拉取容器：
～ % docker pull nacos/nacos-server
```

##### 2：创建容器

```shell
# 创建容器：
# 标准版
～ % docker run --env MODE=standalone --name dev-nacos -d -p 8848:8848 nacos/nacos-server

# 详细版
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
nacos/nacos-server:1.2.1
```

更新时间：2020-03-21



#### Docker 安装postgresql

##### 1：拉取镜像

```shell
~ % docker pull postgres
```

##### 2：创建容器

```shell
~ % docker run -d \
    --name dev-postgres \
    -e POSTGRES_PASSWORD=123456 \
    -e PGDATA=/var/lib/postgresql/data/pgdata \
    -v /Users/ligang/devtools/docker/postgres:/var/lib/postgresql/data \
    -p 5432:5432 \
    postgres
```

更新时间：2020-03-21



#### Docker 安装 Rabbit MQ：

#### 1：拉取镜像

```shell
# 无管理界面
~ % docker pull rabbitmq

# 有管理界面
~ % docker pull rabbitmq:management

```

#### 2：创建容器

```shell

# 无管理界面
~ % docker run -d --hostname my-rabbit --name dev-rabbit -p 5672:5672 -p 15672:15672 -v /Users/ligang/devtools/docker/rabbitmq:/var/lib/rabbitmq -e RABBITMQ_DEFAULT_VHOST=my_vhost -e RABBITMQ_DEFAULT_USER=admin -e RABBITMQ_DEFAULT_PASS=123456 rabbitmq:latest

# 有管理界面
~ % docker run -d --hostname my-rabbit --name dev-rabbit -p 5672:5672 -p 15672:15672 -v /Users/ligang/devtools/docker/rabbitmq:/var/lib/rabbitmq -e RABBITMQ_DEFAULT_VHOST=my_vhost -e RABBITMQ_DEFAULT_USER=admin -e RABBITMQ_DEFAULT_PASS=123456 rabbitmq:3.8.3-management
```

更新时间：2020-03-21



#### Docker 安装 oracle database

##### 1：拉取镜像

```shell
# 拉取image：
~ % docker pull store/oracle/database-enterprise:12.2.0.1
```

##### 2：创建容器

```shell
# 第一种创建oracle容器的方法：
~ % docker run -d -it --name dev-oracle -p 1521:1521 -p 5500:5500  -v /Users/ligang/devtools/docker/oracle/data:/ORCL --env-file /Users/ligang/devtools/docker/oracle/conf/ora.conf store/oracle/database-enterprise:12.2.0.1

# 第二种创建oracle容器的方法(已经连接成功)：
~ % docker login
~ % docker run -d -it --name dev-oracle -p 1521:1521 -p 5500:5500 -v /Users/ligang/devtools/docker/oracle/data:/ORCL store/oracle/database-enterprise:12.2.0.1

# oracle 默认密码： Oradoc_db1
```

##### 3：进入容器创建存放表空间文件的文件夹

```shell
# 进入oracle容器的方法
# 进入容器并连接数据库
~ % docker exec -it dev-oracle bash -c "source /home/oracle/.bashrc; sqlplus /nolog"
# ~ % sqlplus sys/Oradoc_db1@ORCLCDB as sysdba
# 以root权限进入容器
~ % docker exec -it --user root dev-oracle /bin/bash
~ % docker exec -it --user oracle dev-oracle /bin/bash

# 创建表空间存放路径
[root@a3b2f1adcd02 /]# mkdir -p /home/oracle/data/retail
# 给oracle用户赋权，以便创建表空间文件
[root@a3b2f1adcd02 /]# chown -R oracle:oinstall /home/oracle/data/retail/

# 配置环境
[root@5b410880417d /]# vi /etc/profile
# 加在配置文件最后
export ORACLE_HOME=/home/oracle/app/oracle/product/12.2.0.1/dbhome_2
export ORACLE_SID=ORCLCDB
export PATH=$ORACLE_HOME/bin:$PATH
# 软件连接
[root@a3b2f1adcd02 /]#  ln -s $ORACLE_HOME/bin/sqlplus /usr/bin
```

##### 4：创建表空间以及用户

```sql
# 连接数据库
SQL> conn / as sysdba;
# 修改用户密码
SQL> alter user system identified by 123456;
SQL> alter user sys identified by 123456;
SQL> ALTER PROFILE DEFAULT LIMIT PASSWORD_LIFE_TIME UNLIMITED;

# 查看所有表空间
SQL> select tablespace_name,status,contents from user_tablespaces; 
SQL> alter session set container=cdb$root;

SQL> alter session set container=ORCLPDB1;

# 创建表空间
SQL> create tablespace retail datafile '/home/oracle/data/cdb/retail.dbf' size 200M autoextend on next 50M;
SQL> create tablespace retail datafile '/home/oracle/data/pdb/retail.dbf' size 200M autoextend on next 50M;

SQL> create tablespace retail datafile '/home/oracle/data/retail/retail.dbf' size 10M autoextend on maxsize 1G;

# 在表空间上创建用户
# 第一种创建用户的方法
SQL> create user retail identified by 123456 default tablespace retail;
# 第二种创建用户的方法 cdb下
SQL> create user c##retail identified by 123456 default tablespace retail;

# 修改密码
SQL> alter user retail identified by 123456;

# 删除用户
SQL> DROP USER retail CASCADE;

# 给新建的用户赋权
SQL> grant connect,resource,dba to C##RETAIL;

# delete tablespace
SQL> drop tablespace retail including contents and datafiles
```

更新时间：2020-03-21



#### 容器命令：

```shell
~ % docker ps																			# 查看容器
~ % docker ps -a																	# 查看所有容器
~ % docker start [container id]										# 启动容器
~ % docker restart [container id]									# 重启容器
~ % docker stop [container id]										# 停止容器
~ % docker rm [container name]										# 删除容器
~ % docker rm -f [container name]									# 删除运行中的容器

~ % docker inspect [container name]								# 查看docker容器元数据

# 显示日志
-tf																								# 显示日志
--tail																						# 显示日志数量
~ % docker logs -tf --tail 200 [container name]		# 打印docker容器日志

```

更新时间：2019-03-21



#### Docker 运行 mysql：

##### 1：拉取镜像

```
~ % docker pull mysql
```

2：创建容器

```shell
# 第一种
$ docker run -d -v /Users/ligang/devtools/docker/mysql/:/var/lib/mysql -p 3306:3306 --name dev-mysql -e MYSQL_ROOT_PASSWORD=123456 docker.io/mysql

# 第二种（查询忽略表名大小写）
$ docker run --name dev-mysql -v /Users/ligang/devtools/docker/mysql:/var/lib/mysql -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123456 -d docker.io/mysql --lower_case_table_names=1

$ docker run --name dev-mysql-5nd -v /Users/ligang/devtools/docker/mysql_5nd:/var/lib/mysql -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123456 -d docker.io/mysql:5.7.28 --lower_case_table_names=1

# 第三种（设置字符集为utf8mb4）
# 1
$ docker run --name dev-mysql -v /Users/ligang/devtools/docker/mysql:/var/lib/mysql -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123456 -d docker.io/mysql --lower_case_table_names=1 --character-set-server=utf8mb4 --collation-server=utf8mb4_unicode_ci
# 2 配置文件
$ docker run --name dev-mysql -v /Users/ligang/devtools/docker/mysql/data:/var/lib/mysql -v /Users/ligang/devtools/docker/mysql/custom:/etc/mysql/conf.d -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123456 -d mysql:8.0.20 --character-set-server=utf8mb4 --collation-server=utf8mb4_unicode_ci
```

> -p 3306:3306->把容器的mysql端口3306映射到宿主机的3306端口，这样想访问mysql就可以直接访问宿主机的3306端口。
> -v /opt/data/mysql:/var/lib/mysql->把宿主机/opt/data/mysql/目录映射到容器的/var/lib/mysql目录

更新时间：2019-03-21



#### Docker 运行 redis：

##### 1：拉取镜像

```shell
~ % docker pull redis
```

##### 2：创建容器

```shell
~ % # 创建redis容器，并设置密码
~ % docker run --name dev-redis -d -p 6379:6379 -v /Users/ligang/devtools/docker/redis/data:/data redis:latest redis-server --appendonly yes --requirepass "123456"

# 创建redis容器，并挂载配置文件
~ % docker run --name dev-redis -d -p 6379:6379 -v /Users/ligang/devtools/docker/redis/data:/data -v /Users/ligang/devtools/docker/redis/conf/redis.conf:/etc/redis/redis.conf redis:latest redis-server --requirepass "123456"

# 进入redis容器，并且启动redis-cli
# 方法1
~ % docker exec -it [container name] or [container id] redis-cli -h 192.168.74.128 -p 6379
# 方法2
~ % docker exec -it [container name] or [container id] redis-cli

# 进入redis容器
~ % docker exec -it [container name] or [container id] /bin/sh

# 连接设置了密码的redis-server
127.0.0.1:6379> auth password
```

更新时间：2019-03-21



#### Docker 运行 mongo：

##### 1：拉取镜像

```
~ % docker pull mongo
```

##### 2：创建容器

```shell
~ % docker run --name dev-mongo -p 27017:27017 -v /Users/ligang/devtools/docker/mongo/data/configdb:/data/configdb/ -v /Users/ligang/devtools/docker/mongo/data/db/:/data/db/ -d mongo --auth

# 挂载配置文件：-v /Users/ligang/devtools/docker/mongo/data/configdb:/data/configdb/
# 挂载数据文件：-v /Users/ligang/devtools/docker/mongo/data/db/:/data/db/
# 设置mongo需要登陆验证：--auth
```

##### 3：创建mongo用户

```shell
# 进入mongo容器
~ % docker exec -it [container name] or [container id] mongo admin

# 创建数据库及账号
> db.createUser({ user: 'admin', pwd: '123456', roles: [ { role: "userAdminAnyDatabase", db: "admin" } ] });

```

更新时间：2019-03-21



#### Docker 运行 zookeeper

##### 1：拉取镜像

```shell
~ % docker pull zookeeper
```

##### 2：创建容器

```shell
~ % docker run -d -p 2181:2181 -v /Users/ligang/devtools/docker/zookeeper/data/:/data/ --name=learn-zookeeper --privileged zookeeper
```

##### 3：执行进程

```shell
~ % docker exec -it [container id] /bin/bash 
# 进入docker的zookeeper容器，找到zkCli.sh，执行./zkCli.sh
```

更新时间：2019-03-21