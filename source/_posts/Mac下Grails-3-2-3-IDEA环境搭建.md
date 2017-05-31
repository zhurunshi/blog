---
title: Mac下Grails(3.2.3)+IDEA环境搭建
categories: Grails
date: 2017-04-01 22:52:28
tags:
---
# 1. 安装JDK
这里以安装JDK1.7为例，因为Grails3.0以上均需要JDK1.7及更高版本
从官网下载.dmg格式直接安装即可，官网链接：http://www.oracle.com
打开终端，输入

	java -version

显示如下所示内容，即安装成功

	java version "1.7.0_79"
	Java(TM) SE Runtime Environment (build 1.7.0_79-b15)
	Java HotSpot(TM) 64-Bit Server VM (build 24.79-b02, mixed mode)

<!--more-->
# 2. 安装Grails
打开终端，输入

	curl -s get.sdkman.io | bash

根据屏幕上的指示完成安装SDKMAN（中文名为:软件开发工具管理器），这个工具的主要用途是用来解决在类Unix操作系统（如Mac或Linux等）中多种版本开发工具的切换, 安装和卸载的工作，然后键入如下命令

	source "$HOME/.sdkman/bin/sdkman-init.sh"

接着安装Grails

	sdk install grails

最终，输入

	grails -version

显示如下内容，即安装成功

	| Grails Version: 3.2.3
	| Groovy Version: 2.4.7
	| JVM Version: 1.7.0_79

# 3. 创建一个Grails项目
用cd命令切换到一个文件夹内，输入命令

	grails create-app [project-name]

# 4. 打开项目
创建完成后，用IDEA打开该项目，如图所示。
![](http://upload-images.jianshu.io/upload_images/2319568-7e887bff3458684e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![](http://upload-images.jianshu.io/upload_images/2319568-a8c2d562a9b03091.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
# 5.运行项目
## 5.1 使用内置终端运行
打开项目后，项目结构如左侧所示。
![Grails项目结构](http://upload-images.jianshu.io/upload_images/2319568-8dbc4462d04e494e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
点击左下角按钮打开IDEA内置终端，目录默认是该项目下，比较方便，输入

	grails run-app

运行项目，看到下面提示，则运行成功。

	Grails application running at http://localhost:8080 in environment: development

打开浏览器，输入该地址，页面如下图所示（Windows会有所不同），则环境全部搭建完成。
![](http://upload-images.jianshu.io/upload_images/2319568-94a3be684aec4e3e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
若想要停止服务，点击内置终端左侧的按钮即可。
![](http://upload-images.jianshu.io/upload_images/2319568-bf7a1e11ea0495f8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 5.2 配置命令运行

![](http://upload-images.jianshu.io/upload_images/2319568-9201d6de0dbd0b84.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
如果此处没有配置的话，点击此处，在下拉菜单中选择“Edit Configurations...”，然后点击“+”加号，选择Grails，写入以下参数，Application中填写项目名称，然后保存配置。
![](http://upload-images.jianshu.io/upload_images/2319568-34c233a3e9846198.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
最后点击右上角的绿色运行按钮，即可启动Grails项目。
启动成功后页面与5.1中相同，这里就不再赘述。