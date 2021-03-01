### [springmvc-hibernate](https://github.com/wangxinforme/springmvc-hibernate)
 它是一个典型的MVC三层框架示例工程，快速简单的上手。 

+ 介绍：
	+ 集成框架有：SpringMVC、Hibernate、Bootstrap3、Apache Shiro、Sitemesh3、memcached、solr、redis、log4j2；
	+ 集成示例有：用户登录、文件上传下载、文件压缩、JQuery联想搜索；
	+ 数据库支持：Oracle、MySQL、SQLite；  
	
+ 启动工程：
	+  web.xml 文件当中的 spring.profiles.default 可切换系统环境，选development是以开发环境启动，选production则是生产环境启动；
	+ 数据库选择，默认开启SQLite数据库，若改用Oracle或SQLite，可在工程的 config-datasource.properties 数据源配置文件当中设置，按启动的是开发环境还是生产环境来选择数据源配置文件；
	+ 若采用的是SQLite数据库，本步骤可跳过，初始化数据可查看 InitServiceTest 类中的Junit方法，注意下单元测试类当中 @ActiveProfiles("") ，请指定相应的环境；
	+ 如若启动 memcached、solr、redis ，修改 web.xml 文件当中spring配置文件加载项；
		+ 如果启用 Memcached ，打开 MemcachedFactory 类中的 @Resource(name = "memcachedClient") 注释
		+ 如果启用 Solr ，打开 BaseSolrRepositoryImpl 接口实现类中的 @Resource(name = "solrcloud_server") 注释
		+ 如果启用 Redis ，打开 RedisBaseService 抽象类中的 @Resource(name = "redisTemplate") 注释
	+ 启动工程；
	+ 浏览器访问工程查看示例效果；  


欢迎[交流讨论](https://github.com/wangxinforme/springmvc-hibernate/issues)

 [胡桃夹子GitHub](https://github.com/wangxinforme "Vincent Git@OSC主页") 



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)