#### mac卸载和安装openjdk

##### 1、卸载jdk(可省略)

```
java -version 

# 检查是否有jdk，有且非openJDK则卸载，否则跳过此步骤，打开终端输入：
sudo rm -fr /Library/Internet\ Plug-Ins/JavaAppletPlugin.plugin
sudo rm -fr /Library/PreferencesPanes/JavaControlPanel.prefpane
```

###### 查找当前版本输入：

```
ls /Library/Java/JavaVirtualMachines/
```

###### 输出样例：

```
jdk-9.0.1.jdk
```

###### 输入:

```
sudo rm -rf /Library/Java/JavaVirtualMachines/jdk-9.0.1.jdk
```

##### 2、安装openJDK

```
# 输入：
brew tap adoptopenjdk/openjdk
brew search /adoptopenjdk/
brew install --cask adoptopenjdk8

# 验证：
java -version
```

