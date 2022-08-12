#### go热部署

##### install air

```shell
go install github.com/cosmtrek/air@latest
```

##### air启动项目

```shell
# 进入项目目录
cd /path/to/your_project
# air 环境初始化
air init
# air 启动项目
air
```



#### gRPC

```shell
# 1、安装gRPC
$ go install google.golang.org/protobuf/cmd/protoc-gen-go@v1.26
$ go install google.golang.org/grpc/cmd/protoc-gen-go-grpc@v1.1

# 2、配置插件编译路径
$ export PATH="$PATH:$(go env GOPATH)/bin"

# 3、编写 xxx.proto 文件

# 4、生成文件命令
# option go_package = "./;pb"; 
# 注意：`./`：文件路径 `pb`：包名
# paths参数
# 使用 source_relative 则不会使用option go_package中指定的路径
# 使用 import 则是使用option go_package 中指定的路径
$ protoc --go_out=. --go_opt=paths=source_relative \
    --go-grpc_out=. --go-grpc_opt=paths=source_relative \
    helloworld/helloworld.proto
```



##### 卸载Golang

```shell
# 1、查看路径在哪里：
~ % which go

# 2、root 权限下删除
~ % rm -rf /usr/local/go

# 3、删除
~ % rm -rf /etc/paths.d/go

# 4、将环境变量，有关 go 的删了即可
~ % vim ~/.bash_profile
```



#### 安装Golang

```
官网下载安装包，默认安装就好
```



#### 配置开发环境

```shell
# 设置GOPATH路径（GOPATH路径是我们的工作区）
~ % go env -w GOPATH=我们自己的工作区路径

# 配置代理
# 步骤一：打开GoMOD
~ % go env -w GO111MODULE=on
# 步骤二：配置代理
# 方式一
~ % go env -w GOPROXY=https://goproxy.io,direct

# 方式二
~ % go env -w GOPROXY=https://goproxy.cn/,direct
```



#### 在VSCode中安装Go插件

```
在插件市场搜索go，并安装
```

#### VSCode智能提示修复

```shell
~ % go get -u -v github.com/mdempsky/gocode
```

#### 在我们的GOPATH/src目录下，创建一个hello/hello.go文件，并且用VSCode打开

```
（​GOPATH是指我们刚刚配置的环境变量。比如上面配置的环境变量位置为/Users/naonao/go，即GOPATH就是指/Users/naonao/go这个路径。那么​GOPATH/src就是指/Users/naonao/go/src目录）

在安装了Go插件后的VsCode，现在打开go文件后，会自动安装我们自己的必要的环境依赖
```

#### Go Modules的使用

```shell
进入我们的hello文件夹，并且执行go mod init即可
~ % cd $GOPATH/src/hello
~ % go mod init

# go mod tidy，通俗来说就是将当前的库源码文件所依赖的包，全部安装并记录下来，多的包就删掉，少了的就自动补上
```

#### VSCode开发环境配置

```json
// 1、Lunch.json配置
{
    // 使用 IntelliSense 了解相关属性。 
    // 悬停以查看现有属性的描述。
    // 欲了解更多信息，请访问: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [
        
        {
            "name": "Launch file",
            "type": "go",
            "request": "launch",
            "mode": "debug",
            "program": "${file}"
        },
        {
            "name": "Launch",
            "type": "go",
            "request": "launch",
            "mode": "auto",
            "program": "${fileDirname}",
            "env": {
                "GOPATH": "/Users/ligang/go",
                "GOROOT": "/usr/local/go"
            },
            "args": []
        }
    ]
}

// 2、Setting.json配置
{
    "go.useLanguageServer": true,
    "editor.minimap.renderCharacters": false,
    "editor.minimap.enabled": false,
    "terminal.external.osxExec": "iTerm.app",
    "go.docsTool": "gogetdoc",
    "go.testFlags": [
        "-v",
        "-count=1"
    ],
    "go.buildTags": "",
    "go.buildFlags": [],
    "go.lintFlags": [],
    "go.vetFlags": [],
    "go.coverOnSave": false,
    "go.useCodeSnippetsOnFunctionSuggest": false,
    "go.gocodeAutoBuild": false,
    "go.goroot": "/usr/local/go",
    "go.gopath": "/Users/ligang/go",
    "go.autocompleteUnimportedPackages": true,
    "go.formatOnSave": true,
    "window.zoomLevel": 0,
    "debug.console.fontSize": 16,
    "debug.console.lineHeight": 30,
}

```

#### 编译成可执行文件

```shell
# 进入项目目录下
~ % go build -o application_name
```

#### 安装gin框架

```shell
~ % go get -u github.com/gin-gonic/gin
```

### Go程序开发注意事项

1. Go源文件以“go”为扩展名
2. Go应用程序的执行入口是main()函数
3. Go语言严格区分大小写
4. Go方法由一条条语句构成，每个语句后不需要分号（Go语言会在每行后面自动添加分号），这也体现出Golang的简洁性
5. Go编译器是一行行进行编译的，因此我们一行就写一条语句，不能吧多条语句写在同一行，否则会报错
6. Go语言`定义的变量`或者`improt的包`如果没有使用到，代码不能编译通过
7. 大括号都是成对出现的，缺一不可