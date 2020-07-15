#### Mac查看端口占用

```shell
# port替换成端口号，比如6379,可以查看该端口被什么程序占用，并显示PID，方便KILL
➜  ~ lsof -i tcp:port  
```



#### [解决GitHub的raw.githubusercontent.com无法连接问题](https://www.cnblogs.com/sinferwu/p/12726833.html)

###### 1、修改hosts Ubuntu，CentOS及macOS直接在终端输入

```
sudo vi /etc/hosts
```

###### 2、添加以下内容保存即可 （IP地址查询后相应修改，可以ping不同IP的延时 选择最佳IP地址）

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



### yarn常用命令

```shell
# 安装yarn
~ % npm install -g yarn

# 安装成功后，查看版本号：
~ % yarn --version

# 创建文件夹 yarn
~ % md yarn

# 进入yarn文件夹
~ % cd yarn

# 初始化项目
# 同npm init，执行输入信息后，会生成package.json文件
~ % yarn init

# yarn的配置项：
~ % yarn config list														# // 显示所有配置项
~ % yarn config get <key>												# //显示某配置项
~ % yarn config delete <key>										# //删除某配置项
~ % yarn config set <key> <value> [-g|--global]	# 设置配置项

# 安装包：
~ % yarn install									# 安装package.json里所有包，并将包及它的所有依赖项保存进yarn.lock
~ % yarn install --flat						# 安装一个包的单一版本
~ % yarn install --force					# 强制重新下载所有包
~ % yarn install --production 		# 只安装dependencies里的包
~ % yarn install --no-lockfile 		# 不读取或生成yarn.lock
~ % yarn install --pure-lockfile	# 不生成yarn.lock

# 添加包（会更新package.json和yarn.lock）：
~ % yarn add [package] // 在当前的项目中添加一个依赖包，会自动更新到package.json和yarn.lock文件中
~ % yarn add [package]@[version] // 安装指定版本，这里指的是主要版本，如果需要精确到小版本，使用-E参数
~ % yarn add [package]@[tag] // 安装某个tag（比如beta,next或者latest）
//不指定依赖类型默认安装到dependencies里，你也可以指定依赖类型：

~ % yarn add --dev/-D // 加到 devDependencies
~ % yarn add --peer/-P // 加到 peerDependencies
~ % yarn add --optional/-O // 加到 optionalDependencies

# 默认安装包的主要版本里的最新版本，下面两个命令可以指定版本：
# 安装包的精确版本。例如yarn add foo@1.2.3会接受1.9.1版，但是yarn add foo@1.2.3 --exact只会接受1.2.3版
~ % yarn add --exact/-E
# 安装包的次要版本里的最新版。例如yarn add foo@1.2.3 --tilde会接受1.2.9，但不接受1.3.0
~ % yarn add --tilde/-T

# 发布包
~ % yarn publish

# 移除一个包
~ % yarn remove <packageName>	# 移除一个包，会自动更新package.json和yarn.lock

# 更新一个依赖
~ % yarn upgrade 							# 用于更新包到基于规范范围的最新版本

# 运行脚本
~ % yarn run									# 用来执行在 package.json 中 scripts 属性下定义的脚本

# 显示某个包的信息
~ % yarn info <packageName> 	# 可以用来查看某个模块的最新版本信息

# 缓存
~ % yarn cache
~ % yarn cache list						# 列出已缓存的每个包
~ % yarn cache dir						# 返回 全局缓存位置
~ % yarn cache clean					# 清除缓存
————————————————
版权声明：本文为CSDN博主「yw00yw」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/yw00yw/java/article/details/81354533
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

### 安装 vue

```shell
关于旧版本

Vue CLI 的包名称由 vue-cli 改成了 @vue/cli。 如果你已经全局安装了旧版本的 vue-cli (1.x 或 2.x)，你需要先通过 
～% npm uninstall vue-cli -g 
或
～% yarn global remove vue-cli 卸载它。

Node 版本要求
Vue CLI 需要 Node.js 8.9 或更高版本 (推荐 8.11.0+)。你可以使用 nvm 或 nvm-windows 在同一台电脑中管理多个 Node 版本。

可以使用下列任一命令安装这个新的包：
～% npm install -g @vue/cli
# OR
～% yarn global add @vue/cli

安装之后，你就可以在命令行中访问 vue 命令。你可以通过简单运行 vue，看看是否展示出了一份所有可用命令的帮助信息，来验证它是否安装成功。
你还可以用这个命令来检查其版本是否正确：
～% vue --version
```

更新时间：2020-04-12

#### 安装node

```
～% brew install -g node
～% brew link node
```

更新时间：2019-12-11

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

##### 3、Mac 上卸载node和npm

```
卸载node
依次在终端执行下面的脚本

sudo npm uninstall npm -g
sudo rm -rf /usr/local/lib/node /usr/local/lib/node_modules /var/db/receipts/org.nodejs.*
sudo rm -rf /usr/local/include/node /Users/$USER/.npm
sudo rm /usr/local/bin/node
sudo rm /usr/local/share/man/man1/node.1
sudo rm /usr/local/lib/dtrace/node.d
最后验证一下

node //command not found
npm //command not found

# npm 安装组件网速问题
# 安装时指定镜像服务器
～% npm install -gd express --registry=http://registry.npm.taobao.org
# 永久指定服务器
～% npm config set registry http://registry.npm.taobao.org
```

##### 4、Mac 安装 cnpm

```
sudo npm install -g cnpm --registry=https://registry.npm.taobao.org --verbose
cnpm -v
```

更新时间：2019-11-28

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
```

更新时间：2019-07-12