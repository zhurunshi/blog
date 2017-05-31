---
title: Mac终端学习（一）：基本操作
categories: 终端
date: 2017-04-24 09:29:09
tags:
---
# 1 在目录间游走
**命令1：**pwd
**作用：**获取当前所在路径

![](http://upload-images.jianshu.io/upload_images/2319568-d588ba85bf6a1835.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
<!--more-->
***
**命令2：**ls (list)
**作用：**列出当前目录下的所有文件

![](http://upload-images.jianshu.io/upload_images/2319568-6018aa030e3bd23b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
**其他用法：**ls -l (long)
**作用：**用长格式列出来

![](http://upload-images.jianshu.io/upload_images/2319568-5e73db9d2a72b3d6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
**其他用法：**ls -a
**作用：**列出文件（包括隐藏的文件）

![](http://upload-images.jianshu.io/upload_images/2319568-98eafa97028f2e77.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
**其他用法：**ls -al
**作用：**以长格式列出文件（包括隐藏的文件）

![](http://upload-images.jianshu.io/upload_images/2319568-63d303c28f7eb2c6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


***
**命令3：**cd
**作用：**进行目录之间的相互跳转
**Tips1：**可以利用Tab键将目录名补全
**Tips2：**可以输入cd后，将文件拖入终端，这样可以显示该文件的目录

![](http://upload-images.jianshu.io/upload_images/2319568-443b57df941c3619.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
**其他用法：**cd (不带任何参数)
**作用：**返回家目录

![](http://upload-images.jianshu.io/upload_images/2319568-275892e169aa7d01.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
**其他用法：**cd ~
**作用：**返回家目录
**Tips：**可以利用cd ~/Music快速到达该目录

![](http://upload-images.jianshu.io/upload_images/2319568-5bcc90ab30f88fac.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
**Tips：**利用cd ~Guest/进入Guest用户的家目录
由于本机没有其他用户登录，所以无法演示该效果

**其他用法：**cd -
**作用：**返回上一个目录，你总是可以在两个目录之间进行切换

![](http://upload-images.jianshu.io/upload_images/2319568-441ee4afa3f9a772.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**其他用法：**cd(空格)..
**作用：**返回上一层目录
**Tips：**..表示上一层目录，而.表示当前目录
**Tips：**如果想要执行当前目录可执行文件a，需要输入./a，表示当前目录下的那个a
**说明：**这样做可以提高安全性，不会与命令的英文发生歧义

![](http://upload-images.jianshu.io/upload_images/2319568-1fe6b53c29e44883.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
# 2 目录文件操作
**命令1：**mkdir [文件名] (make dir)
**作用：**新建文件夹

![](http://upload-images.jianshu.io/upload_images/2319568-b9aa39e5a55e0a91.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
***
**命令2：**rmdir [文件名] (remove dir)
**作用：**删除**文件夹**

![](http://upload-images.jianshu.io/upload_images/2319568-1088a0a681af8b2b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
**Tips：**如果文件夹内不为空，则无法用rmdir删除文件夹

![](http://upload-images.jianshu.io/upload_images/2319568-f0de5c0c61d6524c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
***
**命令3：**mv [原文件名] [新文件名] (move)
**作用：**把文件从一个地方移到另一个地方，但是当没有给出另外一个目录时，移动的现象就是为其更改了名字

![](http://upload-images.jianshu.io/upload_images/2319568-8957ee122477c2c4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](http://upload-images.jianshu.io/upload_images/2319568-d8989d0d639ef855.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
***
**命令4：**rm [文件名] (remove)
**作用：**删除文件
**注意：用rm删除掉的文件是无法从回收站中找回的！！**
![](http://upload-images.jianshu.io/upload_images/2319568-38814a2000456cdc.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**Tips：**不能使用rm来删除文件夹

![](http://upload-images.jianshu.io/upload_images/2319568-050983bde73de369.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**Tips：**rm -rf [目录] (r-recursive递归的；f-force强迫的)
**危险操作：使用rm递归删除文件夹及文件夹内所有内容，无法挽回**

![](http://upload-images.jianshu.io/upload_images/2319568-9bc51fca99901bf7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
***
**命令5：**cp [带目录文件] [目标目录]
**作用：**复制黏贴

![](http://upload-images.jianshu.io/upload_images/2319568-b1b4feae37f74e8f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
**其他用法：**cp -R [目录] [目标目录]
**作用：**用于带目录文件的复制
***
**命令6：**mv [原文件] [目标目录] (同命令3)
**作用：**移动

![](http://upload-images.jianshu.io/upload_images/2319568-0fd49d500cbfe913.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
# 3 查看使用手册
**命令1：**man [命令]
**例如：**man cp
**作用：**查看该命令的使用手册
**Tips：**输入q来直接退出

![](http://upload-images.jianshu.io/upload_images/2319568-f3bdc495ba41f63d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
**终端学习系列：**
[Mac终端学习（一）：基本操作](http://zhurunshi.com/Mac-Terminal-Learning-1/)
[Mac终端学习（二）：操作历史](http://zhurunshi.com/Mac-Terminal-Learning-2/)
[Mac终端学习（三）：进程管理](http://zhurunshi.com/Mac-Terminal-Learning-3/)
[Mac终端学习（四）：重定向和管道](http://zhurunshi.com/Mac-Terminal-Learning-4/)
[Mac终端学习（五）：万能的grep](http://zhurunshi.com/Mac-Terminal-Learning-5/)
[Mac终端学习（六）：环境变量](http://zhurunshi.com/Mac-Terminal-Learning-6/)
[Mac终端学习（七）：网络配置](http://zhurunshi.com/Mac-Terminal-Learning-7/)