#### oracle jar包无法解析

##### 1、pom.xm 配置本地仓库

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

##### 2、maven 本地仓库安装oracle jar包

```shell
~ % mvn install:install-file -DgroupId=com.Oracle -DartifactId=ojdbc14 -Dversion=10.2.0.4.0 -Dpackaging=jar -D file=ojdbc14-10.2.0.4.0.jar
```

