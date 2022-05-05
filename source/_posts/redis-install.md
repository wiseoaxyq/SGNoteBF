title: redis的安装
tags:
  - note
categories:
  - note
thumbnail: 'https://s4.ax1x.com/2022/01/10/7E2SBT.png'
date: 2022-01-10 14:07:00
---
<img src="https://s4.ax1x.com/2022/01/10/7ErYuD.png" alt="redis" width="auto" height="50">  

## redis Windows环境下的安装
github上有redis的安装包：<https://github.com/tporadowski/redis/releases>
这里主要介绍的是redis.zip的安装。

<!-- more -->

##### 1、下载redis：
首先下载redis for windows.zip，redis支持32/64位，但github上一般都是64位的。下载解压后将解压好的文件夹放到你要安装的目录下。
<img src="https://s4.ax1x.com/2022/01/10/7ErPNn.png" alt="redis" width="auto" height="300">

##### 2、执行安装：
cmd进入redis所在的安装文件夹运行以下代码
```
redis-server.exe redis.windows.conf
```
tips:不想每次都cmd进入安装文件夹的话可以将redis的安装路径添加至环境变量中，输入之后显示以下界面 👇
<img src="https://s4.ax1x.com/2022/01/10/7ErVjU.png" alt="redis" width="auto" height="300">

这时候再打开一个cmd窗口，切换到安装目录，为redis设置键值对 👇
```
redis-cli.exe -h 127.0.0.1 -p 6379   // 6379 为默认端口号，可按照需求设置端口号
set myKey abc                       //设置键值对
get myKey                          // 测试取出键值对
```
<img src="https://s4.ax1x.com/2022/01/10/7Erihq.png" alt="redis" width="auto" height="150">

这时就已经完成redis的安装了，但是每次启动redis都需要输入```redis-server.exe redis.windows.conf```,而且cmd窗口不能关闭，services.msc中也没有redis的服务。
这时就需要将redis服务添加进windows中了。

##### 3、添加redis服务：
cmd切换到redis的安装目录，执行以下代码，添加redis服务（我这里已经添加了） 👇
```
redis-server --service-install redis.windows.conf
```
<img src="https://s4.ax1x.com/2022/01/10/7ErA3V.png" alt="redis" width="auto" height="150">

之后到services.msc中查看，已经将redis服务添加，之后直接在这里启动redis服务即可使用，并且是开机自启。
<img src="https://s4.ax1x.com/2022/01/10/7Erp7j.png" alt="redis" width="auto" height="200">

##### 4、修改redis的端口号
打开redis的安装目录，打开redis.windows.conf文件，找到port,将端口号更改为需要的端口号。
<img src="https://s4.ax1x.com/2022/01/10/7EreuF.png" alt="redis" width="auto" height="300">

之后重启redis服务即可。