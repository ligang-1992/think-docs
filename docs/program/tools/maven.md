##### Maven 环境配置

```
# 输入命令
➜  ~ vim ~/.bash_profile

# 写入配置
# maven
export M2_HOME=/Users/louis/devtools/maven/apache-maven-3.6.3
export PATH=$PATH:$M2_HOME/bin
```



#### oracle jar包无法解析

##### pom.xm 配置本地仓库

```xml
		<repositories>
        <!--阿里云镜像仓库-->
        <repository>
            <id>public</id>
            <name>aliyun nexus</name>
            <url>http://maven.aliyun.com/nexus/content/groups/public/</url>
            <releases>
                <enabled>true</enabled>
            </releases>
        </repository>
        <!--oracle驱动没有发布到中央仓库，只能从此仓库下载-->
        <repository>
            <id>jeecg</id>
            <name>jeecg Repository</name>
            <url>http://maven.jeewx.com/nexus/content/repositories/jeecg</url>
            <snapshots>
                <enabled>false</enabled>
            </snapshots>
        </repository>
    </repositories>

    <pluginRepositories>
        <pluginRepository>
            <id>public</id>
            <name>aliyun nexus</name>
            <url>http://maven.aliyun.com/nexus/content/groups/public/</url>
            <releases>
                <enabled>true</enabled>
            </releases>
            <snapshots>
                <enabled>false</enabled>
            </snapshots>
        </pluginRepository>
    </pluginRepositories>
```



##### maven 本地仓库安装oracle jar包

```shell
~ % mvn install:install-file -DgroupId=com.Oracle -DartifactId=ojdbc14 -Dversion=10.2.0.4.0 -Dpackaging=jar -D file=ojdbc14-10.2.0.4.0.jar

mvn install:install-file -DgroupId=com.rzt -DartifactId=rzt-base -Dversion=1.0.0 -Dpackaging=jar -D file=rzt-base-1.0.0.jar

mvn install:install-file -DgroupId=com.rzt -DartifactId=rzt-starter-cloud -Dversion=1.0.0 -Dpackaging=jar -D file=rzt-starter-cloud-1.0.0.jar

mvn install:install-file -DgroupId=com.rzt -DartifactId=rzt-starter-job -Dversion=1.0.0 -Dpackaging=jar -D file=rzt-starter-job-1.0.0.jar

mvn install:install-file -DgroupId=com.rzt -DartifactId=rzt-starter-lock -Dversion=1.0.0 -Dpackaging=jar -D file=rzt-starter-lock-1.0.0.jar
```



##### maven本地仓库安装jar包

```
➜  ~ mvn install:install-file -DgroupId=com.hnxt -DartifactId=encryptutil -Dversion=1.0 -Dpackaging=jar -Dfile=/Users/louis/.m2/repository/cn/encrypt/util/encryptutil-jar-with-dependencies.jar

安装指定文件到本地仓库命令：mvn install:install-file
-DgroupId=<groupId>       : 设置项目代码的包名(一般用组织名)
-DartifactId=<artifactId> : 设置项目名或模块名 
-Dversion=1.0.0           : 版本号
-Dpackaging=jar           : 什么类型的文件(jar包)
-Dfile=<myfile.jar>       : 指定jar文件路径与文件名(同目录只需文件名)
```

