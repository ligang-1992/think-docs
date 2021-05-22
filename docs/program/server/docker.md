### 容器操作命令

##### 帮助命令

```shell
~ % docker version																# 显示docker容器版本
~ % docker info																		# 显示docker的系统信息，包括镜像和容器的数量
~ % docker [command] --help												# 帮助命令
```

##### 镜像命令

###### 查看镜像

```shell
~ % docker images																	# 显示docker所有镜像
# 注释
REPOSITORY																				# 镜像的仓库源
TAG																								# 镜像的版本
IMAGE ID																					# 镜像的ID
CREATED																						# 镜像的创建时间
SIZE																							# 镜像的大小

# 可选项
Options:
  -a, --all             Show all images (default hides intermediate images)
      --digests         Show digests
  -f, --filter filter   Filter output based on conditions provided
      --format string   Pretty-print images using a Go template
      --no-trunc        Don't truncate output
  -q, --quiet           Only show numeric IDs
```

###### 搜索镜像

```shell
~ % docker search [OPTIONS] TERM										# 搜索docker的镜像
# 可选项
Options:
  -f, --filter filter   Filter output based on conditions provided
      --format string   Pretty-print search using a Go template
      --limit int       Max number of search results (default 25)
      --no-trunc        Don't truncate output
```

###### 拉取镜像命令

```shell
# docker pull [OPTIONS] NAME[:TAG|@DIGEST]
~ % docker pull [image name]											# 拉取docker的镜像											
# 可选项
Options:
  -a, --all-tags                Download all tagged images in the repository
      --disable-content-trust   Skip image verification (default true)
  -q, --quiet                   Suppress verbose output
```

###### 删除镜像

```shell
# docker rmi [OPTIONS] IMAGE [IMAGE...]
~ % docker rmi [image name]												# 删除docker的镜像						
# 可选项
Options:
  -f, --force      Force removal of the image
      --no-prune   Do not delete untagged parents
```

##### 容器命令

###### 查看容器命令

```shell
~ % docker ps																			# 查看容器
# 可选项
Options:
  -a, --all             Show all containers (default shows just running)
  -f, --filter filter   Filter output based on conditions provided
      --format string   Pretty-print containers using a Go template
  -n, --last int        Show n last created containers (includes all states) (default -1)
  -l, --latest          Show the latest created container (includes all states)
      --no-trunc        Don't truncate output
  -q, --quiet           Only display numeric IDs
  -s, --size            Display total file sizes
```

###### 创建容器

