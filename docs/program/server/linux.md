#### 2019-05-01	09:28

##### CentOS 7 内核更新后删除旧内核

###### 0.当前

```shell
# uname -sr Linux 3.10.0-123.20.1.el7.x86_64
```

###### 1.搜索查询

```shell
# rpm -q kernel kernel-3.10.0-123.el7.x86_64 kernel-3.10.0-123.20.1.el7.x86_64 kernel-devel-3.10.0-123.el7.x86_64
```

###### 2.删除

```shell
倾向于 
# yum remove kernel-3.10.0-123.el7.x86_64 kernel-devel-3.10.0-123.el7.x86_64 
或者 
# rpm -e kernel-3.10.0-123.el7.x86_64
```

###### 3.定量

```shell
# vi /etc/yum.conf  修改该项值 installonly_limit=5
```

###### 4.重启

```shell
# reboot
```

###### 5.查看

```shell
# rpm -qa|grep kernel*
```



#### 2018-12-15	15:40

##### Linux 设置别名，快捷命令

```shell
# vi ~/.bashrc alias 快捷名='程序路径' 
```



#### 2018-12-13	10：31

##### SQL Server 安装：

下载 Microsoft SQL Server 2017 Red Hat 存储库配置文件：

```shell
# sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo 
```

工作电脑本地数据库密码：admin2018.



##### centos 重启网卡：

```shell
# service network restart 
```

##### centos 网络错误：

```shell
# vi /etc/resolv.conf 输入以下内容： #主DNS nameserver 8.8.8.8 #备DNS nameserver 8.8.4.4 
```



#### 2018-12-10	23：11

##### Redis 安装：

###### 1、安装编译环境：

```shell
# yum install gcc-c++ 
```

###### 2、下载redis并解压：

```shell
# tar -zxvf redis... 
# cd redis...

# 编译：
# make 
```

###### 3、安装到目录：

```shell
# make PREFIX=/usr/local/redis install 

# 把配置文件复制到安装目录：
# cp redis.conf /usr/local/redis/ 
```

###### 4、启动和关闭 redis 服务：

```shell
# ./bin/redis-server 

# 查看redis 是否运行命令：
# ps -ef | grep -i redis 
```



#### 2018-12-10	以前

Centos升级到7之后，内置的防火墙已经从iptables变成了firewalld。所以，端口的开启还是要从两种情况来说明的，即iptables和firewalld。更多关于CentOs防火墙的最新内容，请参考Redhat官网。

##### 一、iptables

###### 1.打开/关闭/重启防火墙

```shell
# 开启防火墙(重启后永久生效)：
# chkconfig iptables on 

# 关闭防火墙(重启后永久生效)：
# chkconfig iptables off 

# 开启防火墙(即时生效，重启后失效)：
# service iptables start 

# 关闭防火墙(即时生效，重启后失效)：
# service iptables stop 

# 重启防火墙:
# service iptables restartd
```

###### 2.查看打开的端口

```shell
# /etc/init.d/iptables status 
```

###### 3.打开某个端口(以8080为例)

```shell
# 1.开启端口
# iptables -A INPUT -p tcp --dport 8080 -j ACCEPT  

# 2.保存并重启防火墙
# /etc/rc.d/init.d/iptables save /etc/init.d/iptables restart 
```

###### 4.打开49152~65534之间的端口

```shell
# iptables -A INPUT -p tcp --dport 49152:65534 -j ACCEPT   
```

同样，这里需要对设置进行保存，并重启防火墙。

###### 5.其他打开方式

```shell
# 我们还可以通过修改/etc/sysconfig/iptables文件的方式开启端口，如下
# vi /etc/sysconfig/iptables 

# 然后在文件中增加一行
# -A RH-Firewall-1-INPUT -m state –state NEW -m tcp -p tcp –dport 8080 -j ACCEPT 

# 参数说明:
–A 参数就看成是添加一条规则
–p 指定是什么协议，我们常用的tcp 协议，当然也有udp，例如53端口的DNS
–dport 就是目标端口，当数据从外部进入服务器为目标端口
–sport 数据从服务器出去，则为数据源端口使用
–j 就是指定是 ACCEPT -接收 或者 DROP 不接收
```



