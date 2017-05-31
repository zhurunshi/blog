---
title: 从零开始学习基于WebMagic的Java爬虫（二）：爬取CSDN博客
categories: Java
date: 2017-04-24 09:43:27
tags:
---
声明：
本例中的源代码参考了：http://blog.csdn.net/qq598535550/article/details/51287630 ，并进行修改而成的。

由于案例就是爬取的CSDN博客，分析了一下各大博客网站，发现CSDN比较适合入门，所以我也选择CSDN作为开始，写我的第一个爬虫程序。

首先来介绍爬虫的核心爬取逻辑，即PageProcessor，我们每写一个爬虫，都必须编写一个针对待爬取网站的爬取逻辑，该类要实现PageProcessor接口。
<!--more-->

    import us.codecraft.webmagic.Page;
    import us.codecraft.webmagic.Site;
    import us.codecraft.webmagic.Spider;
    import us.codecraft.webmagic.pipeline.JsonFilePipeline;
    import us.codecraft.webmagic.processor.PageProcessor;

    import java.text.SimpleDateFormat;
    import java.util.Date;
    import java.util.List;
    import java.util.Scanner;

    /**
     * Created by Rush on 2017/3/27.
     */

    public class CsdnBlogPageProcessor implements PageProcessor {
        // 部分一：抓取网站的相关配置，包括编码、抓取间隔、重试次数等
        private Site site = Site.me().setRetryTimes(3).setSleepTime(1000)
                .setUserAgent(
                        "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_7_2) AppleWebKit/537.31 (KHTML, like Gecko) Chrome/26.0.1410.65 Safari/537.31");
    //            .setUserAgent("Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/31.0.1650.63 Safari/537.36");
        private static String username; // 设置的Csdn用户名
        private static int size = 0; // 共抓取到的文章数量

        // process是定制爬虫逻辑的核心接口，在这里编写抽取逻辑
        public void process(Page page) {
            // 部分二：定义如何抽取页面信息，并保存下来
            // 如果匹配成功，说明是文章页
            if(!page.getUrl().regex("http://blog\\.csdn\\.net/" + username + "/article/details/\\d+").match()){
                // 添加所有文章页
                page.addTargetRequests(page.getHtml().xpath("//div[@id='article_list']").links()
                        .regex("/" + username + "/article/details/\\d+")
                        .replace("/" + username + "/", "http://blog.csdn.net/" + username + "/")
                        .all());
                // 添加其他列表页
                page.addTargetRequests(page.getHtml().xpath("//div[@id='papelist']").links() // 限定其他列表页获取区域
                        .regex("/" + username + "/article/list/\\d+")
                        .replace("/" + username + "/", "http://blog.csdn.net/" + username + "/")// 巧用替换给把相对url转换成绝对url
                        .all());
            } else {
                ++size;

                page.putField("numbers", page.getUrl().regex("\\d+$").get());
                page.putField("authors", username);
                page.putField("titles", page.getHtml()
                                .xpath("//div[@class='article_title']//h1//span[@class='link_title']/a/text()").get());
                page.putField("dates", page.getHtml()
                                .xpath("//div[@class='article_r']//span[@class='link_postdate']/text()").get());
                page.putField("tags", listToString(page.getHtml()
                        .xpath("//div[@class='article_l']//span[@class='link_categories']/a/text()").all()));
                page.putField("categorys", listToString(page.getHtml()
                                .xpath("//div[@class='category_r']//label//span//text()").all()));
                page.putField("views", page.getHtml()
                                .xpath("//div[@class='article_r']//span[@class='link_view']").regex("\\d+").get());
                page.putField("comments", page.getHtml()
                                .xpath("//div[@class='article_r']//span[@class='link_comments']//text()").regex("\\d+").get());
                page.putField("copyright", page.getHtml().regex("bog_copyright").match() ? 1 : 0);
                SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
                page.putField("dateCreated", sdf.format(new Date()));

                /* 如果想要存储到数据库中，打开此代码段，并将上面的代码段注释掉。
                CsdnBlog csdnBlog = new CsdnBlog(
                        // 文章随机编号
                        Integer.valueOf(page.getUrl()
                                .regex("\\d+$").get()),
                        // 文章作者
                        username,
                        // 文章标题
                        page.getHtml()
                                .xpath("//div[@class='article_title']//h1//span[@class='link_title']/a/text()").get(),
                        // 文章日期
                        page.getHtml()
                                .xpath("//div[@class='article_r']//span[@class='link_postdate']/text()").get(),
                        // 文章标签
                        listToString(page.getHtml()
                                .xpath("//div[@class='article_l']//span[@class='link_categories']/a/text()").all()),
                        // 文章类别
                        listToString(page.getHtml()
                                .xpath("//div[@class='category_r']//label//span//text()").all()),
                        // 阅读人数
                        Integer.valueOf(page.getHtml()
                                .xpath("//div[@class='article_r']//span[@class='link_view']").regex("\\d+").get()),
                        // 评论人数
                        Integer.valueOf(page.getHtml()
                                .xpath("//div[@class='article_r']//span[@class='link_comments']//text()").regex("\\d+").get()),
                        // 是否原创
                        page.getHtml().regex("bog_copyright").match() ? 1 : 0
                );
                new CsdnBlogDao().add(csdnBlog);
                System.out.println(csdnBlog);
                */
            }
        }

        public Site getSite() {
            return site;
        }

        private static String listToString(List<String> stringList){
            if(stringList == null){
                return null;
            }
            StringBuffer result = new StringBuffer();
            boolean flag = false;
            for(String s : stringList){
                if(flag){
                    result.append(',');
                } else {
                    flag = true;
                }
                result.append(s);
            }
            return result.toString();
        }

        public static void main(String[] args) {
            long startTime, endTime;
            System.out.print("请输入要爬取的CSDN博主用户名：");
            Scanner scanner = new Scanner(System.in);
            username = scanner.next();
            System.out.println("-----------启动爬虫程序-----------");
            startTime = System.currentTimeMillis();
            Spider.create(new CsdnBlogPageProcessor())
                .addUrl("http://blog.csdn.net/" + username)
                .addPipeline(new JsonFilePipeline("D:\\webmagic\\"))
                //开启5个线程抓取
                .thread(5)
                //启动爬虫
                .run();
            endTime = System.currentTimeMillis();
            System.out.println("结束爬虫程序，共抓取 " + size + " 篇文章，耗时约 " + ((endTime - startTime) / 1000) + " 秒！");
        }
    }

