---
title: git
date: 2023-11-19 15:14:05
tags: git
---
设置用户信息

``` bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

查看配置的用户信息

``` bash
git config --global  --list 
```

初始化当前文件夹为仓库

``` bash
git init 
```

文件创建操作

``` bash
mkdir my_project #创建一个叫my_project的文件夹。使用mkdir -p 可以创建多层文件夹
cd my_project #转到my_project文件夹。之后可以使用git init指令设置仓库。cd意为change direction
```

查看当前仓库信息

``` bash
git config --local  --list 
```

添加绑定远程仓库

```bash
    git remote add origin [远程仓库URL]//
```

添加文件到暂存区

``` bash
git add README.md
```

推送到远程仓库

``` bash
git push -u origin master
```

拉取项目注意需要的话用cd指令切换本地目标文件夹

``` bash
git clone [远程仓库URL] #会在当前文件夹下创建一个项目同名的文件夹，里面才是项目源代码
```