##### 二、firewalld

Centos7默认安装了firewalld，如果没有安装的话，可以使用 yum install firewalld firewalld-config进行安装。

###### 1.启动防火墙

```shell
# systemctl start firewalld  
```

###### 2.禁用防火墙

```
# systemctl stop firewalld 
```

###### 3.设置开机启动

```
# systemctl enable firewalld 
```

###### 4.停止并禁用开机启动

```
# sytemctl disable firewalld 
```

###### 5.重启防火墙

```
# firewall-cmd --reload 
```

###### 6.查看状态

```
# systemctl status firewalld 
# 或者
# firewall-cmd --state 
```

###### 7.查看版本

```
# firewall-cmd --version 
```

###### 8.查看帮助

```
# firewall-cmd --help 
```

###### 9.查看区域信息

```
# firewall-cmd --get-active-zones 
```

###### 10.查看指定接口所属区域信息

```
# firewall-cmd --get-zone-of-interface=eth0 
```

###### 11.拒绝所有包

```
# firewall-cmd --panic-on 
```

###### 12.取消拒绝状态

```
# firewall-cmd --panic-off 
```

###### 13.查看是否拒绝

```
# firewall-cmd --query-panic 
```

###### 14.将接口添加到区域(默认接口都在public)

```
# firewall-cmd --zone=public --add-interface=eth0(永久生效再加上 --permanent 然后reload防火墙) 
```

15.设置默认接口区域

```
# firewall-cmd --set-default-zone=public(立即生效，无需重启) 
```

16.更新防火墙规则

```
# firewall-cmd --reload
# 或
# firewall-cmd --complete-reload
(两者的区别就是第一个无需断开连接，就是firewalld特性之一动态添加规则，第二个需要断开连接，类似重启服务)
```

###### 17.查看指定区域所有打开的端口

```
# firewall-cmd --zone=public --list-ports 
```

###### 18.在指定区域打开端口（记得重启防火墙）

```
# firewall-cmd --zone=public --add-port=80/tcp(永久生效再加上 --permanent) 

# 说明：
–zone 作用域
–add-port=8080/tcp 添加端口，格式为：端口/通讯协议
–permanent #永久生效，没有此参数重启后失效
```

```
快捷键：
# 查看监听(Listen)的端口
# netstat -lntp

# 查看所有建立的TCP连接
# netstat -antp

# 查看所有运行中的服务的详细信息
# netstat -tulpn

# 显示所有进程
# ps -ef

# 显示使用内存的进程
# ps -aux

# 查看内存使用说明 (shift+m 按照排名)
# top
```

###### redis 关闭：

```
# 1.kill redis进程 
# 2.redis-cli shutdown
```

###### CentOS7安装iptables防火墙

```
# CentOS7默认的防火墙不是iptables,而是firewalle.
```

###### 1、安装iptable iptable-service

```
# 先检查是否安装了
# iptables service iptables status  

# 安装
# iptables yum install -y iptables  

# 升级iptables（安装的最新版本则不需要）
# yum update iptables   

# 安装
# iptables-services yum install iptables-services 
```

###### 2、禁用/停止自带的firewalld服务

```
# 停止firewalld服务
# systemctl stop firewalld  

# 禁用firewalld服务
# systemctl mask firewalld 
```

###### 3、设置现有规则

