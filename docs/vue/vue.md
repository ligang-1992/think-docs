### 初始化项目

```
# 命令行初始化
～% vue create xxx(项目名称)

# 图形化界面初始化
～% vue ui
```

### Vue 项目设置端口

```
# 1、在项目根目录下，新建 vue.config.js 文件
# 2、配置
module.exports = {
  devServer: {
    port: 3000, // 端口
  },
  ...
};


```

