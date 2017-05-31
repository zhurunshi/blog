---
title: Mac终端学习（六）：环境变量
categories: 终端
date: 2017-04-24 09:30:00
tags:
---
前言：
我们在终端里能够执行的一条条命令（ls cd cp mv等等），都是放在/bin下面的一个个小程序。
之所以能够直接运行，不需要再其前面添加目录。
是因为将这些目录都添加到了环境变量PATH中

**命令1：**set | grep PATH
**作用：**查看环境变量

![](http://upload-images.jianshu.io/upload_images/2319568-6f29f68c22dc2cd5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
虽然东西很多，但是可以看出来他们之间使用了冒号分隔开
<!--more-->
**命令2：**PATH=$PATH:~/bin
**作用：**将其他文件夹路径（本机用户下面的bin目录）添加到PATH
**Tips：**
这样做只是**一次性**的，也就是说在当前终端，是可以直接生效的，但是当你关闭后，重新打开终端，这个操作是不被保存的。
在/etc/profile这个文件是**任何人打开终端都会执行的，是系统级的profile**。
如果我们想自定义自己的profile，可以在自己的家目录下新建文件命名为：.profile，这个文件会在你打开终端时自动执行
我们将刚刚的命令2输入其中，然后保存退出（vim下使用:wq）
这样的话，在我们刚刚已经登录的终端里面它还是不起作用的，假如你希望它可以立刻生效，你可以使用source命令。

**命令3：**source
**作用：**使Shell读入指定的Shell程序文件并依次执行文件中的所有语句，**通常用于重新执行刚修改的初始化文件，使之立即生效，而不必注销并重新登录**
**例如：**source .profile
至此，每次当你打开终端的时候，将会默认执行一遍.profile中的命令。

**终端学习系列：**
[Mac终端学习（一）：基本操作](http://zhurunshi.com/Mac-Terminal-Learning-1/)
[Mac终端学习（二）：操作历史](http://zhurunshi.com/Mac-Terminal-Learning-2/)
[Mac终端学习（三）：进程管理](http://zhurunshi.com/Mac-Terminal-Learning-3/)
[Mac终端学习（四）：重定向和管道](http://zhurunshi.com/Mac-Terminal-Learning-4/)
[Mac终端学习（五）：万能的grep](http://zhurunshi.com/Mac-Terminal-Learning-5/)
[Mac终端学习（六）：环境变量](http://zhurunshi.com/Mac-Terminal-Learning-6/)
[Mac终端学习（七）：网络配置](http://zhurunshi.com/Mac-Terminal-Learning-7/)