```shell
# docker run [OPTIONS] IMAGE [COMMAND] [ARG...]
~ % docker run [image name]												# 创建容器
# 可选项
Options:
      --add-host list                  Add a custom host-to-IP mapping (host:ip)
  -a, --attach list                    Attach to STDIN, STDOUT or STDERR
      --blkio-weight uint16            Block IO (relative weight), between 10 and 1000, or 0 to disable (default 0)
      --blkio-weight-device list       Block IO weight (relative device weight) (default [])
      --cap-add list                   Add Linux capabilities
      --cap-drop list                  Drop Linux capabilities
      --cgroup-parent string           Optional parent cgroup for the container
      --cidfile string                 Write the container ID to the file
      --cpu-period int                 Limit CPU CFS (Completely Fair Scheduler) period
      --cpu-quota int                  Limit CPU CFS (Completely Fair Scheduler) quota
      --cpu-rt-period int              Limit CPU real-time period in microseconds
      --cpu-rt-runtime int             Limit CPU real-time runtime in microseconds
  -c, --cpu-shares int                 CPU shares (relative weight)
      --cpus decimal                   Number of CPUs
      --cpuset-cpus string             CPUs in which to allow execution (0-3, 0,1)
      --cpuset-mems string             MEMs in which to allow execution (0-3, 0,1)
  -d, --detach                         Run container in background and print container ID
      --detach-keys string             Override the key sequence for detaching a container
      --device list                    Add a host device to the container
      --device-cgroup-rule list        Add a rule to the cgroup allowed devices list
      --device-read-bps list           Limit read rate (bytes per second) from a device (default [])
      --device-read-iops list          Limit read rate (IO per second) from a device (default [])
      --device-write-bps list          Limit write rate (bytes per second) to a device (default [])
      --device-write-iops list         Limit write rate (IO per second) to a device (default [])
      --disable-content-trust          Skip image verification (default true)
      --dns list                       Set custom DNS servers
      --dns-option list                Set DNS options
      --dns-search list                Set custom DNS search domains
      --domainname string              Container NIS domain name
      --entrypoint string              Overwrite the default ENTRYPOINT of the image
  -e, --env list                       Set environment variables
      --env-file list                  Read in a file of environment variables
      --expose list                    Expose a port or a range of ports
      --gpus gpu-request               GPU devices to add to the container ('all' to pass all GPUs)
      --group-add list                 Add additional groups to join
      --health-cmd string              Command to run to check health
      --health-interval duration       Time between running the check (ms|s|m|h) (default 0s)
      --health-retries int             Consecutive failures needed to report unhealthy
      --health-start-period duration   Start period for the container to initialize before starting health-retries countdown (ms|s|m|h) (default 0s)
      --health-timeout duration        Maximum time to allow one check to run (ms|s|m|h) (default 0s)
      --help                           Print usage
  -h, --hostname string                Container host name
      --init                           Run an init inside the container that forwards signals and reaps processes
  -i, --interactive                    Keep STDIN open even if not attached
      --ip string                      IPv4 address (e.g., 172.30.100.104)
      --ip6 string                     IPv6 address (e.g., 2001:db8::33)
      --ipc string                     IPC mode to use
      --isolation string               Container isolation technology
      --kernel-memory bytes            Kernel memory limit
  -l, --label list                     Set meta data on a container
      --label-file list                Read in a line delimited file of labels
      --link list                      Add link to another container
      --link-local-ip list             Container IPv4/IPv6 link-local addresses
      --log-driver string              Logging driver for the container
      --log-opt list                   Log driver options
      --mac-address string             Container MAC address (e.g., 92:d0:c6:0a:29:33)
  -m, --memory bytes                   Memory limit
      --memory-reservation bytes       Memory soft limit
      --memory-swap bytes              Swap limit equal to memory plus swap: '-1' to enable unlimited swap
      --memory-swappiness int          Tune container memory swappiness (0 to 100) (default -1)
      --mount mount                    Attach a filesystem mount to the container
      --name string                    Assign a name to the container
      --network network                Connect a container to a network
      --network-alias list             Add network-scoped alias for the container
      --no-healthcheck                 Disable any container-specified HEALTHCHECK
      --oom-kill-disable               Disable OOM Killer
      --oom-score-adj int              Tune host's OOM preferences (-1000 to 1000)
      --pid string                     PID namespace to use
      --pids-limit int                 Tune container pids limit (set -1 for unlimited)
      --privileged                     Give extended privileges to this container
  -p, --publish list                   Publish a container's port(s) to the host
  -P, --publish-all                    Publish all exposed ports to random ports
      --read-only                      Mount the container's root filesystem as read only
      --restart string                 Restart policy to apply when a container exits (default "no")
      --rm                             Automatically remove the container when it exits
      --runtime string                 Runtime to use for this container
      --security-opt list              Security Options
      --shm-size bytes                 Size of /dev/shm
      --sig-proxy                      Proxy received signals to the process (default true)
      --stop-signal string             Signal to stop a container (default "SIGTERM")
      --stop-timeout int               Timeout (in seconds) to stop a container
      --storage-opt list               Storage driver options for the container
      --sysctl map                     Sysctl options (default map[])
      --tmpfs list                     Mount a tmpfs directory
  -t, --tty                            Allocate a pseudo-TTY
      --ulimit ulimit                  Ulimit options (default [])
  -u, --user string                    Username or UID (format: <name|uid>[:<group|gid>])
      --userns string                  User namespace to use
      --uts string                     UTS namespace to use
  -v, --volume list                    Bind mount a volume
      --volume-driver string           Optional volume driver for the container
      --volumes-from list              Mount volumes from the specified container(s)
  -w, --workdir string                 Working directory inside the container
```

###### 删除容器

```shell
# docker rm [OPTIONS] CONTAINER [CONTAINER...]
~ % docker rm [container name]										# 删除容器
~ % docker rm -f [container name]									# 删除运行中的容器
# 可选项
Options:
  -f, --force     Force the removal of a running container (uses SIGKILL)
  -l, --link      Remove the specified link
  -v, --volumes   Remove anonymous volumes associated with the container
```

