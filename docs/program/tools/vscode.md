#### 常用快捷键

```
全局

Command + Shift + P / F1 显示命令面板
Command + P 快速打开
Command + Shift + N 打开新窗口
Command + W 关闭窗口

基本

Command + X 剪切（未选中文本的情况下，剪切光标所在行）
Command + C 复制（未选中文本的情况下，复制光标所在行）
Option + Up 向上移动行
Option + Down 向下移动行
Option + Shift + Up 向上复制行
Option + Shift + Down 向下复制行
Command + Shift + K 删除行
Command + Enter 下一行插入
Command + Shift + Enter 上一行插入
Command + Shift + 跳转到匹配的括号
Command + [ 减少缩进
Command + ] 增加缩进
Home 跳转至行首
End 跳转到行尾
Command + Up 跳转至文件开头
Command + Down 跳转至文件结尾
Ctrl + PgUp 按行向上滚动
Ctrl + PgDown 按行向下滚动
Command + PgUp 按屏向上滚动
Command + PgDown 按屏向下滚动
Command + Shift + [ 折叠代码块
Command + Shift + ] 展开代码块
Command + K Command + [ 折叠全部子代码块
Command + K Command + ] 展开全部子代码块
Command + K Command + 0 折叠全部代码块
Command + K Command + J 展开全部代码块
Command + K Command + C 添加行注释
Command + K Command + U 移除行注释
Command + / 添加、移除行注释
Option + Shift + A 添加、移除块注释
Option + Z 自动换行、取消自动换行

多光标与选择

Option + 点击 插入多个光标
Command + Option + Up 向上插入光标
Command + Option + Down 向下插入光标
Command + U 撤销上一个光标操作
Option + Shift + I 在所选行的行尾插入光标
Command + I 选中当前行
Command + Shift + L 选中所有与当前选中内容相同部分
Command + F2 选中所有与当前选中单词相同的单词
Command + Ctrl + Shift + Left 折叠选中
Command + Ctrl + Shift + Right 展开选中
Alt + Shift + 拖动鼠标 选中代码块
Command + Shift + Option + Up 列选择 向上
Command + Shift + Option + Down 列选择 向下
Command + Shift + Option + Left 列选择 向左
Command + Shift + Option + Right 列选择 向右
Command + Shift + Option + PgUp 列选择 向上翻页
Command + Shift + Option + PgDown 列选择 向下翻页

查找替换

Command + F 查找
Command + Option + F 替换
Command + G 查找下一个
Command + Shift + G 查找上一个
Option + Enter 选中所有匹配项
Command + D 向下选中相同内容
Command + K Command + D 移除前一个向下选中相同内容

进阶

Ctrl + Space 打开建议
Command + Shift + Space 参数提示
Tab Emmet插件缩写补全
Option + Shift + F 格式化
Command + K Command + F 格式化选中内容
F12 跳转到声明位置
Option + F12 查看具体声明内容
Command + K F12 分屏查看具体声明内容
Command + . 快速修复
Shift + F12 显示引用
F2 重命名符号
Command + Shift + . 替换为上一个值
Command + Shift + , 替换为下一个值
Command + K Command + X 删除行尾多余空格
Command + K M 更改文件语言

导航

Command + T 显示所有符号
Ctrl + G 跳转至某行
Command + P 跳转到某个文件
Command + Shift + O 跳转到某个符号
Command + Shift + M 打开问题面板
F8 下一个错误或警告位置
Shift + F8 上一个错误或警告位置
Ctrl + Shift + Tab 编辑器历史记录
Ctrl + - 后退
Ctrl + Shift + - 前进
Ctrl + Shift + M Tab 切换焦点

编辑器管理

Command + W 关闭编辑器
Command + K F 关闭文件夹
Command + 编辑器分屏
Command + 1 切换到第一分组
Command + 2 切换到第二分组
Command + 3 切换到第三分组
Command + K Command + Left 切换到上一分组
Command + K Command + Right 切换到下一分组
Command + K Command + Shift + Left 左移编辑器
Command + K Command + Shift + Right 右移编辑器
Command + K Left 激活左侧编辑组
Command + K Right 激活右侧编辑组

文件管理

Command + N 新建文件
Command + O 打开文件
Command + S 保存文件
Command + Shift + S 另存为
Command + Option + S 全部保存
Command + W 关闭
Command + K Command + W 全部关闭
Command + Shift + T 重新打开被关闭的编辑器
Command + K Enter 保持打开
Ctrl + Tab 打开下一个
Ctrl + Shift + Tab 打开上一个
Command + K P 复制当前文件路径
Command + K R 在资源管理器中查看当前文件
Command + K O 新窗口打开当前文件

显示

Command + Ctrl + F 全屏、退出全屏
Command + Option + 1 切换编辑器分屏方式（横、竖）
Command + + 放大
Command + - 缩小
Command + B 显示、隐藏侧边栏
Command + Shift + E 显示资源管理器 或 切换焦点
Command + Shift + F 显示搜索框
Ctrl + Shift + G 显示Git面板
Command + Shift + D 显示调试面板
Command + Shift + X 显示插件面板
Command + Shift + H 全局搜索替换
Command + Shift + J 显示、隐藏高级搜索
Command + Shift + C 打开新终端
Command + Shift + U 显示输出面板
Command + Shift + V Markdown预览窗口
Command + K V 分屏显示 Markdown预览窗口

调试

F9 设置 或 取消断点
F5 开始 或 继续
F11 进入
Shift + F11 跳出
F10 跳过
Command + K Command + I 显示悬停信息

集成终端

Ctrl + 显示终端 Ctrl + Shift + 新建终端
Command + Up 向上滚动
Command + Down 向下滚动
PgUp 向上翻页
PgDown 向下翻页
Command + Home 滚动到顶部
Command + End 滚动到底部
```

