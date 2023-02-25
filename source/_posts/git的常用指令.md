---
title: git的常用指令
date: 2022-05-20 09:49:10
tags: git
categories: note
# 加入时间线
selected: true
---

git 提交/推送/拉取等一些常用的指令

<!-- more -->

## 一、提交代码到仓库
### 添加到本地仓库
``` html
//添加指定文件
$ git add <xxx>

//添加全部文件
$ git add .
```

### 提交到本地仓库，并添加描述信息
``` html
$ git commit -m <message>
```

### 推送到远程
``` html
$ git push origin master
```

## 二、拉取代码到本地
### 克隆或拉取代码
``` html
//克隆
$ git clone http://xxx

//拉取
$ git pull https://xxx

//拉取关联仓库分支的代码
$ git pull origin master
```

## 三、远程仓库
### 添加远程仓库绑定
``` html
$ git remote add origin <ssh>
```

### 解除远程仓库绑定
``` html
$ git remote rm origin
```

### 查看绑定的仓库信息
``` html
$ git remote -v
```

## 四、本地仓库
### 新建本地仓库
``` html
$ git init
```
### 删除本地仓库
直接删除 .git 文件夹即可，默认情况下 .git 文件夹是 *(隐藏的)*