简单说明下程序：

首先输入想要爬取的CSDN博主用户名，然后回车即可开始爬取数据，爬取完成的数据将存在D:\webmagic目录中，当然，你可以修改这个地址。

爬取获得的数据将以JSON格式存储在文件夹内。

**如果你想将爬取的数据，保存到数据库内的话，可以将上面的注释打开，并且将原注释上方的代码段注释掉，然后加上下面的贴出来的代码，即可将数据保存到数据库中。**

main()函数是java程序的入口，我们从这里开始看，开头几句话不用多说。

Spider.create()函数可以定义爬虫的目标地址以及爬取的各种参数，进程等等。

create中的addPipeline()说明了保存数据的方法，这里我使用了最基本的JsonFilePipeline方法，将数据以JSON格式保存在本地文件里面，当然，你也可以自定义你的保存方法。

process()函数，可以看出来本例中大量使用了XPath来获取元素，想必有HTML基础的人应该可以看出来；并且还使用了正则表达式来匹配和抽取文本。其中使用page.addTargetRequests()来不断添加要抓取的网页到队列中。

举个例子：
我们可以看到标题(titles)元素的抽取，使用的xpath语句是：

    page.putField("titles", page.getHtml()
    .xpath("//div[@class='article_title']//h1//span[@class='link_title']/a/text()").get());

