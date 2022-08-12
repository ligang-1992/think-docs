##### Mac Iterm2 配置rz、sz命令

```
# 第一步 安装lrzsz
brew install lrzsz

# 第二步 下载iterm2-zmodem
git clone https://github.com/aikuyun/iterm2-zmodem.git
cd iterm2-zmodem

cp iterm2-* /usr/local/bin
cd /usr/local/bin
chmod +x iterm2-*

# 第三步 进入iterm2配置项 profiles->default->editProfiles->Advanced中的Tirgger
Regular expression:  \*\*B0100
Action: Run Silent Coprocess
Parameters: /usr/local/bin/iterm2-send-zmodem.sh

Regular expression:  \*\*B00000000000000
Action: Run Silent Coprocess
Parameters: /usr/local/bin/iterm2-recv-zmodem.sh
```



#### 修复mac终端命令失效

```shell
# 步骤一
PATH=/bin:/usr/bin:/usr/local/bin:${PATH}  

# 步骤二
export PATH
```



#### Homebrew 完全卸载软件 And 依赖包

```
# 前记
# 鉴于 brew uninstall 只会卸载软件包本身而不会卸载其依赖包，所以我们用 homebrew-rmtree 来解决完全卸载
homebrew-rmtree

# 安装
brew tap beeftornado/rmtree

# 使用
brew rmtree pyenv-virtualenv
brew cleanup
```



#### Mac查看端口占用

```shell
# port替换成端口号，比如6379,可以查看该端口被什么程序占用，并显示PID，方便KILL
➜  ~ lsof -i tcp:port  
```



#### [解决GitHub的raw.githubusercontent.com无法连接问题](https://www.cnblogs.com/sinferwu/p/12726833.html)

###### 1、查询对应的IP地址

```
# IP查询地址
# https://www.ipaddress.com/
# https://site.ip138.com/raw.Githubusercontent.com/

例如：raw.githubusercontent.com
```

###### 2、修改hosts Ubuntu，CentOS及macOS直接在终端输入

```
sudo vi /etc/hosts
```

###### 3、添加以下内容保存即可 （IP地址查询后相应修改，可以ping不同IP的延时 选择最佳IP地址）

```
# GitHub Start
52.74.223.119 github.com
192.30.253.119 gist.github.com
54.169.195.247 api.github.com
185.199.111.153 assets-cdn.github.com
151.101.76.133 raw.githubusercontent.com
151.101.108.133 user-images.githubusercontent.com
151.101.76.133 gist.githubusercontent.com
151.101.76.133 cloud.githubusercontent.com
151.101.76.133 camo.githubusercontent.com
151.101.76.133 avatars0.githubusercontent.com
151.101.76.133 avatars1.githubusercontent.com
151.101.76.133 avatars2.githubusercontent.com
151.101.76.133 avatars3.githubusercontent.com
151.101.76.133 avatars4.githubusercontent.com
151.101.76.133 avatars5.githubusercontent.com
151.101.76.133 avatars6.githubusercontent.com
151.101.76.133 avatars7.githubusercontent.com
151.101.76.133 avatars8.githubusercontent.com
# GitHub End
```



### 重启网卡

```shell
# 停止
～% sudo ifconfig en0 down
# 启动
~% sudo ifconfig en0 up
```



### Docsify 教程

```shell
# 1、初始化文档目录
~ % docsify init ./think-docs
# think-docs 为文件夹名称

# 2、启动项目
~ % docsify serve ./think-docs
```

```shell
# npm安装模块
~ % npm install xxx							# 利用 npm 安装xxx模块到当前命令行所在目录；
~ % npm install -g xxx					# 利用npm安装全局模块xxx；

# 本地安装时将模块写入package.json中：
~ % npm install xxx							# 安装但不写入package.json；
~ % npm install xxx --save			# 安装并写入package.json的"dependencies"中；
~ % npm install xxx --save-dev	# 安装并写入package.json的"devDependencies"中。

# npm 删除模块
~ % npm uninstall xxx						# 删除xxx模块；
~ % npm uninstall -g xxx				# 删除全局模块xxx；
```

更新时间：2020-04-12



### Mac 软件包损坏解决办法

```shell
~ % sudo xattr -r -d com.apple.quarantine
# 注意quarantine后面要加一个空格，然后将应用程序里面的app拖拽到这段命令的后面，然后回车输入密码即可，务必不要忘记了quarantine后面那个空格。
```

