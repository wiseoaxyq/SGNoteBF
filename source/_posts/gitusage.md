---
title: git的使用
date: 2021-08-03 15:29:39
tags: note
categories: note
thumbnail: https://z3.ax1x.com/2021/08/16/f2bllQ.png
---
## 一、本地仓库
首先，把你想要创建版本库的文件夹打开，可以是有项目的文件夹，也可以是空文件夹。（windows用户请注意避免中文路径哦！）
右键选择 “git bash here”  ~~前提是你已经装了git（不是）~~
> 输入：
``$ git init``
这时候你的文件夹里会出现 .git 这样一个文件夹 *（是隐藏的）*
这时候你的本地版本库就算已经建好啦！

<!-- more -->

现在，我们先编写一个 readme.txt 文件，内容如下：
```
Git is a version control system.
Git is free software
```
放到你git版本库的目录下 *（子目录也可以哦）*

接下来就可以开始将你的文件放进git仓库了
#### 1.告诉git把文件添加到仓库：
```
$ git add 文件名
$ git add . //所有文件
```
#### 2.告诉git把文件提交到仓库：
``$ git commit -m '本次提交的说明'``
说明记录会保存到 readme.txt 文件中

#### 小结：
1. 初始化一个Git仓库使用 ``git init`` 命令
2. 1. 添加文件到仓库使用 ``git add <file>`` （可重复添加）
   2. 使用命令 ``git commit -m <message>``，完成提交


## 二、远程仓库
我一般习惯将代码托管到 GitHub 上，那么 git 的远程仓库就很管用啦。

首先，我们登录 GitHub ，创建一个新的 repository 仓库，这样我们就拥有了一个远程仓库啦！

接着，回到要上传到远程仓库的本地仓库，右键 git bash here，输入以下命令：
``$ git remote add origin <ssh>``

添加后，远程库的名字就是 origin，这是Git的默认叫法，也可以改成其它的。

下一步就可以将本地库的所有内容推送到远程库上了：
``$ git push origin master //master是分支名称``  

推送成功后，可以立刻查看 GitHub 上的内容，已经跟本地的一模一样了

#### 删除远程库：
有时候 ssh 不小心输错了，可以通过``$ git remote rm origin``来删除远程库，删除远程库并不会影响远程库，只是解除了本地与远程的绑定关系

在删除链接前，可以先用``$ git remote -v``查看远程库信息

#### 小结：
1. 要关联一个远程库，使用命令：``git remote add origin <ssh>``；
2. 关联后，使用命令：``git push -u origin master`` 第一次推送master分支的所有内容；
3. 此后，每次本地提交后，只要有必要，就可以使用``git push origin master``推送最新修改。