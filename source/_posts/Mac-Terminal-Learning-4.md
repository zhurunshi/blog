---
title: Mac终端学习（四）：重定向和管道
categories: 终端
date: 2017-04-24 09:29:47
tags:
---
首先我们先做出一个A.java，输出一些简单的内容。

![A.java](http://upload-images.jianshu.io/upload_images/2319568-2a0f193a43be916a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
<!--more-->
**命令1（重定向）：**java A > out
**作用：**执行java程序A，把它在标准输出的结果写到名为out的文件里

![](http://upload-images.jianshu.io/upload_images/2319568-0fc45bfe110505e6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**命令2（重定向）：**java A < in
**作用：**执行java程序A，将in中的文本当做输入

![](http://upload-images.jianshu.io/upload_images/2319568-e40a8aeda63c4aa1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
**组合命令1和2：**java A < in > out

![](http://upload-images.jianshu.io/upload_images/2319568-7448ead3b1848e96.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
**在执行一个程序的时候，它的标准输入和标准输出可以被我们重定向到文件里面，使它可以从文件里读数据，往文件里面写数据。**
***
**命令3（管道）：**ls | more
**作用：**可以让ls的输出拿过来当做右侧more的输入，而more是按照一屏一屏的显示，所以最后是把ls的结果按一屏一屏的显示出来
**Tips：**按q退出

![](http://upload-images.jianshu.io/upload_images/2319568-7f0c3a2041a319cc.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
***
**命令4：**more [文件名] （cat [文件名]）
**作用：**查看文件内容

![](http://upload-images.jianshu.io/upload_images/2319568-31d52aa29738ed06.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
**命令5：**cat > [文件名]
**作用：**向文件里写文本
**Tips：**按control+d

![](http://upload-images.jianshu.io/upload_images/2319568-379e6add2b83cd75.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
***
**命令6：**touch [文件名]
**作用：仅仅使修改时间发生变化，而不改变文件内容**

![](http://upload-images.jianshu.io/upload_images/2319568-47b32a5d12afb95d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**其他作用：**touch [不存在的文件名]
**效果：**创建0字节的新文件

![](http://upload-images.jianshu.io/upload_images/2319568-37b0a659eb47b2ef.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
***
**命令7：**tail
**作用：**列出文件的最后几行

![](http://upload-images.jianshu.io/upload_images/2319568-e5681c54f4b9c7e0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
**扩展命令：**ls /usr/bin | tail -n 50
**作用：**列出最后50行

![](http://upload-images.jianshu.io/upload_images/2319568-1d1fe8afd2b91033.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**扩展命令：**ls /usr/bin | tail -n 50 | more
**作用：**将得到的结果分屏显示

![](http://upload-images.jianshu.io/upload_images/2319568-2fd8af1d268d6433.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**扩展命令：**tail -f [文件名]
**作用：**若有程序持续向该文件写入内容，则可以**实时查看该文件的内容**
***
**快捷键：**control+z
**作用：暂停**一直在运行的程序

**命令8：**bg
**作用：**搭配control+z使用，把刚才暂停下来的程序放到后台运行
**Tips：**如果此时想中断该程序，只能使用px命令查看进程，获取到进程号后，根据进程号杀掉该进程

**命令9：**java A.java > log.txt &
**作用：**直接在**后台**运行A.java，并将输出结果写入log.txt

**终端学习系列：**
[Mac终端学习（一）：基本操作](http://zhurunshi.com/Mac-Terminal-Learning-1/)
[Mac终端学习（二）：操作历史](http://zhurunshi.com/Mac-Terminal-Learning-2/)
[Mac终端学习（三）：进程管理](http://zhurunshi.com/Mac-Terminal-Learning-3/)
[Mac终端学习（四）：重定向和管道](http://zhurunshi.com/Mac-Terminal-Learning-4/)
[Mac终端学习（五）：万能的grep](http://zhurunshi.com/Mac-Terminal-Learning-5/)
[Mac终端学习（六）：环境变量](http://zhurunshi.com/Mac-Terminal-Learning-6/)
[Mac终端学习（七）：网络配置](http://zhurunshi.com/Mac-Terminal-Learning-7/)