#### 个人设置

```
{
	"[css]": {
		"editor.defaultFormatter": "esbenp.prettier-vscode",
		"editor.tabSize": 2
	},
	"[dart]": {
		"editor.formatOnSave": true,
		"editor.formatOnType": true,
		"editor.rulers": [80],
		"editor.selectionHighlight": false,
		"editor.suggest.snippetsPreventQuickSuggestions": false,
		"editor.suggestSelection": "first",
		"editor.tabCompletion": "onlySnippets",
		"editor.wordBasedSuggestions": false
	},
	"[html]": {
		"editor.defaultFormatter": "vscode.html-language-features",
		"editor.tabSize": 2
	},
	"[java]": {
		"editor.defaultFormatter": "xaver.clang-format"
	},
	// "[java]": {
	// 	// "editor.defaultFormatter": "esbenp.prettier-vscode"
	// },
	"[javascript]": {
		"editor.defaultFormatter": "esbenp.prettier-vscode",
		"editor.tabSize": 2
	},
	"[javascriptreact]": {
		"editor.defaultFormatter": "esbenp.prettier-vscode",
		"editor.tabSize": 2,
		"editor.wordWrap": "on"
	},
	"[json]": {
		"editor.defaultFormatter": "esbenp.prettier-vscode",
		"editor.tabSize": 2
	},
	"[jsonc]": {
		"editor.defaultFormatter": "esbenp.prettier-vscode",
		"editor.tabSize": 2
	},
	"[proto3]": {
		"editor.defaultFormatter": "xaver.clang-format"
	},
	"[python]": {
		"editor.defaultFormatter": "ms-python.python",
		"editor.formatOnPaste": false
	},
	"[scss]": {
		"editor.defaultFormatter": "esbenp.prettier-vscode",
		"editor.tabSize": 2
	},
	"[sql]": {
		"editor.defaultFormatter": "mtxr.sqltools"
		// "editor.defaultFormatter": "adpyke.vscode-sql-formatter"
	},
	"[typescript]": {
		// "editor.defaultFormatter": "esbenp.prettier-vscode",
		"editor.defaultFormatter": "vscode.typescript-language-features",
		"editor.tabSize": 2
	},
	"[vue]": {
		// "editor.defaultFormatter": "johnsoncodehk.volar",
		"editor.defaultFormatter": "esbenp.prettier-vscode",
		"editor.tabSize": 2
	},
	"bracket-pair-colorizer-2.depreciation-notice": false,
	// proto 格式化配置
	"clang-format.style": "google",
	"cSpell.enableFiletypes": ["vue"],
	"cSpell.userWords": [
		"actix",
		"adipisicing",
		"Alibaba",
		"alicdn",
		"allowfullscreen",
		"amet",
		"amqp",
		"Antd",
		"appbar",
		"appenders",
		"arity",
		"arrs",
		"asim",
		"auctor",
		"AUTOGENERATED",
		"Avenir",
		"bcrypt",
		"bodyparser",
		"browserslist",
		"bson",
		"camelcase",
		"chacha",
		"charcode",
		"chenfengyuan",
		"classprops",
		"clickaway",
		"cloudbase",
		"commitlint",
		"compat",
		"Configurer",
		"consectet",
		"consectetur",
		"consetetur",
		"coverpage",
		"crossorigin",
		"cupertino",
		"Datepicker",
		"datetimepicker",
		"dbname",
		"deadpool",
		"Debugf",
		"dgrijalva",
		"distpicker",
		"docsify",
		"dolore",
		"doloremque",
		"dotenv",
		"Downie",
		"dubbo",
		"easypiechart",
		"echarts",
		"eget",
		"eirmod",
		"eius",
		"elit",
		"elitr",
		"esnext",
		"esversion",
		"euismod",
		"excanvas",
		"extendee",
		"felis",
		"Fenix",
		"flot",
		"fontawesome",
		"Freemarker",
		"gerudo",
		"getrandom",
		"glassmorphism",
		"gocolly",
		"goctl",
		"godotenv",
		"gofiber",
		"gomock",
		"gonic",
		"gorm",
		"grayscale",
		"Helvetica",
		"httpx",
		"hylia",
		"Hyrule",
		"iconfont",
		"icyfenix",
		"Idxs",
		"Infof",
		"intbuf",
		"Intelli",
		"invidunt",
		"javaagent",
		"jinzhu",
		"joho",
		"jqdata",
		"Jwts",
		"kratos",
		"krypt",
		"Krypto",
		"kubernetes",
		"labore",
		"ldigits",
		"leetcode",
		"libc",
		"ligang",
		"llimllib",
		"logx",
		"Luffy",
		"lxml",
		"microservices",
		"middlewares",
		"mixins",
		"mockdata",
		"mockdb",
		"mockjs",
		"mollis",
		"multiline",
		"nacos",
		"natoque",
		"navbars",
		"nofollow",
		"nonumy",
		"noopener",
		"noreferrer",
		"nouislider",
		"nums",
		"Nuxt",
		"nuxtjs",
		"ocidd",
		"offsetmust",
		"omnis",
		"oneof",
		"opentype",
		"ornare",
		"Parens",
		"penatibus",
		"pinia",
		"popperjs",
		"porta",
		"postgres",
		"postgresql",
		"proto",
		"protobuf",
		"protoc",
		"protoimpl",
		"pymongo",
		"qcloud",
		"qrcode",
		"regexpu",
		"reqwest",
		"rgba",
		"sadipscing",
		"Schyler",
		"scripthost",
		"scrollbar",
		"semver",
		"Servlet",
		"SFCs",
		"signin",
		"sigs",
		"simplefactory",
		"skywalking",
		"Slidefu",
		"sociis",
		"sparkline",
		"sqlc",
		"starman",
		"steelblue",
		"streadway",
		"stretchr",
		"strs",
		"structs",
		"Submenu",
		"summernote",
		"Swal",
		"tailwindcss",
		"tempor",
		"todos",
		"togglebutton",
		"Treeview",
		"truetype",
		"TTFB",
		"udigits",
		"unknow",
		"urna",
		"Verticle",
		"vertx",
		"Vestibulum",
		"vhost",
		"vite",
		"vitejs",
		"voluptatum",
		"vueuse",
		"Vuex",
		"Warnf",
		"wasi",
		"webfonts",
		"webstorm",
		"wireframe",
		"xorm",
		"zrpc"
	],
	// enable native bracket matching
	"editor.bracketPairColorization.enabled": true,
	"editor.codeActionsOnSave": {
		"source.fixAll": true
	},
	"editor.dragAndDrop": false,
	"editor.fontFamily": "Monaco, 'Operator Mono', 'dank mono', 'Fira code', Menlo, 'Courier New', monospace",
	"editor.fontLigatures": true,
	"editor.fontSize": 14,
	"editor.formatOnPaste": true,
	"editor.formatOnSave": true,
	"editor.formatOnType": true,
	"editor.guides.bracketPairs": "active",
	"editor.inlineSuggest.enabled": true,
	"editor.linkedEditing": true,
	"editor.suggestSelection": "first",
	"editor.tabSize": 4,
	"editor.unicodeHighlight.invisibleCharacters": false,
	"editor.wordWrap": "wordWrapColumn",
	"editor.wordWrapColumn": 120,
	"emmet.includeLanguages": {
		"javascript": "javascriptreact"
	},
	"files.autoSave": "afterDelay",
	"files.exclude": {
		"**/.classpath": true,
		"**/.factorypath": true,
		"**/.idea": true,
		"**/.project": true,
		"**/.settings": true,
		"**/*.iml": true,
		"**/*.pyc": true
	},
	"files.watcherExclude": {
		"**/.ammonite": true,
		"**/.bloop": true,
		"**/.metals": true
	},
	"git.autofetch": true,
	"github.copilot.enable": {
		"*": true,
		"yaml": false,
		"plaintext": false,
		"markdown": false,
		"java": false,
		"dart": false
	},
	"go.autocompleteUnimportedPackages": true,
	"go.docsTool": "gogetdoc",
	"go.formatTool": "goformat",
	"go.testFlags": ["-v", "-count=1"],
	"go.toolsManagement.autoUpdate": true,
	"go.useLanguageServer": true,
	"java.configuration.maven.globalSettings": "/Users/luffy/.m2/settings.xml",
	"java.configuration.maven.userSettings": "/Users/luffy/.m2/settings.xml",
	"java.import.gradle.home": "/usr/local/bin/gradle",
	"java.jdt.ls.java.home": "/usr/local/opt/openjdk@11",
	"java.jdt.ls.vmargs": "-XX:+UseParallelGC -XX:GCTimeRatio=4 -XX:AdaptiveSizePolicyWeight=90 -Dsun.zip.disableMemoryMapping=true -Xmx1G -Xms100m -javaagent:\"/Users/luffy/.vscode/extensions/gabrielbb.vscode-lombok-1.0.1/server/lombok.jar\"",
	"leetcode.endpoint": "leetcode-cn",
	"leetcode.workspaceFolder": "/Users/luffy/.leetcode",
	"liveServer.settings.donotShowInfoMsg": true,
	"pdf-preview.default.scale": "page-fit",
	"prettier.arrowParens": "avoid",
	"prettier.bracketSpacing": true,
	"prettier.enableDebugLogs": true,
	"prettier.jsxSingleQuote": false,
	"prettier.printWidth": 120,
	"prettier.semi": false,
	"prettier.singleQuote": true,
	"prettier.trailingComma": "es5",
	"prettier.useTabs": true,
	"prettier.vueIndentScriptAndStyle": true,
	"prettier.withNodeModules": true,
	"projectManager.git.baseFolders": ["/Users/luffy/github", "/Users/luffy/go"],
	"projectManager.sortList": "Path",
	"python.analysis.extraPaths": [
		"./src", // 自定义模块的相对路径，可多个，可绝对路径
		"./pymongo"
	],
	"python.formatting.provider": "black",
	"python.testing.pytestEnabled": true,
	"redhat.telemetry.enabled": true,
	"screencastMode.onlyKeyboardShortcuts": true,
	"sync.gist": "c2fbef30ad6f394faa533fbfda6970c9",
	"tabnine.experimentalAutoImports": true,
	"terminal.integrated.fontSize": 14,
	"terminal.integrated.persistentSessionReviveProcess": "never",
	"vim.easymotion": true,
	"vim.handleKeys": {
		"<C-a>": false,
		"<C-f>": false
	},
	"vim.hlsearch": true,
	"vim.incsearch": true,
	"vim.insertModeKeyBindings": [
		{
			"after": ["<Esc>"],
			"before": ["j", "j"]
		}
	],
	"vim.leader": "<space>",
	"vim.normalModeKeyBindingsNonRecursive": [
		{
			"after": ["d", "d"],
			"before": ["<leader>", "d"]
		},
		{
			"before": ["<C-n>"],
			"commands": [":nohl"]
		}
	],
	"vim.useCtrlKeys": true,
	"vim.useSystemClipboard": true,
	"vsintellicode.modify.editor.suggestSelection": "automaticallyOverrodeDefaultValue",
	"workbench.iconTheme": "material-icon-theme",
	"dart.previewFlutterUiGuides": true,
	"dart.previewFlutterUiGuidesCustomTracking": true,
	"dart.previewHotReloadOnSaveWatcher": true
}

```



