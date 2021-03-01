
#### webpasser是一款可配置的开源爬虫框架，提供爬虫控制台管理界面，通过配置解析各类网页内容，无需写一句java代码即可抽取所需数据。

1. 包含强大的页面解析引擎，提供jsoup、xpath、正则表达式等处理链，通过简单配置即可抽取所需的指定内容。
2. 提供爬虫控制管理界面，可实时监控抓取状态，动态添加抓取任务，动态配置定时任务，可对单个网页进行测试抓取。
3. 提供抓取各阶段的触发器、拦截器，方便扩展。
4. 支持多线程，失败重试，代理等


#### 项目结构

* **webpasser.common**    包含项目的一些工具类
* **webpasser.core**  项目核心包，包含爬虫任务整个流程模块、页面解析引擎、配置规则引擎、定时器等，可以直接引用此包进行爬虫任务抓取。
* **webpasser.project**  用于项目自定义业务扩展，如解析后数据持久化类，触发器实现类等。
* **webpasser.web**    爬虫管理控制台，包含爬虫监控、添加任务、配置定时任务、单个网页抓取测试的界面。


#### 使用:

将根目录中已编译好的webpasser.war放到tomcat容器部署启动，访问项目页面；或将代码以maven形式导入eclipse，编译启动。当然，也可以直接只依赖webpasser.core包完成爬虫任务。


#### 控制台方式添加一个爬虫任务:

1. 查看目标网站的页面特征，在xml中配置所需抓取内容。
2. 在控制台添加一个抓取任务，将xml配置提交。
3. 对单个网页测试或整个任务执行测试。
4. 在webpasser.project中扩展数据持久化类或使用现有持久化类存储数据
5. 设置定时任务。


#### 只依赖webpasser.core包方式完成一个爬虫任务:

1. 用maven依赖webpasser.core包
```
	 
		 com.hxt.webpasser 
		 webpasser.core 
		 0.0.1-SNAPSHOT 
	 
```
2. 查看目标网站的页面特征，在xml中配置所需抓取内容。
3. 写启动代码:
```
	SpiderTask spiderTask=new SpiderTask("testTask","catch/testtask.xml");
	
	spiderTask.start();
```




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)