```shell
~ % xcode-select --install
```

更新时间：2020-04-12

##### 查看IP地址

```shell
# 方法1
~ % ifconfig

# 方法2
~ % ifconfig | grep "inet"
```

更新时间：2020-04-12



#### 编辑hosts文件

```
～% vi /etc/hosts
```

```
配置python环境：
～% vi ~/.bash_profile
alias python="/usr/local/bin/python3"
```

更新时间：2019-12-01

#### Home Brew 安装

##### 1、解决brew 更新慢的问题

```
第一种：
～% cd "$(brew --repo)"
～% git remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/brew.git
～% git checkout master
～% git pull origin master

～% cd "$(brew --repo)/Library/Taps/homebrew/homebrew-core"
～% git remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-core.git
～% git checkout master
～% git pull origin master

～% brew update

第二种：
1、替换brew.git
～% cd "$(brew --repo)"
～% git remote set-url origin https://mirrors.ustc.edu.cn/brew.git

2、替换homebrew-core.git
～% cd "$(brew --repo)/Library/Taps/homebrew/homebrew-core"
～% git remote set-url origin https://mirrors.ustc.edu.cn/homebrew-core.git

第三种：
# 替换brew.git:
$ cd "$(brew --repo)"
# 中国科大:
$ git remote set-url origin https://mirrors.ustc.edu.cn/brew.git
# 清华大学:
$ git remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/brew.git

# 替换homebrew-core.git:
$ cd "$(brew --repo)/Library/Taps/homebrew/homebrew-core"
# 中国科大:
$ git remote set-url origin https://mirrors.ustc.edu.cn/homebrew-core.git
# 清华大学:
$ git remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-core.git

# 替换homebrew-bottles:
# 中国科大:
$ echo 'export HOMEBREW_BOTTLE_DOMAIN=https://mirrors.ustc.edu.cn/homebrew-bottles' >> ~/.bash_profile
$ source ~/.bash_profile
# 清华大学:
$ echo 'export HOMEBREW_BOTTLE_DOMAIN=https://mirrors.tuna.tsinghua.edu.cn/homebrew-bottles' >> ~/.bash_profile
$ source ~/.bash_profile

# 应用生效:
$ brew update

切换回官方源
# 重置brew.git:
$ cd "$(brew --repo)"
$ git remote set-url origin https://github.com/Homebrew/brew.git

# 重置homebrew-core.git:
$ cd "$(brew --repo)/Library/Taps/homebrew/homebrew-core"
$ git remote set-url origin https://github.com/Homebrew/homebrew-core.git

```

##### 2、HomeBrew 更新时打印日志

```
～% brew update --verbose
```



#### 全屏化程序坞不会隐藏

```
第一种：
～% killall Dock

第二种：
～% defaults write com.apple.dock autohide-delay -int 0
～% defaults write com.apple.dock autohide-time-modifier -float 1.0
～% killall Dock
```

更新时间：2019-11-14

#### Mac 使用技巧

##### 1、mac 创建文件

```
～% touch file_name.xxx
```

更新时间：2019-11-06

##### 1、设置mac安装软件限制  

```
## 需要输入电脑密码
sudo spctl --master-disable
```

```
java环境变量配置：vim ~/.bash_profile 
```

```
Mac 查看文件权限：ls -l 文件名
```

```
mac 切换管理员用户：
```

```
修改文件读写权限：sudo chmod -R 775 文件名
```

##### 2、gradle 环境变量配置：

```
1、编辑配置文件
vi ~/.bash_profile

2、添加环境变量
GRADLE_HOME=/Users/ligang/devtools/gradle/gradle-5.5
export GRADLE_HOME
export PATH=$PATH:$GRADLE_HOME/bin

3、是配置文件生效
source ～/.bash_profile
```

##### 3、brew 安装

```
安装brew：
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

brew 常用命令：
    brew install 软件名				安装软件
    brew search 软件名					搜索软件
    brew uninstall 软件名			卸载软件
    brew list									列出已安装的软件
    brew update								更新brew
    brew home									用浏览器打开brew的官方网站
    brew info									显示软件信息
    brew deps									显示包依赖
    brew cleanup             # 清理所有包的旧版本
		brew cleanup $FORMULA    # 清理指定包的旧版本
		brew cleanup -n          # 查看可清理的旧版本包，不执行实际操作
		brew upgrade 软件名			 	更新某软件
```

更新时间：2019-07-12