```json
{
  "go.formatTool": "goimports", // or "gofmt", or "goreturns", 这三种都是格式化工具
  "go.useLanguageServer": true,
  "editor.minimap.renderCharacters": false,
  "editor.minimap.enabled": true,
  "terminal.external.osxExec": "iTerm.app",
  "go.docsTool": "gogetdoc",
  "go.testFlags": ["-v", "-count=1"],
  "go.buildTags": "",
  "go.buildFlags": [],
  "go.lintFlags": [],
  "go.vetFlags": [],
  "go.coverOnSave": false,
  "go.useCodeSnippetsOnFunctionSuggest": true,
  "go.gocodeAutoBuild": false,
  "go.goroot": "/usr/local/go",
  "go.gopath": "/Users/ligang/go",
  "go.inferGopath": true,
  "go.autocompleteUnimportedPackages": true,
  "go.gocodePackageLookupMode": "go",
  // "go.formatOnSave": true,
  "go.gotoSymbol.includeImports": true,
  "go.useCodeSnippetsOnFunctionSuggestWithoutType": true,
  "window.zoomLevel": 0,
  "debug.console.fontSize": 16,
  "debug.console.lineHeight": 30,
  "workbench.iconTheme": "file-icons",
  "editor.fontSize": 16,
  "files.autoSave": "afterDelay",
  "workbench.startupEditor": "newUntitledFile",
  "[javascript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "explorer.confirmDelete": false,
  "[vue]": {
    "editor.defaultFormatter": "octref.vetur"
  },
  "editor.quickSuggestions": {
    "strings": true
  },
  "editor.formatOnSave": true,
  "editor.formatOnType": true,
  "[jsonc]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "leetcode.endpoint": "leetcode-cn",
  "leetcode.workspaceFolder": "/Users/ligang/program/LeetCode",
  "python.linting.flake8Enabled": true,
  "python.formatting.provider": "yapf",
  "python.linting.flake8Args": ["--max-line-length=248"],
  "python.linting.pylintEnabled": false
}
```