###### 启动容器

```shell
~ % docker start [container id]										# 启动容器
~ % docker restart [container id]									# 重启容器
~ % docker stop [container id]										# 停止容器


~ % docker inspect [container name]								# 查看docker容器元数据

# 显示日志
-tf																								# 显示日志
--tail																						# 显示日志数量
~ % docker logs -tf --tail 200 [container name]		# 打印docker容器日志

```

##### 其他常用命令

```shell
# 以root权限进入容器
# 方法一
~ % docker exec -it --user root dev-oracle /bin/bash
# 方法二
~ % docker attach [container id]

# 拷贝docker容器中的文件
# docker cp [OPTIONS] CONTAINER:SRC_PATH DEST_PATH|-
# docker cp [OPTIONS] SRC_PATH|- CONTAINER:DEST_PATH
~ % docker cp [container id]/[filepath] /[target path]

# 创建文件
~ % mkdir xxx.xx

# 查看容器占用磁盘大小
~ % docker system df

# 查看单个image、container大小：
~ % docker system df -v
```



### 软件安装命令

```shell
~ % docker pull xuxueli/xxl-job-admin:2.3.0
# 第一种
~ % docker run -d -p 8080:8080 \
		-v $PWD/devtools/docker/xxl-job/logs:/data/applogs \
		--name xxl-job-admin -d xuxueli/xxl-job-admin:2.3.0

# 第二种
~ % docker run  -p 9080:8080 --name xxl-job-admin \
		-e PARAMS="--spring.datasource.url=jdbc:mysql://127.0.0.1:3306/xxl_job?useUnicode=true&characterEncoding=UTF-8&autoReconnect=true&serverTimezone=Asia/Shanghai spring.datasource.username=root --spring.datasource.password=123456" \
    -v $PWD/devtools/docker/xxl-job/logs:/data/applogs \
    xuxueli/xxl-job-admin:2.3.0

--spring.datasource.url=jdbc:mysql://jeecg-boot-mysql:3306/xxl_job?Unicode=true&characterEncoding=UTF-8&useSSL=false --spring.datasource.username=root --spring.datasource.password=123456 --xxl.admin.login=false
```



##### SonarQube

```shell
# 默认数据库
~ > docker run -d --name sonarqube \
    -p 9000:9000 \
    -v $PWD/devtools/docker/sonarqube/data:/opt/sonarqube/data \
    -v $PWD/devtools/docker/sonarqube/extensions:/opt/sonarqube/extensions \
    -v $PWD/devtools/docker/sonarqube/logs:/opt/sonarqube/logs \
    sonarqube:8.9.0-community

# 配置数据库
~ > docker run -d --name sonarqube \
    -p 9000:9000 \
    -e SONAR_JDBC_URL=jdbc:postgresql://127.0.0.1:3306/sonarqube \
    -e SONAR_JDBC_USERNAME=root \
    -e SONAR_JDBC_PASSWORD=123456 \
    -v $PWD/devtools/docker/sonarqube/data:/opt/sonarqube/data \
    -v $PWD/devtools/docker/sonarqube/extensions:/opt/sonarqube/extensions \
    -v $PWD/devtools/docker/sonarqube/logs:/opt/sonarqube/logs \
    sonarqube:8.9.0-community
```



#### Centos

```shell
# 第一步 ssh默认的端口为22,我们将docker中centos的22端口映射到宿主机的1022端口
~ > docker run -d -p 1022:22 --name dev-centos --privileged=true -v $PWD/devtools/docker/centos/data:/data centos:8.3.2011 /usr/sbin/init

# 第二步：安装常用工具
~ > yum install -y openssh-server vim lrzsz wget gcc-c++ pcre pcre-devel zlib zlib-devel ruby openssl openssl-devel patch bash-completion zlib.i686 libstdc++.i686 lsof unzip zip net-tools

# 第三步：service安装
yum install initscripts  

# 第四步：ifconfig安装
yum install net-tools.x86_64

# 第五步：ssh安装
sshd rpm -qa | grep ssh
yum install openssh-server 
service sshd restart
netstat -antp | grep sshd
```



#### Kafka

##### 安装

###### 步骤一：拉取镜像

