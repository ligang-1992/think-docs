### Docsify 教程

```
1、初始化文档目录
～% docsify init ./think-docs
# think-docs 为文件夹名称

2、启动项目
～% docsify serve ./think-docs
```



```
npm安装模块
【npm install xxx】利用 npm 安装xxx模块到当前命令行所在目录；
【npm install -g xxx】利用npm安装全局模块xxx；
本地安装时将模块写入package.json中：

【npm install xxx】安装但不写入package.json；
【npm install xxx --save】 安装并写入package.json的"dependencies"中；
【npm install xxx --save-dev】安装并写入package.json的"devDependencies"中。
npm 删除模块
【npm uninstall xxx】删除xxx模块；
【npm uninstall -g xxx】删除全局模块xxx；
```



### Mac 软件包损坏解决办法

```
sudo xattr -r -d com.apple.quarantine
注意quarantine后面要加一个空格，然后将应用程序里面的app拖拽到这段命令的后面，然后回车输入密码即可，务必不要忘记了quarantine后面那个空格。
```

```
xcode-select --install
```



##### 查看IP地址

```
第一种方法：
～% ifconfig

第二种方法：
～% ifconfig | grep "inet"
```



### 安装 vue

```
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



### 日期：2019-12-11

#### 安装node

```
～% brew install -g node
～% brew link node
```



### 日期：2019-12-01

#### 编辑hosts文件

```
～% vi /etc/hosts
```

日期：2019-11-29

```
配置python环境：
～% vi ~/.bash_profile
alias python="/usr/local/bin/python3"
```



### 日期：2019-11-28

#### 1、解决brew 更新慢的问题

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

#### 2、HomeBrew 更新时打印日志

```
～% brew update --verbose
```

#### 3、Mac 上卸载node和npm

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
```

#### 4、Mac 安装 cnpm

```
sudo npm install -g cnpm --registry=https://registry.npm.taobao.org --verbose
cnpm -v
```



### 日期：2019-11-14

#### 全屏化程序坞不会隐藏

```
第一种：
～% killall Dock

第二种：
～% defaults write com.apple.dock autohide-delay -int 0
～% defaults write com.apple.dock autohide-time-modifier -float 1.0
～% killall Dock
```



### 日期：2019-11-06

#### 1、mac 创建文件

```
～% touch file_name.xxx
```



### 日期：2019-07-12

#### 1、设置mac安装软件限制  

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

#### 2、gradle 环境变量配 置：

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

#### 3、brew 安装

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