```json
// 更新时间：2020-09-07
{
    "editor.quickSuggestions": {
        "strings": true
    },
    "files.autoSave": "afterDelay",
    "editor.fontSize": 16,
    "go.formatTool": "goimports",
    "go.useLanguageServer": true,
    "editor.minimap.renderCharacters": false,
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
    "window.zoomLevel": 0,
    "debug.console.fontSize": 16,
    "debug.console.lineHeight": 30,
    "workbench.iconTheme": "material-icon-theme",
    // vscode默认启用了根据文件类型自动设置tabsize的选项
    // "editor.detectIndentation": false,
    "editor.suggestSelection": "first",
    // #每次保存的时候自动格式化 
    "editor.formatOnSave": true,
    // #每次保存的时候将代码按eslint格式进行修复
    "editor.codeActionsOnSave": {
        "source.fixAll.eslint": true
    },
    "prettier.requireConfig": true,
    "prettier.tabWidth": 2,
    // prettier 设置语句末尾加分号 true 加分号 false 不加分好
    "prettier.semi": false,
    // prettier 设置强制单引号
    "prettier.singleQuote": true,
    // 针对[html]语言，配置替代编辑器设置
    "[html]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode"
        // "editor.defaultFormatter": "vscode.html-language-features"
    },
    // 针对[javascript]语言，配置替代编辑器设置
    "[javascript]": {
        "editor.tabSize": 2,
        "editor.defaultFormatter": "esbenp.prettier-vscode",
    },
    // 针对[vue]语言，配置替代编辑器设置
    "[vue]": {
        "editor.defaultFormatter": "octref.vetur",
        "editor.tabSize": 2
    },
    "eslint.codeActionsOnSave.mode": "all",
    "eslint.format.enable": true,
    "eslint.validate": [
        "javascript",
        "vue",
        "html"
    ],
    "eslint.options": {
        "extensions": [
            ".js",
            ".vue",
            ".ts",
            ".tsx"
        ]
    },
    // #这个按用户自身习惯选择
    "vetur.format.defaultFormatter.html": "js-beautify-html",
    // #让vue中的js按编辑器自带的ts格式进行格式化
    "vetur.format.defaultFormatter.js": "vscode-typescript",
    "vetur.format.defaultFormatterOptions": {
        "prettier": {
            // vue 在语句结尾处加上分号,false是不加分号
            "semi": false,
            "singleQuote": true
        },
        "js-beautify-html": {
            "wrap_line_length": 120,
            // 设置 vue 格式化后标签属性不换行
            "wrap_attributes": "auto",
            "end_with_newline": false
        },
        "prettyhtml": {
            "printWidth": 100,
            "singleQuote": false,
            "wrapAttributes": false,
            "sortAttributes": false
        }
    },
    "workbench.colorTheme": "Visual Studio Dark",
    "files.exclude": {
        ".idea": true
    },
    "explorer.confirmDragAndDrop": false,
    "hediet.vscode-drawio.local-storage": "eyIuZHJhd2lvLWNvbmZpZyI6IntcImxhbmd1YWdlXCI6XCJcIixcImN1c3RvbUZvbnRzXCI6W10sXCJsaWJyYXJpZXNcIjpcImdlbmVyYWxcIixcImN1c3RvbUxpYnJhcmllc1wiOltcIkwuc2NyYXRjaHBhZFwiXSxcInBsdWdpbnNcIjpbXSxcInJlY2VudENvbG9yc1wiOltdLFwiZm9ybWF0V2lkdGhcIjpcIjI0MFwiLFwiY3JlYXRlVGFyZ2V0XCI6ZmFsc2UsXCJwYWdlRm9ybWF0XCI6e1wieFwiOjAsXCJ5XCI6MCxcIndpZHRoXCI6ODI3LFwiaGVpZ2h0XCI6MTE2OX0sXCJzZWFyY2hcIjp0cnVlLFwic2hvd1N0YXJ0U2NyZWVuXCI6dHJ1ZSxcImdyaWRDb2xvclwiOlwiI2QwZDBkMFwiLFwiZGFya0dyaWRDb2xvclwiOlwiIzZlNmU2ZVwiLFwiYXV0b3NhdmVcIjp0cnVlLFwicmVzaXplSW1hZ2VzXCI6bnVsbCxcIm9wZW5Db3VudGVyXCI6MCxcInZlcnNpb25cIjoxOCxcInVuaXRcIjoxLFwiaXNSdWxlck9uXCI6ZmFsc2UsXCJ1aVwiOlwiXCJ9In0=",
    "cSpell.userWords": [
        "Nuxt",
        "Vuex",
        "bcrypt"
    ],
    "workbench.startupEditor": "newUntitledFile",
    "[jsonc]": {
        "editor.defaultFormatter": "vscode.json-language-features"
    },
}


{
    "editor.quickSuggestions": {
        "strings": true
    },
    "editor.fontSize": 16,
    // vscode默认启用了根据文件类型自动设置tabsize的选项
    // "editor.detectIndentation": false,
    "editor.suggestSelection": "first",
    // #每次保存的时候将代码按eslint格式进行修复
    "editor.codeActionsOnSave": {
        "source.fixAll.eslint": true
    },
    "files.exclude": {
        ".idea": true,
        ".github": true
    },
    "go.formatTool": "goimports",
    "go.useLanguageServer": true,
    "editor.minimap.renderCharacters": false,
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
    "window.zoomLevel": 0,
    "debug.console.fontSize": 16,
    "debug.console.lineHeight": 30,
    "workbench.iconTheme": "material-icon-theme",
    "prettier.tabWidth": 2,
    // prettier 设置强制单引号
    "prettier.singleQuote": true,
    "prettier.semi": false,
    // 针对[html]语言，配置替代编辑器设置
    "[html]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode"
        // "editor.defaultFormatter": "vscode.html-language-features"
    },
    "[css]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode"
    },
    // 针对[javascript]语言，配置替代编辑器设置
    "[javascript]": {
        "editor.tabSize": 2,
        "editor.defaultFormatter": "esbenp.prettier-vscode",
    },
    "typescript.preferences.quoteStyle": "single",
    "[typescript]": {
        "editor.tabSize": 2,
        "editor.defaultFormatter": "esbenp.prettier-vscode"
    },
    // 针对[vue]语言，配置替代编辑器设置
    "[vue]": {
        "editor.defaultFormatter": "octref.vetur",
        "editor.tabSize": 2
    },
    "eslint.codeActionsOnSave.mode": "all",
    "eslint.format.enable": true,
    "eslint.validate": [
        "javascript",
        "vue",
        "html"
    ],
    "eslint.options": {
        "extensions": [
            ".js",
            ".vue",
            ".ts",
            ".tsx"
        ]
    },
    // #这个按用户自身习惯选择
    "vetur.format.defaultFormatter.html": "js-beautify-html",
    // #让vue中的js按编辑器自带的ts格式进行格式化
    "vetur.format.defaultFormatter.js": "vscode-typescript",
    "vetur.format.defaultFormatterOptions": {
        "prettier": {
            // vue 在语句结尾处加上分号,false是不加分号
            "semi": false,
            "singleQuote": true
        },
        "js-beautify-html": {
            "wrap_line_length": 120,
            // 设置 vue 格式化后标签属性不换行
            // "wrap_attributes": "auto",
            "end_with_newline": false
        },
        "prettyhtml": {
            "printWidth": 100,
            "singleQuote": false,
            "wrapAttributes": false,
            "sortAttributes": false
        }
    },
    "workbench.colorTheme": "Visual Studio Dark",
    "explorer.confirmDragAndDrop": false,
    "hediet.vscode-drawio.local-storage": "eyIuZHJhd2lvLWNvbmZpZyI6IntcImxhbmd1YWdlXCI6XCJcIixcImN1c3RvbUZvbnRzXCI6W10sXCJsaWJyYXJpZXNcIjpcImdlbmVyYWxcIixcImN1c3RvbUxpYnJhcmllc1wiOltcIkwuc2NyYXRjaHBhZFwiXSxcInBsdWdpbnNcIjpbXSxcInJlY2VudENvbG9yc1wiOltdLFwiZm9ybWF0V2lkdGhcIjpcIjI0MFwiLFwiY3JlYXRlVGFyZ2V0XCI6ZmFsc2UsXCJwYWdlRm9ybWF0XCI6e1wieFwiOjAsXCJ5XCI6MCxcIndpZHRoXCI6ODI3LFwiaGVpZ2h0XCI6MTE2OX0sXCJzZWFyY2hcIjp0cnVlLFwic2hvd1N0YXJ0U2NyZWVuXCI6dHJ1ZSxcImdyaWRDb2xvclwiOlwiI2QwZDBkMFwiLFwiZGFya0dyaWRDb2xvclwiOlwiIzZlNmU2ZVwiLFwiYXV0b3NhdmVcIjp0cnVlLFwicmVzaXplSW1hZ2VzXCI6bnVsbCxcIm9wZW5Db3VudGVyXCI6MCxcInZlcnNpb25cIjoxOCxcInVuaXRcIjoxLFwiaXNSdWxlck9uXCI6ZmFsc2UsXCJ1aVwiOlwiXCJ9In0=",
     
    "workbench.startupEditor": "newUntitledFile",
    "[jsonc]": {
        "editor.defaultFormatter": "vscode.json-language-features"
    },
    "files.autoSave": "afterDelay",
    "editor.defaultFormatter": "esbenp.prettier-vscode",
    "editor.formatOnPaste": true,
    "editor.formatOnSave": true,
    "editor.formatOnType": true,
    "prettier.useTabs": true,
}
```



