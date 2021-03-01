#Crwaler V1.0.3

增加正则表达式爬取工具

```
-cr URL -rule "[rule 正则表达式]" 最好带个冒号括起来 {other data} 可以选择性加 -input 输入结果到文件中
```
![爬取贴吧email](http://git.oschina.net/uploads/images/2016/0405/141744_195178e0_383838.png "demo 爬取贴吧email")

-------------------------------code------------------- 2016.04.01
#Crwaler V1.0.2

修复 -cl 命令 增加自动去重功能

-cl URL -cq div[class=XX]

-cl URL -cq div[class=xx] -file   将URL按行保存在某一个地方

```
-cq 可以是   传a就行 -cq a  
```

```
如果是     ...  ...n   -cq div[class=xss]即可取出所有url并去重
```

----------------------code--------------------------- 2016.3.28
#Crawler v1.0.1 升级版本

**Other data **
- {-header User-Agent@Android} 
- {-cookie CookieValue}
- {-data user=x&pass=x}
- {proxy IP:PORT}
- {-timesec time}
- {-post}

Command：

   -v   Manipulator Crawler Version

   -h   Manipulator Crawler UseINFO FAQ

   -u   [url] {other data}

   -cw  [url] -cq k,v@k,v k=title v=div[class=XXX] {other data}

   -ci  -file   -input   -cq k,v@k,v... {other data}

1、增加头伪造 -header 可以伪造浏览器或者其他认证信息

2、增加Cookik登录爬取 -cookie 模拟登录爬取

3、增加POST\GET带参数提交  -data user=XX?pass=xx 

4、增加代理IP功能  proxy ip:port 128.0.0.1:3389

5、增加延时爬取功能 -timesec 1000 = 1s

E.g>:C:\Users\ssHss\Desktop\ImageTemp>java -jar 1.jar -ci -file url.txt -cq title,h1[
id=artibodyTitle]#date,span[id=pub_date]#nodes,div[id=artibody] -input dataxsxs.
xml

和第一个版本不一样，一定要写好参数

----------------------code--------------------------- 2016.3.25

#Crawler V1.0.0
1. 代码还没有优化
2. 框架结构很简单
3. 部分功能需要你们给我需求，我后期添加测试

操作指南
------------

```
命令：java -jar Crawler.jar -[option]
```

```
    -v  爬虫的版本信息
```

```
    -h  爬虫的帮助文档
```

```
    -ct [url]  爬虫爬取一个网站测试 URL:测试的URL地址
```

```
    -cw [url] [k,v] 测试信息抽取 | URL:测试的URL | [k,v] title,div[class=title] 如果有多个参数,使用#隔开 
```

```
    -ci [urllist] [k,v]   把抽取的信息规则保存xml中,可以使用SQL工具的导入向导导入到数据库或者转成其他格式|   保存结
果目录
```

```
    -cl [url] [k,v]   把某URL的列表URL保存到文件中,可以用ci进行深入爬取
```

---------------


E.g 例子
---------------
1、-ci  URL文件 爬虫规则 输出路径

![URL文件](http://git.oschina.net/uploads/images/2016/0322/172027_907f276a_383838.png "URL文件路径")

2、执行java -jar crawler.jar -ci url.txt title,h1[id=artibodyTitle]#date,span[id=pub_date]#nodes,div[id=artibody] data.xml

![执行结果](http://git.oschina.net/uploads/images/2016/0322/172615_e539eaff_383838.png "执行结果")

然后我们可以使用SQL导入向导，用xml导入的方式,然后又可以转换为XML、TXT、EXCEL、WORD等多种格式。Navicat工具等

3、-cl命令就是用来生成urllist.txt 然后执行ci命令即可

我的邮箱344892053@qq.com BUG直接ISS或者邮件,你把你的需求告诉我,我来完善,我自己手头有一堆还没完善。

已经完成的:

1、URL格式化,部分网站的URL以"/" "./" "../" "//" 这些已经解决了

2、HTTP代理接口,有了 还没有加

3、自定义UA和Cookie登录 也有了，没有加

4、JDBC之前有,感觉没有xml导入的快，是个累赘 删除了

5、预留了个性化工具,批量提取EMail、QQ、手机号等

6、给SQLMAP做了接口,可在后期实现自动化注入测试和XSS测试

7、可以给Nutch结合上

8、还有问题给我提，我记记，然后慢慢完善。代码是开源 JavaGUI你懂

PS：使用者必须要有Java运行时环境

--------

现在的功能可与Shell DOS命令结合：定时爬虫、分布式爬虫，可以自由组合

QQ群：549067011

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)