##### 1、删除 git 仓库中的文件

```shell
## 删除文件
~ % git rm --cached <filename>

## 删除文件夹
~ % git rm --cached -r <filename>
```

##### 2、本地仓库上传远程仓库

```shell
## 设置远程仓库
~ % git remote add origin ***/***.git

## 拉取远程仓库地址
~ % git pull --rebase origin master

## 推送代码到仓库
~ % git push origin master
```

