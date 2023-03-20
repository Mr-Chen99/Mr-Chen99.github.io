---
title: Git操作整理
date: 2023-03-20 14:34:40
categories:
- Git
tags:
- 项目
---

## Github上Fork的项目如何获取源更新

>  1、添加上游项目地址(URL为Fork的源项目地址)
``` cmd
    git remote add upstream URL
```

> 2、查看远程仓库信息(可以看到上游项目地址已经添加进来了)
```cmd
    git remote -v
```
![img](git-fork.png)

> 3、获取上游项目更新(获取到的更新会被保存在本地的 upstream/master 分支)
```cmd
    git fetch upstream
```
> 4、合并到本地分支(如果不是master分支，要切换到 master 分支，然后合并 upstream/master 分支)
```cmd
    git merge upstream/master
```
>5、把更新后的代码push到git上
```cmd
    git push origin master
```
