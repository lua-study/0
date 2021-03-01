项目名为alexgaoyh  但是发布的时候，设定的context root 为web  即发布到容器中之后，使用的是web项目名
后台登陆为： http://localhost:8080/web/admin/login  如果导入项目包含的web.sql 文件的话，登录名密码为admin/admin

1: 发送邮件的功能，需要手动更改  spring-smtp-mail.xml 配置文件的username&&password两个参数，
	调用方法为直接调用EmailUtil.send(subject, content, to);
	
2: 本例数据库使用的是mysql5.5版本，并且在项目启动前，需要更改 db-config.properties 文件的数据库对应的ip,username,password


3: 使用ueditor,后期需要更改/WEB-INF/jsp/config.json 包含的*UrlPrefix部分，现在写死为项目名称    ***已经与2014/11/10修改此问题***

4: 20141124 增加ehcache缓存逻辑，1、配置相关实体；2、ehcache.xml增加对应配置；3、重写baseDaoImpl相关方法，增加.setCacheable(true)属性； 已验证
	
	1、默认情况下二级缓存只会对load get 之类的方法缓存， 想list iterator 之类的方法也使用缓存 必须跟查询缓存一起使用， 
		在BaseDaoImpl中重写方法，增加.setCacheable(true) 
		Eg:   criteria.setCacheable(true).list();         				criteria.setCacheable(true).setProjection(Projections.rowCount()).uniqueResult();
		
	2、实体关系中增加注解 @Cache(usage = CacheConcurrencyStrategy.READ_WRITE, region="newsTemplete")  
		ehcache.xml 文件中增加相关配置  注意名称要一致(newsTemplete);
		
	3、window下java.io.tmpdir/ehcache 路径对应 C:\Users\{当前用户}\AppData\Local\Temp\ehcache 可以打印输出进行验证.
	
5: 20141212 整合redis2.6 win32/64的redis服务端在附件位置，请先下载并运行进行配置。
	
	1、 com.alexgaoyh.redis.util.RedisClient 为客户端，注入RedisTemplate(redis-config.xml)
	2、 测试方法 在Action中引入 RedisClient对应的bean 直接调用相关方法即可。
		如下：
		
			@Controller
			@RequestMapping(value="test")
			public class TestAction {
			
				@Resource
				private RedisClient  redisClient;
				
				@RequestMapping(value="test")  
				public ModelAndView test(){
    				redisClient.add("aaaa", "aaaa");
    				System.out.println(redisClient.get("aaaa"));
        			return new ModelAndView("views/test");
				}
				
			}
			


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)