```
# 查看iptables现有规则
# iptables -L -n

# 先允许所有,不然有可能会杯具
# iptables -P INPUT ACCEPT

# 清空所有默认规则
# iptables -F

# 清空所有自定义规则
# iptables -X

# 所有计数器归0
# iptables -Z

# 允许来自于lo接口的数据包(本地访问)
# iptables -A INPUT -i lo -j ACCEPT

# 开放22端口
# iptables -A INPUT -p tcp --dport 22 -j ACCEPT

# 开放21端口(FTP)
# iptables -A INPUT -p tcp --dport 21 -j ACCEPT

# 开放80端口(HTTP)
# iptables -A INPUT -p tcp --dport 80 -j ACCEPT

# 开放443端口(HTTPS)
# iptables -A INPUT -p tcp --dport 443 -j ACCEPT

# 允许ping
# iptables -A INPUT -p icmp --icmp-type 8 -j ACCEPT

# 允许接受本机请求之后的返回数据 RELATED,是为FTP设置的
# iptables -A INPUT -m state --state  RELATED,ESTABLISHED -j ACCEPT

# 其他入站一律丢弃
# iptables -P INPUT DROP

# 所有出站一律绿灯
# iptables -P OUTPUT ACCEPT

# 所有转发一律丢弃
# iptables -P FORWARD DROP
```

###### 4、其他规则设定

```
# 如果要添加内网ip信任（接受其所有TCP请求） 
# iptables -A INPUT -p tcp -s 45.96.174.68 -j ACCEPT  

# 过滤所有非以上规则的请求 
# iptables -P INPUT DROP  

# 要封停一个IP，使用下面这条命令： 
# iptables -I INPUT -s ... -j DROP  

# 要解封一个IP，使用下面这条命令: 
# iptables -D INPUT -s ... -j DROP 
```

###### 5、保存规则设定

```
# 保存上述规则
# service iptables save 
```

###### 6、开启iptables服务 

```
# 注册iptables服务
# 相当于以前的 chkconfig iptables on 
# systemctl enable iptables.service  

# 开启服务
# systemctl start iptables.service  

# 查看状态
# systemctl status iptables.service 
```

###### 7、映射端口（如将mysql默认的3306端口映射成1306对外提供服务）

```
# iptables -t mangle -I PREROUTING -p tcp --dport 1306 -j MARK --set-mark 883306
# iptables -t nat -I PREROUTING -p tcp --dport 1306 -j REDIRECT --to-ports 3306  
# iptables -I INPUT -p tcp --dport 3306 -m mark --mark 883306 -j ACCEPT 
```

```
vim取消搜索高亮—— 
# :noh
```

##### Linux 开发环境安装

```
# 安装上传功能的运行命令：
# yum install -y lrzsz  

# 安装gcc编译环境命令：
# yum install gcc 
```



##### CentOS 配置ip地址

###### 第一步：

```
# 获取IP地址命令： 
# dhclient  

# 查看ip地址： 
# ip addr  

#记下ip地址 
```

###### 第二步：

```
# 查看虚拟机网卡网关
# 记下网卡网关
```

###### 第三步：

```shell
# 编辑ip配置文件
# vi /etc/sysconfig/network-scripts/ifcfg-ens33 
```

##### 第四步：

```shell
# 重启ip服务：
# sudo service network restart 
```



```
Linux命令中并没有这几项，而是存在于vi和vim等编辑器中，详情如下：
# q：退出
# wq：修改后保存退出
# q！：强制退出，不保存修改的内容
```



Linux CentOS安装：

```shell
# 分区：
/boot 200m
swap 4g
/（剩余的空间都分给“/”）

# 配置ip地址：、

# 自动获取一个ip地址：
# dhclient

# 查看ip地址：
# ip addr（192.168.141.128）

# NAT：获取网关地址

# 永久性删除用户账号：
# userdel peter
```



##### ArchLiunx 安装

###### 1、archlinux 安装

###### 2、deepin 桌面环境安装

```shell
# pacman -S deepin  
# pacman -S deepin-extra  
# pacman -S networkmanager  
# systemctl start NetworkManager  
# vim /etc/lightdm/lightdm.conf 

# 查找 greeter-session 
	greeter-session:example-gtx-gnone 
修改为：
	greeter-session:ligthdm-deepin-greeter 

# systemctl enable lightdm  

# 创建一个用户：
# useradd -m -g users -G wheel -s /bin/bash lee 

# 设置密码：
# passwd  visudo 
```



