---
title: Mac终端学习（三）：进程管理
categories: 终端
date: 2017-04-24 09:29:40
tags:
---
**命令1：**ps
**作用：**查看当前终端运行的程序

![](http://upload-images.jianshu.io/upload_images/2319568-4a4a8e31dd346486.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
**其他用法：**ps ax
**作用：**列出这台电脑上正在运行的所有程序

![](http://upload-images.jianshu.io/upload_images/2319568-9abc467965b21080.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
<!--more-->
***
**命令2：**top
**作用：**显示这台计算机上有哪些进程，它们占据了多少内存、CPU、负载等
**Tips：**按q退出

![](http://upload-images.jianshu.io/upload_images/2319568-09397b0a23f9b7f1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
***
**命令3：**kill [PID]
**作用：**结束指定进程ID的进程
**具体做法：**先使用top命令查看想要结束进程的PID，然后使用命令kill [PID]
**Tips：**如果遇到无法杀掉的进程，输入命令sudo kill -9 [PID] (伪装超级管理员，强迫杀掉该进程)，接着输入自己用户的密码（前提是自己这个用户具有sudo的资格）

**终端学习系列：**
[Mac终端学习（一）：基本操作](http://zhurunshi.com/Mac-Terminal-Learning-1/)
[Mac终端学习（二）：操作历史](http://zhurunshi.com/Mac-Terminal-Learning-2/)
[Mac终端学习（三）：进程管理](http://zhurunshi.com/Mac-Terminal-Learning-3/)
[Mac终端学习（四）：重定向和管道](http://zhurunshi.com/Mac-Terminal-Learning-4/)
[Mac终端学习（五）：万能的grep](http://zhurunshi.com/Mac-Terminal-Learning-5/)
[Mac终端学习（六）：环境变量](http://zhurunshi.com/Mac-Terminal-Learning-6/)
[Mac终端学习（七）：网络配置](http://zhurunshi.com/Mac-Terminal-Learning-7/)