![](http://upload-images.jianshu.io/upload_images/2319568-226a7eb9671bfc1d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
可以看到标题的文字是在class名为article_title的div内，紧接着后面的路径还有h1>span(class名为link_title)>a，然后a里面的文字就是文章的题目，所以可以使用形如上面的代码来表示这一部分内容，紧接着用get()函数取出文字。

除了get()函数，WebMagic还提供了all()函数，可以获得与xpath匹配出路径相同的所有元素的list，返回一个String列表。

另外你还可以使用regex()函数跟在xpath后面， 将抽取出来的数据进行进一步处理，从而产生出需要的数据。

如果想获取更多更详细的方法介绍，请参见http://webmagic.io/

通过以上两种手段，就已经可以写出简单的爬取CSDN博客的爬虫。

如果想将数据保存到数据库，还需要后面两段代码。


    import java.sql.*;

    /**
     * Created by Rush on 2017/3/27.
     */
    public class CsdnBlogDao {
        private Connection conn = null;
        private Statement stmt = null;

        public CsdnBlogDao(){
            try{
                Class.forName("com.mysql.jdbc.Driver");
                String url = "jdbc:mysql://localhost:3306/spider";
                String username = "root";
                String password = "rush";
                conn = DriverManager.getConnection(url, username, password);
                stmt = conn.createStatement();
            } catch (ClassNotFoundException e){
                e.printStackTrace();
            } catch (SQLException e){
                System.out.println("数据库连接失败！");
                e.printStackTrace();
            }
        }

        public int add(CsdnBlog csdnBlog){
            try{
                String sql = "insert into spider.csdnblog(" +
                        "numbers, authors, titles, dates, tags, categorys, " +
                        "views, comments, copyright, date_created) " +
                        "values(" + csdnBlog.getNumbers() +
                        ", '" + csdnBlog.getAuthors() +
                        "', '" + csdnBlog.getTitles() +
                        "', '" + csdnBlog.getDates() +
                        "', '" + csdnBlog.getTags() +
                        "', '" + csdnBlog.getCategorys() +
                        "', " + csdnBlog.getViews() +
                        ", " + csdnBlog.getComments() +
                        ", " + csdnBlog.getCopyright() +
                        ", sysdate())";
                System.out.println(sql);
                PreparedStatement ps = conn.prepareStatement(sql);
                int rows = stmt.executeUpdate(sql);
            } catch (SQLException e){
                System.out.println("插入数据失败！");
                e.printStackTrace();
            }
            return -1;
        }
    }


    import java.util.Date;

    /**
     * Created by Rush on 2017/3/27.
     */
    public class CsdnBlog {

        private int id;

        private int numbers; // 编号

        private String authors; // 作者

        private String titles; // 标题

        private String dates; // 文章日期

        private String tags; // 标签

        private String categorys; // 分类

        private int views; // 阅读人数

        private int comments; // 评论人数

        private int copyright; // 是否原创

        private Date dateCreated; // 爬取时间

        public CsdnBlog() {}

        public CsdnBlog(int numbers, String authors, String titles, String dates, String tags, String categorys, int views, int comments, int copyright) {
            this.numbers = numbers;
            this.authors = authors;
            this.titles = titles;
            this.dates = dates;
            this.tags = tags;
            this.categorys = categorys;
            this.views = views;
            this.comments = comments;
            this.copyright = copyright;
        }

        public int getNumbers() {
            return numbers;
        }

        public void setNumbers(int numbers) {
            this.numbers = numbers;
        }

        public String getAuthors() {
            return authors;
        }

        public void setAuthors(String authors) {
            this.authors = authors;
        }

        public String getTitles() {
            return titles;
        }

        public void setTitles(String titles) {
            this.titles = titles;
        }

        public String getDates() {
            return dates;
        }

        public void setDates(String date) {
            this.dates = dates;
        }

        public String getTags() {
            return tags;
        }

        public void setTags(String tags) {
            this.tags = tags;
        }

        public String getCategorys() {
            return categorys;
        }

        public void setCategorys(String categorys) {
            this.categorys = categorys;
        }

        public int getViews() {
            return views;
        }

        public void setViews(int views) {
            this.views = views;
        }

        public int getComments() {
            return comments;
        }

        public void setComments(int comments) {
            this.comments = comments;
        }

        public int getCopyright() {
            return copyright;
        }

        public void setCopyright(int copyright) {
            this.copyright = copyright;
        }

        public Date getDateCreated() {
            return dateCreated;
        }

        public void setDateCreated(Date dateCreated) {
            this.dateCreated = dateCreated;
        }

        @Override
        public String toString() {
            return "CsdnBlog{" +
                    "numbers=" + numbers +
                    ", authors='" + authors + '\'' +
                    ", titles='" + titles + '\'' +
                    ", dates='" + dates + '\'' +
                    ", tags='" + tags + '\'' +
                    ", categorys='" + categorys + '\'' +
                    ", views=" + views +
                    ", comments=" + comments +
                    ", copyright=" + copyright +
                    '}';
        }
    }


**如果你想知道爬到这些数据有什么用呢？**

**好吧，我也不知道他们有什么用。**

**不过可以肯定的一点是：**

**你已经完成了自己的第一个爬虫程序了，不是吗？**