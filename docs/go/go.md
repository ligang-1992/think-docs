#### 1、安装go

```
官网下载安装包，默认安装就好
```

#### 2、配置环境变量

```
1、设置GOPATH路径（GOPATH路径是我们的工作区）
～ % go env -w GOPATH=我们自己的工作区路径

2、打开GoMOD，再配置代理
～ % go env -w GO111MODULE=on
～ % go env -w GOPROXY=https://goproxy.cn,direct
```

#### 3、在VSCode中安装Go插件

```
在插件市场搜索go，并安装
```

#### 4、在我们的GOPATH/src目录下，创建一个hello/hello.go文件，并且用VSCode打开

```
（​GOPATH是指我们刚刚配置的环境变量。比如上面配置的环境变量位置为/Users/naonao/go，即GOPATH就是指/Users/naonao/go这个路径。那么​GOPATH/src就是指/Users/naonao/go/src目录）

在安装了Go插件后的VsCode，现在打开go文件后，会自动安装我们自己的必要的环境依赖
```

#### 5、Go Modules的使用

```
进入我们的hello文件夹，并且执行go mod init即可
～ % cd $GOPATH/src/hello
～ % go mod init

go mod tidy，通俗来说就是将当前的库源码文件所依赖的包，全部安装并记录下来，多的包就删掉，少了的就自动补上
```

#### 6、VSCode的Lunch.json配置以及Setting.json配置

```
1、Lunch.json配置
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

2、Setting.json配置
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

#### 7、编译成可执行文件

```
# 进入项目目录下
～% go build -o application_name
```

