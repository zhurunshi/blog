---
title: Mac终端学习（七）：网络配置
categories: 终端
date: 2017-04-24 09:30:06
tags:
---
**命令1：**ifconfig
**作用：**列出本机所有的网络设备以及其上面的配置，主要指的是ip地址和mac地址

![](http://upload-images.jianshu.io/upload_images/2319568-13ede027a4f8f0e3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
<!--more-->
现在主要在连的就是en4，它是一个ip地址是192.168.1.105，然后它的状态时active（最后一行），而其他的状态都是inactive。
**其他用法：**ifconfig en4 down/up
**作用：**关闭（或打开）某个网络接口，比如en4
**Tips：**一般需要管理员权限，所以需要在前面加sudo命令

**其他用法：**sudo ifconfig en4 add 10.10.10.12 netmask 255.255.255.0
**作用：**给en4加入别的网段

![](http://upload-images.jianshu.io/upload_images/2319568-1d9ee83b5128fd61.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**其他用法：**sudo ifconfig en4 delete 10.10.10.12
**作用：**给en4删除指定网段

![](http://upload-images.jianshu.io/upload_images/2319568-574dd0ac0900a4fa.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**其他用法：**

    ifconfig en0 down // 关闭网卡设备（这里假设是en0）
    ifconfig en0 hw ether [MAC地址] // 修改MAC地址
    ifconfig en0 up // 重启网卡

**作用：**临时修改MAC地址

**其他用法：**

    ifconfig en0 down
    ifconfig en0 192.168.169.245 netmask 255.255.255.0

**作用：**临时修改内网ip地址

**命令2：**ping
**作用：**检测网络是否是连通状态

![](http://upload-images.jianshu.io/upload_images/2319568-86c0e9c1a6549b3c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
如果能ping通，说明它们的网关之间是通的，当然也可以用它来检测到外网是不是通的

**命令3：**netstat
**作用：**显示各种网络相关信息

**其他用法：**netstat -l
**作用：**列出本机进行监听的端口

**其他用法：**netstat -lt
**作用：**只列出tcp的连接，同理在l后面跟上u的话，将会列出各种udp的监听端口

**其他用法：**netstat -s
**作用：**查看统计数据

**其他用法：**netstat -p
**作用：**列出进程信息，你可以了解是哪一个程序在哪一个端口上做些什么事情

**其他用法：**netstat -pc
**作用：**会显示出实时更新的进程信息

**其他用法：**netstat -r
**作用：**查看路由表

![](http://upload-images.jianshu.io/upload_images/2319568-fed589a0a480b10f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
**其他用法：**netstat -i
**作用：**查看接口信息

![](http://upload-images.jianshu.io/upload_images/2319568-e05343f2c922de69.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**终端学习系列：**
[Mac终端学习（一）：基本操作](http://zhurunshi.com/Mac-Terminal-Learning-1/)
[Mac终端学习（二）：操作历史](http://zhurunshi.com/Mac-Terminal-Learning-2/)
[Mac终端学习（三）：进程管理](http://zhurunshi.com/Mac-Terminal-Learning-3/)
[Mac终端学习（四）：重定向和管道](http://zhurunshi.com/Mac-Terminal-Learning-4/)
[Mac终端学习（五）：万能的grep](http://zhurunshi.com/Mac-Terminal-Learning-5/)
[Mac终端学习（六）：环境变量](http://zhurunshi.com/Mac-Terminal-Learning-6/)
[Mac终端学习（七）：网络配置](http://zhurunshi.com/Mac-Terminal-Learning-7/)