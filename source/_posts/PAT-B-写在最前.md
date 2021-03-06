---
title: PAT-B 写在最前
date: 2016-09-17 00:26:39
categories: PAT-B
tags:
---
暑假听说想考浙大的小伙伴都去刷PAT了，勾起来我的好奇心。听说PAT对找工作也有一定的帮助，于是我也光荣的加入到了刷题的行列中来。
<!--more-->
首先，由于我个人发展方向的缘故，我选择了使用Java语言来做题，但是做题的过程中，发现Java语言的效率实在堪忧，这里没有贬低Java语言的意思，而是由于Java的语言类型以及类加载等各种各样机制存在的缘故，使其速度慢于C/C++等语言，这也是我在做了快20道题时才逐渐发现的。

如果是竞赛的话，会适当放宽对Java语言的速度要求，可是在PAT的帮助一栏中写到：

>**不同语言的时间限制和内存限制是相同的吗？**

>是相同的，我们认为选择合适的编程语言也是一项必备技能，所以没有为不同语言设置不同的限制条件

所以，最终我放弃了Java语言，从而选用了C++来刷题。

写在这里希望能让准备PAT的考生少走一些弯路。

另外需要注意的是：

1. PAT的考场一般都会配备了VS2010旗舰版，所以建议想要考试的同学，尽量使用此编译器进行练习。

2. 由于VS2010没能很好的支持C99标准，这通常体现在变长数组的声明过程中，而PAT的判题系统是4.7.2版本的g++，是支持C99标准的，所以可以在程序中使用变量来声明数组。