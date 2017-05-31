---
title: 从零开始学习基于WebMagic的Java爬虫（一）：环境配置
categories: Java
date: 2017-04-24 09:43:26
tags:
---
# 1 扫盲
## 1.1 网络爬虫
[网络爬虫](http://baike.baidu.com/item/%E7%BD%91%E7%BB%9C%E7%88%AC%E8%99%AB)，是一种按照一定的规则，自动地抓取万维网信息的程序或者脚本。
## 1.2 WebMagic
[WebMagic](http://webmagic.io/)是一个简单灵活的Java爬虫框架。基于WebMagic，你可以快速开发出一个高效、易维护的爬虫。
<!--more-->
# 2 环境搭建
## 2.1 Maven
[Maven](http://baike.baidu.com/item/Maven)项目对象模型，可以通过一小段描述信息来管理项目的构建，报告和文档的软件项目管理工具。
上面那句话看不懂的也没关系，暂时知道这次是利用Maven来管理JAR包就行。
当然，如果不使用Maven也可以手动下载WebMagic框架的JAR包。
### 2.1.1 手动下载JAR包（不推荐）
访问：[https://github.com/code4craft/webmagic/releases/tag/webmagic-parent-0.6.1](https://github.com/code4craft/webmagic/releases/tag/webmagic-parent-0.6.1)，点击红色箭头链接，进行下载，下载完成后，将JAR包放在lib里面即可。
![](http://upload-images.jianshu.io/upload_images/2319568-929a302815cb6e10.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
**如果你没有使用过Maven，那么一定不要错过这次入门的机会。**
### 2.1.2 使用Maven管理本地JAR包
首先先访问网址：[http://maven.apache.org/download.cgi](http://maven.apache.org/download.cgi)，二者任选其一下载后解压，将其放到自己平时常用位置后。
例如：/Library/apache-maven-3.3.9
【macOS】
打开终端，键入如下命令：

    $ vi ~/.bash_profile

添加下列两行代码，之后保存并退出Vi：

    export M2_HOME=/Library/apache-maven-3.3.9
    export PATH=$PATH:$M2_HOME/bin

顺便说一下，vi进入插入模式先按i，接着输入上述两行代码，输入完成后，按":wq"回车，即可保存退出。
【Windows】
配置环境变量即可，详情参照
[http://jingyan.baidu.com/article/1709ad808ad49f4634c4f00d.html](http://jingyan.baidu.com/article/1709ad808ad49f4634c4f00d.html)
# 3 项目新建、配置与运行
打开IDEA，新建项目
![](http://upload-images.jianshu.io/upload_images/2319568-b88365f1c8957a7f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](http://upload-images.jianshu.io/upload_images/2319568-5f9587c21e0207ca.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](http://upload-images.jianshu.io/upload_images/2319568-f88fb95955492b34.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](http://upload-images.jianshu.io/upload_images/2319568-da913f2a970bb706.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![选择自动引入Maven项目](http://upload-images.jianshu.io/upload_images/2319568-87064c664389a9d2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![在pom.xml中插入红框内配置语句](http://upload-images.jianshu.io/upload_images/2319568-027a36fe818fbb70.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![点击右侧Maven Projects列表刷新Maven项目](http://upload-images.jianshu.io/upload_images/2319568-fdcf335e7fc7e1d0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![在src/main/resources目录下新建文件命名为log4j.properties](http://upload-images.jianshu.io/upload_images/2319568-72accec965e2e662.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
并向其中写入以下代码。

    log4j.rootCategory=INFO, stdout , R   

    log4j.appender.stdout=org.apache.log4j.ConsoleAppender   
    log4j.appender.stdout.layout=org.apache.log4j.PatternLayout   
    log4j.appender.stdout.layout.ConversionPattern=[QC] %p [%t] %C.%M(%L) | %m%n   

    log4j.appender.R=org.apache.log4j.DailyRollingFileAppender   
    log4j.appender.R.File=D:\\Tomcat 5.5\\logs\\qc.log   
    log4j.appender.R.layout=org.apache.log4j.PatternLayout   
    1log4j.appender.R.layout.ConversionPattern=%d-[TS] %p %t %c - %m%n   

    log4j.logger.com.neusoft=DEBUG   
    log4j.logger.com.opensymphony.oscache=ERROR   
    log4j.logger.net.sf.navigator=ERROR   
    log4j.logger.org.apache.commons=ERROR   
    log4j.logger.org.apache.struts=WARN   
    log4j.logger.org.displaytag=ERROR   
    log4j.logger.org.springframework=DEBUG   
    log4j.logger.com.ibatis.db=WARN   
    log4j.logger.org.apache.velocity=FATAL   

    log4j.logger.com.canoo.webtest=WARN   

    log4j.logger.org.hibernate.ps.PreparedStatementCache=WARN   
    log4j.logger.org.hibernate=DEBUG   
    log4j.logger.org.logicalcobwebs=WARN  

    log4j.rootCategory=INFO, stdout , R

    log4j.appender.stdout=org.apache.log4j.ConsoleAppender
    log4j.appender.stdout.layout=org.apache.log4j.PatternLayout
    log4j.appender.stdout.layout.ConversionPattern=[QC] %p [%t] %C.%M(%L) | %m%n

    log4j.appender.R=org.apache.log4j.DailyRollingFileAppender
    log4j.appender.R.File=D:\\Tomcat 5.5\\logs\\qc.log
    log4j.appender.R.layout=org.apache.log4j.PatternLayout
    1log4j.appender.R.layout.ConversionPattern=%d-[TS] %p %t %c - %m%n

    log4j.logger.com.neusoft=DEBUG
    log4j.logger.com.opensymphony.oscache=ERROR
    log4j.logger.net.sf.navigator=ERROR
    log4j.logger.org.apache.commons=ERROR
    log4j.logger.org.apache.struts=WARN
    log4j.logger.org.displaytag=ERROR
    log4j.logger.org.springframework=DEBUG
    log4j.logger.com.ibatis.db=WARN
    log4j.logger.org.apache.velocity=FATAL

    log4j.logger.com.canoo.webtest=WARN

    log4j.logger.org.hibernate.ps.PreparedStatementCache=WARN
    log4j.logger.org.hibernate=DEBUG
    log4j.logger.org.logicalcobwebs=WARN


![在src/main/java下新建GithubRepoProcessor.java](http://upload-images.jianshu.io/upload_images/2319568-0ea1cff7433a3486.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

插入实例代码。

    import us.codecraft.webmagic.Page;
    import us.codecraft.webmagic.Site;
    import us.codecraft.webmagic.Spider;
    import us.codecraft.webmagic.processor.PageProcessor;

    public class GithubRepoPageProcessor implements PageProcessor {

        private Site site = Site.me().setRetryTimes(3).setSleepTime(100);

        public void process(Page page) {
            page.addTargetRequests(page.getHtml().links().regex("(https://github\\.com/\\w+/\\w+)").all());
            page.putField("author", page.getUrl().regex("https://github\\.com/(\\w+)/.*").toString());
            page.putField("name", page.getHtml().xpath("//h1[@class='entry-title public']/strong/a/text()").toString());
            if (page.getResultItems().get("name")==null){
                //skip this page
                page.setSkip(true);
            }
            page.putField("readme", page.getHtml().xpath("//div[@id='readme']/tidyText()"));
        }

        public Site getSite() {
            return site;
        }

        public static void main(String[] args) {
            Spider.create(new GithubRepoPageProcessor())
                    .addUrl("https://github.com/code4craft")
                    .thread(5)
                    .run();
        }
    }

此时还需要配置最后一处。

![下拉列表选择Edit Configurations...](http://upload-images.jianshu.io/upload_images/2319568-fe4440caefac865a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![按照图中参数配置](http://upload-images.jianshu.io/upload_images/2319568-37edac2e7cc80c4f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![点击运行即可运行你的第一个爬虫](http://upload-images.jianshu.io/upload_images/2319568-f3db78df1d334458.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

下一篇文章中，我们将利用WebMagic框架来爬取CSDN博客，作为demo进行讲解。