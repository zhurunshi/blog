---
title: Mac终端学习（五）：万能的grep
categories: 终端
date: 2017-04-24 09:29:53
tags:
---
**命令1：**grep 800 log.txt
**作用：**从log.txt中找出800位置的数据

**命令2：**grep -n 800 log.txt
**作用：**从log.txt中找出800位置的数据，并在前面加上行号

**命令3：**grep (-n) Hello \* (是否加上行号)
**作用：**从当前目录下的所有文件中找出出现过Hello的文件

![](http://upload-images.jianshu.io/upload_images/2319568-7fd351b3a442886d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
<!--more-->
**命令4：**ls /usr/bin | grep ls
**作用：**查看/usr/bin目录下面带ls的目录

![](http://upload-images.jianshu.io/upload_images/2319568-092a00adbf3c5c7c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**命令5**：wc
**与命令4的组合：**ls /usr/bin | grep ls | wc
**作用：**计算出单词的数量

![18行 18个单词 148个字符](http://upload-images.jianshu.io/upload_images/2319568-6a6f5bfa85acf975.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**终端学习系列：**
[Mac终端学习（一）：基本操作](http://zhurunshi.com/Mac-Terminal-Learning-1/)
[Mac终端学习（二）：操作历史](http://zhurunshi.com/Mac-Terminal-Learning-2/)
[Mac终端学习（三）：进程管理](http://zhurunshi.com/Mac-Terminal-Learning-3/)
[Mac终端学习（四）：重定向和管道](http://zhurunshi.com/Mac-Terminal-Learning-4/)
[Mac终端学习（五）：万能的grep](http://zhurunshi.com/Mac-Terminal-Learning-5/)
[Mac终端学习（六）：环境变量](http://zhurunshi.com/Mac-Terminal-Learning-6/)
[Mac终端学习（七）：网络配置](http://zhurunshi.com/Mac-Terminal-Learning-7/)