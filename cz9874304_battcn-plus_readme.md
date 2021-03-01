## battcn-plus(2.5.1) 如果您喜欢它,请点击 Watch  以及 Star Thanking Very Much##

	前端：采用了BootStrap3.3.5 + BootStrap Table + jQuery2.1
	后端：SpringBoot1.5.3 增加PageHelper与通用Mapper方便开发
	通用Mapper：Mybatis单表操作基于注解调用API,方便我们开发,提高开发效率
	权限：采用Spring Shiro做的登陆认证与URL拦截
	本系统秉承开源精神,欢迎大家使用与开发,遇到任何问题可以 申请QQ群：391619659 找到 解答
	该版本为battcn.x的终极版本,只做干净的项目,剔除了battcn2.x的redis模块 以及一些plugin模块,学习该套代码需要掌握boot基本知识 
	简化开发： battcn-generator 提供mybatis-generate代码,生成DAO,POJO(含注释),XML(无具体内容,减少代码),Maven命令：mybatis-generator:generate
	封装mybatis（参考battcn-framework-mybatis）只需要通过简单的配置（application.yml）即可使用自动装配
	启动（battcn-managent）成功访问：
		http://localhost:8082		即可跳转到login.html
		http://localhost:8082/swagger-ui.html		即可跳转到swagger-ui.html,方便接口调试（需要先登录）
		
	
	
[下载静态资源：http://oe8uway3x.bkt.clouddn.com/static.zip](http://oe8uway3x.bkt.clouddn.com/static.zip "下载静态资源：http://oe8uway3x.bkt.clouddn.com/static.zip")

[群官网：http://www.battcn.com](http://www.battcn.com "群官网：http://www.battcn.com")

[演示地址：http://demo.battcn.com](http://demo.battcn.com "演示地址：http://demo.battcn.com")	

完成所有功能，包括权限


# 注意

**如果喜欢它 请认真阅读 README 文件,以及 resources 下的 `doc文档`**

battcn-generator 只是代码生成,并不被具体依赖

打包的时候 install（battcn-framework-commons/battcn-framework-mybatis） 然后 package battcn-managent即可



一.服务人群
------

	A) 初创型公司技术团队
	B) 外包公司技术团队
	C) 独行侠
	D) 学生

二.项目事项
------
	A) 我们只做通用的服务组件,比如基本的(权限管理,用户管理,菜单管理,调度管理等)	
	B) 让用户可以快速根据框架开发并且也可以修改我们的源码从而达到用户的业务要求。
		用户通过本项目可以快速的搭建出自己的开发平台，并且可以让用户减轻考虑基础功能的时间，
		留出时间着重自己的业务开发就是本项目的最终目标。
	C) 项目部署：里面写了一个小的存储过程,所以 需要手动在 数据库执行  battcn2.sql 里面已经注释掉了 ,因为有一个"初始化系统"的功能

三.开发流程
------

	定义实体类Entity(如：UserEntity)
	创建 Mppaer  (如：UserMapper )	如果有自定义SQL操作则需要定义mapper.xml
	定义 Service 接口(如：UserService)（根据Java规范所以接口化编程：可省）
	实现 Service (如：UserServiceImpl)
	创建 Controller 控制器(如：UserController)
	
	1.具体不清楚可以申请加群：391619659
	2.本系统为开源系统可以随意修改
	3.欢迎大家使用,本系统不会记录任何使用者的信息,可以放心使用,有Bug可以提交作者(QQ:1837307557)
	4.如果喜欢可以赞助作者,您的支持就是作者最大的动力

				

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)