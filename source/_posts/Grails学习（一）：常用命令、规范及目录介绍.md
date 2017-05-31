---
title: Grails学习（一）：常用命令、规范及目录介绍
categories: Grails
date: 2017-04-04 15:52:35
tags:
---

# 1 常用命令

	grails -version // 查看版本
	grails create-app [project-name] // 创建项目
	grails generate-all [package-name].[domain-name] // 根据领域类（Domain Class）创建Controller、View、Service、Test
	grails run-app // 运行项目
	grails clean // 清除项目缓存，重新构建项目

如果这些命令无法满足你的需要，请移步：
http://docs.grails.org/latest/ref/Command%20Line/Usage.html
查看网页右侧的“Quick Reference”来了解对应命令的使用方法。
<!--more-->
# 2 命名规范
## 2.1 controllers
例如：NoticeController
首字母大写的驼峰法，后面加上Controller
controller中的方法命名方式为：首字母小写的驼峰法
例如：def getList(...)

## 2.2 domain
例如：Notice
首字母大写的名词或动词
领域类中的变量对应数据库中的字段，命名方式为：首字母小写
的驼峰法

## 2.3 jobs
例如：NoticeJob
首字母大写的驼峰法，后面加上Job

## 2.4 services
例如：NoticeService
与domain类对应的名词，后面加上Service，首字母大写的驼峰法

## 2.5 taglib
例如：NoticeLib
首字母大写的驼峰法，后面加上Lib

## 2.6 test(src/)
例如：NoticeSpec
首字母大写的驼峰法，在Grails3.0 以上的命名方式为与domain类对应的名词，后面加上Spec，首字母大写的驼峰法

# 3 常用目录介绍

![Grails目录介绍](http://upload-images.jianshu.io/upload_images/2319568-d97f5218c79701cc.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

build目录：存放由.java或者.groovy文件生成的class文件
grails-app/assets目录：放置字体文件（fonts）、图像文件（images）、JS文件（javascripts）和层叠样式表文件（stylesheets）
grails-app/conf目录：放置系统的各项配置（如数据源配置、环境配置、hibernate配置等）
grails-app/controllers目录：放置每个页面调用的方法逻辑处理请求，创建或准备响应
grails-app/domain目录：实体类，在Grails框架里面称之为领域类，对应数据库中的每一个表结构
grails-app/i18n目录：负责国际化相关，这里从其中根据提示语代码调用相关提示语
grails-app/init目录：负责程序运行初始化操作
grails-app/jobs目录：可以写一些定时器，定时触发指定操作
grails-app/services目录：将复杂的逻辑实现写在该目录下，有利于代码的重用
grails-app/taglib目录：标签库，gsp网页支持定制tag库，可以在运行时重载。
grails-app/views目录：gsp网页，类似jsp

查看Grail框架的更详细说明，请查阅官方文档：
http://docs.grails.org/latest/