#### PostgreSQL

##### 安装

###### 步骤一：拉取镜像

```shell
~ % docker pull postgres
```

###### 步骤二：创建容器

```shell
~ % docker run -d \
    --name postgres \
    -p 5432:5432 \
    -e POSTGRES_USER=root \
    -e POSTGRES_PASSWORD=123456 \
    -e TZ=PRC \
    -e PGDATA=/var/lib/postgresql/data/pgdata \
    -v $PWD/devtools/docker/postgres:/var/lib/postgresql/data \
    postgres:13.2
```

更新时间：2020-03-21