```json
{// 2021-05-21
	"workbench.startupEditor": "newUntitledFile",
	"workbench.iconTheme": "material-icon-theme",
	"debug.console.fontSize": 16,
	"debug.console.lineHeight": 30,
	"editor.codeActionsOnSave": {
		"source.fixAll": true
	},
	"editor.fontSize": 16,
	"editor.formatOnPaste": true,
	"editor.formatOnSave": true,
	"editor.formatOnType": true,
	"editor.quickSuggestions": {
		"strings": true
	},
	"editor.suggestSelection": "first",
	"explorer.confirmDragAndDrop": false,
	"files.autoSave": "afterDelay",
	"files.exclude": {
		"**/.github": true,
		"**/.idea": true,
		"**/.nuxt": true,
		"**/.vscode": true,
		"**/.classpath": true,
		"**/.project": true,
		"**/.settings": true,
		"**/.factorypath": true
	},
	"prettier.semi": false,
	"prettier.singleQuote": true,
	"prettier.tabWidth": 2,
	"prettier.useTabs": true,
	"prettier.vueIndentScriptAndStyle": true,
	"prettier.withNodeModules": true,
	"typescript.preferences.quoteStyle": "single",
	"typescript.format.semicolons": "ignore",
	"[css]": {
		"editor.defaultFormatter": "esbenp.prettier-vscode"
	},
	"[html]": {
		"editor.defaultFormatter": "esbenp.prettier-vscode",
		"editor.tabSize": 2
	},
	"[javascript]": {
		"editor.defaultFormatter": "esbenp.prettier-vscode",
		"editor.tabSize": 2
	},
	"[jsonc]": {
		"editor.defaultFormatter": "vscode.json-language-features"
	},
	"[typescript]": {
		"editor.defaultFormatter": "esbenp.prettier-vscode",
		"editor.tabSize": 2
	},
	"[vue]": {
		"editor.defaultFormatter": "octref.vetur",
		"editor.tabSize": 2,
	},
	"eslint.codeActionsOnSave.mode": "all",
	"eslint.format.enable": true,
	"eslint.validate": [
		"javascript",
		"vue",
		"html",
		"typescript"
	],
	"eslint.options": {
		"extensions": [
			".js",
			".vue",
			".ts",
			".tsx"
		]
	},
	// #这个按用户自身习惯选择 [js-beautify-html|none]
	"vetur.format.defaultFormatter.html": "none",
	// #让vue中的js按编辑器自带的ts格式进行格式化
	// "vetur.format.defaultFormatter.js": "vscode-typescript",
	"vetur.format.defaultFormatter.js": "none",
	"vetur.format.defaultFormatterOptions": {
		"prettier": {
			// vue 在语句结尾处加上分号,false是不加分号
			"semi": false,
			"singleQuote": true
		},
		"js-beautify-html": {
			// "wrap_line_length": 120,
			// 设置 vue 格式化后标签属性不换行 [auto|force|force-aligned|force-expand-multiline]
			"wrap_attributes": "force-aligned",
			"end_with_newline": false
		},
		"prettyhtml": {
			"printWidth": 120,
			"singleQuote": false,
			"wrapAttributes": true,
			"sortAttributes": true
		}
	},
	"editor.minimap.renderCharacters": false,
	"terminal.external.osxExec": "iTerm.app",
  "go.formatTool": "goimports",
	"go.useLanguageServer": true,
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
	"go.goroot": "/usr/local/Cellar/go",
	"go.gopath": "/Users/louis/go",
	"go.autocompleteUnimportedPackages": true,
	"cSpell.userWords": [
		"AUTOGENERATED",
		"Antd",
		"Datepicker",
		"Intelli",
		"Nuxt",
		"Parens",
		"Submenu",
		"Swal",
		"Treeview",
		"Vestibulum",
		"Vuex",
		"arity",
		"arrs",
		"auctor",
		"bcrypt",
		"browserslist",
		"camelcase",
		"clickaway",
		"cloudbase",
		"compat",
		"coverpage",
		"crossorigin",
		"datetimepicker",
		"docsify",
		"easypiechart",
		"echarts",
		"eget",
		"esnext",
		"esversion",
		"euismod",
		"excanvas",
		"felis",
		"flot",
		"fontawesome",
		"gonic",
		"gorm",
		"intbuf",
		"jinzhu",
		"kratos",
		"ldigits",
		"ligang",
		"mixins",
		"mollis",
		"natoque",
		"navbars",
		"nofollow",
		"nouislider",
		"nuxtjs",
		"offsetmust",
		"ornare",
		"penatibus",
		"porta",
		"postgres",
		"postgresql",
		"regexpu",
		"scripthost",
		"scrollbar",
		"semver",
		"signin",
		"sociis",
		"sparkline",
		"sqlc",
		"starman",
		"stretchr",
		"summernote",
		"togglebutton",
		"udigits",
		"unknow",
		"urna",
		"xorm"
	],
	"editor.linkedEditing": true,
	"[json]": {
		"editor.defaultFormatter": "vscode.json-language-features"
	},
	"liveServer.settings.donotShowInfoMsg": true,
	"python.showStartPage": true,
	// "html.format.endWithNewline": true,
	"editor.fontLigatures": true,
	"editor.fontFamily": "Monaco, 'Fira Code', Menlo, 'Courier New', monospace",
	"editor.autoClosingBrackets": "always",
	"editor.autoClosingQuotes": "always",
	"editor.tabSize": 2,
	"task.quickOpen.showAll": true,
	"tabnine.experimentalAutoImports": true,
	"workbench.editorAssociations": [
		{
			"viewType": "jupyter.notebook.ipynb",
			"filenamePattern": "*.ipynb"
		}
	],
	"leek-fund.stocks": [
		"sh000001",
		"sh000300",
		"sh000016",
		"sh000688",
		"hk03690",
		"hk00700",
		"usr_ixic",
		"usr_dji",
		"usr_inx",
		"sh600036"
	],
	"leek-fund.statusBarStock": [
		"sh600036"
	],
	"C_Cpp.updateChannel": "Insiders",
	"editor.find.autoFindInSelection": "always",
	"git.autofetch": true,
	"go.toolsManagement.autoUpdate": true,
	"http.proxyAuthorization": "false",
	"editor.semanticTokenColorCustomizations": null,
}
```

