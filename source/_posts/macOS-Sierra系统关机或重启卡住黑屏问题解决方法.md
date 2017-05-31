---
title: macOS Sierra系统关机或重启卡住黑屏问题解决方法
categories: Tips
date: 2016-09-26 00:43:42
tags:
---
引起新系统关机或重启黑屏卡住的原因就是：mysql服务无法关闭。
<!--more-->
解决方法就是：

![](http://upload-images.jianshu.io/upload_images/2319568-2d99a1f21725bb51.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

1.打开系统偏好设置 - MySQL（在最下方）；
2.将开机后自动启动MySQL服务（Automatically Start MySQL Server on Startup）的对勾去掉，然后再次重启，肯定还是会卡住的，因为mysql服务关不掉，此次强制关机，然后再次开机就会发现问题已经得到解决。