```
~ % docker pull wurstmeister/kafka:2.13-2.7.0
```

###### 步骤二：创建容器

```shell
# 方法一
~ % docker run -d --restart=always --log-driver json-file --log-opt max-size=100m --log-opt max-file=2 \
	--name dev-kafka -p 9092:9092 \
	-e KAFKA_BROKER_ID=0 -e KAFKA_ZOOKEEPER_CONNECT=127.0.0.1:2181/kafka \
	-e KAFKA_ADVERTISED_LISTENERS=PLAINTEXT://127.0.0.1:9092 \
	-e KAFKA_LISTENERS=PLAINTEXT://0.0.0.0:9092 \
	-v /etc/localtime:/etc/localtime wurstmeister/kafka:2.13-2.7.0
 
```



#### Nginx

##### 安装

###### 步骤一：拉取镜像

```
~ % docker pull nginx
```

###### 步骤二：创建容器

```shell
# 方法一
~ % docker run --rm -d -p 9870:80 --name dev-nginx -v $PWD/devtools/docker/nginx/conf/nginx.conf:/etc/nginx/nginx.conf:ro nginx:1.19.1

# 方法二
~ % docker run -d -p 9870:80 --name dev-nginx -v $PWD/devtools/docker/nginx/content:/usr/share/nginx/html:ro -v $PWD/devtools/docker/nginx/conf/nginx.conf:/etc/nginx/nginx.conf:ro  -v $PWD/devtools/docker/nginx/cache:/var/cache/nginx -v $PWD/devtools/docker/nginx/pid:/var/run nginx:1.19.10

~ % docker run -d -p 9870:80 --name nginx \
	-v $PWD/devtools/docker/nginx/content:/usr/share/nginx/html:ro \
	-v $PWD/devtools/docker/nginx/conf/nginx.conf:/etc/nginx/nginx.conf:ro \
	-v $PWD/devtools/docker/nginx/cache:/var/cache/nginx \
	-v $PWD/devtools/docker/nginx/pid:/var/run nginx:1.20.0
```



#### ELASTIC (ELK) STACK：Elasticsearch

##### 安装

###### 步骤一：拉取镜像
```shell
~ % docker pull elasticsearch:7.6.2
```

###### 步骤二：创建容器

```shell
# 方法1
~ % docker run -p 9200:9200 -p 9300:9300 --name dev-elk -e "discovery.type=single-node" -e "cluster.name=elasticsearch" -v $PWD/devtools/docker/elk/elasticsearch/plugins:/usr/share/elasticsearch/plugins -v $PWD/devtools/docker/elk/elasticsearch/data:/usr/share/elasticsearch/data -d elasticsearch:7.6.2 

# 方法2 官方版
~ % docker run -d --name elasticsearch --net somenetwork -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" elasticsearch:tag
```

###### 步骤三：安装插件

```shell
# 安装插件
# 1、进入容器
~ % docker exec -it contain-id /bin/bash
# 2、安装插件
~ % ./bin/elasticsearch-plugin install analysis-icu(插件名称)
```



#### ELASTIC (ELK) STACK：Kibana

##### 安装

```shell
# 方法一 官方
~ % $ docker run -d --name kibana --net somenetwork -p 5601:5601 kibana:tag

# 方法二 详细配置安装
~ % docker run -d --name dev-kibana -p 5601:5601 --restart=always --log-driver json-file --log-opt max-size=100m --log-opt max-file=2 -v $PWD/devtools/docker/elk/kibana/config/kibana.yml:/usr/share/kibana/config/kibana.yml kibana:7.6.2
```



#### Apache RocketMQ

##### 安装

###### 步骤一：拉取镜像

```shell
～ % docker pull apacherocketmq/rocketmq
```

###### 步骤二：创建容器

```shell
# 步骤一：创建mqnamesrv
～ % docker run -d -p 9876:9876 -v $PWD/devtools/docker/rocketmq/data/namesrv/logs:/root/logs -v $PWD/devtools/docker/rocketmq/data/namesrv/store:/root/store --name rmqnamesrv -e "MAX_POSSIBLE_HEAP=100000000" apacherocketmq/rocketmq:4.5.0 sh mqnamesrv

# 步骤二：创建broker
～ % docker run -d -p 10911:10911 -p 10909:10909 -v $PWD/devtools/docker/rocketmq/data/broker/logs:/root/logs -v $PWD/devtools/docker/rocketmq/data/broker/store:/root/store -v $PWD/devtools/docker/rocketmq/data/broker/conf/broker.conf:/home/rocketmq/rocketmq-4.5.0/conf/broker.conf --name rmqbroker --link rmqnamesrv:namesrv -e "NAMESRV_ADDR=namesrv:9876" -e "MAX_POSSIBLE_HEAP=200000000" apacherocketmq/rocketmq:4.5.0 sh mqbroker
```