##### Centos 卸载自带Java

```shell
# 卸载
# 1、查看已经安装的jdk：通过  rpm -qa | grep Java 命令来查询出系统自带的jdk
[root@bogon jre]# rpm -qa|grep jdk 
java-1.8.0-openjdk-headless-1.8.0.65-3.b17.el7.x86_64 
java-1.7.0-openjdk-1.7.0.91-2.6.2.3.el7.x86_64 
java-1.7.0-openjdk-headless-1.7.0.91-2.6.2.3.el7.x86_64 
java-1.8.0-openjdk-1.8.0.65-3.b17.el7.x86_64

# 2、卸载命令：通过  rpm -e --nodeps  后面跟系统自带的jdk名  这个命令来删除系统自带的jdk
[root@bogon jre]# yum -y remove java-1.8.0-openjdk-headless-1.8.0.65-3.b17.el7.x86_64

# 3、卸载完成之后Java命令不被识别
[root@bogon lib]# java -version bash: java: command not found...

# 安装
# 去官网下载jdk：http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html 
# 1、解压到安装目录
[root@bogon software]# tar -zxvf jdk-8u101-linux-x64.tar.gz -C /usr/local/java/

# 2、安装完毕之后在/etc/profile文件末尾添加
[root@bogon software]# vim /etc/profile 
export JAVA_HOME=/usr/local/java/jdk1.8.0_101 
export JRE_HOME=${JAVA_HOME}/jre 
export CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib 
export PATH=${JAVA_HOME}/bin:$PATH

# 3、使/etc/profile生效
[root@bogon jdk1.8.0_101]# source /etc/profile

# 4、检测安装是否成功
[root@bogon jdk1.8.0_101]# java -version
java version "1.8.0_101"
Java(TM) SE Runtime Environment (build 1.8.0_101-b13)
Java HotSpot(TM) 64-Bit Server VM (build 25.101-b13, mixed mode)
[root@bogon jdk1.8.0_101]# javac
Usage: javac <options> <source files>
where possible options include:
  -g                         Generate all debugging info
  -g:none                    Generate no debugging info
  -g:{lines,vars,source}     Generate only some debugging info
  -nowarn                    Generate no warnings
  -verbose                   Output messages about what the compiler is doing
  -deprecation               Output source locations where deprecated APIs are used
  -classpath <path>          Specify where to find user class files and annotation processors
  -cp <path>                 Specify where to find user class files and annotation processors
  -sourcepath <path>         Specify where to find input source files
  -bootclasspath <path>      Override location of bootstrap class files
  -extdirs <dirs>            Override location of installed extensions
  -endorseddirs <dirs>       Override location of endorsed standards path
  -proc:{none,only}          Control whether annotation processing and/or compilation is done.
  -processor <class1>[,<class2>,<class3>...] Names of the annotation processors to run; bypasses default discovery process
  -processorpath <path>      Specify where to find annotation processors
  -parameters                Generate metadata for reflection on method parameters
  -d <directory>             Specify where to place generated class files
  -s <directory>             Specify where to place generated source files
  -h <directory>             Specify where to place generated native header files
  -implicit:{none,class}     Specify whether or not to generate class files for implicitly referenced files
  -encoding <encoding>       Specify character encoding used by source files
  -source <release>          Provide source compatibility with specified release
  -target <release>          Generate class files for specific VM version
  -profile <profile>         Check that API used is available in the specified profile
  -version                   Version information
  -help                      Print a synopsis of standard options
  -Akey[=value]              Options to pass to annotation processors
  -X                         Print a synopsis of nonstandard options
  -J<flag>                   Pass <flag> directly to the runtime system
  -Werror                    Terminate compilation if warnings occur
  @<filename>                Read options and filenames from file
```