#### Spring Cloud Alibaba

##### 安装

###### 步骤一：拉取容器

```shell
# 拉取容器：
～ % docker pull nacos/nacos-server
```

###### 步骤二：创建容器

```shell
# 创建容器：
# 标准版
～ % docker run --env MODE=standalone --name dev-nacos -d -p 8848:8848 nacos/nacos-server

# 详细版
~ % docker run --name dev-nacos -d -p 8848:8848 --privileged=true --restart=always \
-e JVM_XMS=256m -e JVM_XMX=256m -e MODE=standalone -e PREFER_HOST_MODE=hostname \
-v $PWD/devtools/docker/nacos/logs:/home/nacos/logs nacos/nacos-server:2.0.0
```

更新时间：2020-03-21



#### RabbitMQ

##### 安装

###### 步骤一：拉取镜像

```shell
# 无管理界面
~ % docker pull rabbitmq

# 有管理界面
~ % docker pull rabbitmq:management
```

###### 步骤二：创建容器

```shell
# 无管理界面
~ % docker run -d --hostname my-rabbit --name dev-rabbit -p 5672:5672 -p 15672:15672 -v $PWD/devtools/docker/rabbitmq:/var/lib/rabbitmq -e RABBITMQ_DEFAULT_VHOST=my_vhost -e RABBITMQ_DEFAULT_USER=admin -e RABBITMQ_DEFAULT_PASS=123456 rabbitmq:latest

# 有管理界面
~ % docker run -d --hostname dev-rabbit --name dev-rabbit -p 5672:5672 -p 15672:15672 -v $PWD/devtools/docker/rabbitmq:/var/lib/rabbitmq -e RABBITMQ_DEFAULT_VHOST=dev_vhost -e RABBITMQ_DEFAULT_USER=admin -e RABBITMQ_DEFAULT_PASS=123456 rabbitmq:3.8.9-management
```

更新时间：2020-03-21



#### MariaDB

```shell
docker run --name mariadb \
	-p 127.0.0.1:3306:3306 \
	-v $PWD/devtools/docker/mariadb/datadir:/var/lib/mysql \
	-v $PWD/devtools/docker/mariadb/custom:/etc/mysql/conf.d \
	-e MYSQL_ROOT_PASSWORD=123456 \
	-d mariadb:10.6.0 --character-set-server=utf8mb4 --collation-server=utf8mb4_unicode_ci
```





#### Apache ZooKeeper

##### 安装

###### 步骤一：拉取镜像

```shell
~ % docker pull zookeeper
```

###### 步骤二：创建容器

```shell
# 第一种
~ % docker run -d -p 2181:2181 -v $PWD/devtools/docker/zookeeper/data/:/data/ --name=dev-zookeeper --privileged zookeeper

# 第二种
~ % docker run -d -p 2181:2181 --name dev-zookeeper \
-v $(pwd)/devtools/docker/zookeeper/conf/zoo.cfg:/conf/zoo.cfg \
-v $(pwd)/devtools/docker/zookeeper/logs:/logs/zookeeper.log --restart always \
-e ZOO_LOG4J_PROP="INFO,ROLLINGFILE" \
-e JVMFLAGS="-Dzookeeper.serverCnxnFactory=org.apache.zookeeper.server.NettyServerCnxnFactory" \
-e JVMFLAGS="-Xmx1024m" zookeeper:3.7.0
```

###### 步骤三：执行进程

```shell
~ % docker exec -it [container id] /bin/bash 
# 进入docker的zookeeper容器，找到zkCli.sh，执行./zkCli.sh

# 启动zookeeper客户端
root@44bf9b0d1b30:/apache-zookeeper-3.6.2-bin/bin# ./zkCli.sh
```

更新时间：2019-03-21