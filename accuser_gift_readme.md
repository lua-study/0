
### gift 是  giftmail项目的模块化更细致的划分.

######################此项目是基于Maven+Jetty启动,在每次用jetty启动之前,使用Maven clean,Maven install编译#################

技术栈:

一.spring + springmvc     4.1.1

    二.mybatis                3.2.8

        三.spring + redis         2.7.1

            四.quartz                 2.2.1

                五.druid                  1.0.9

                    六.logback                1.2.3

                        七.freemarker             2.3.23

                            八.maven + nexus

                                九.系统拦截器

                                    十.面向切面的对session的保存入库

                                        十一.分页拦截器

                                            十二.Excel                 org.wuwz.ExcelKit 1.1(开源贡献者)

                                                十三.微信支付-java端获取预支付ID 
                                                
                                                    十四.将原来一个Maven项目,拆分成按照模块多个Maven项目来管理
                                                        
                                                        十五.增加了spring对ActiveMQ的基础管理

13.截止到2017.9.13日将原来的项目 http://git.oschina.net/accuser/giftmail 拆分成多个模块,分别由giftmail-parent,giftmail-common,giftmail-dao,giftmail-service,giftmail-web组成.

	 

		 giftmail-common 

		 giftmail-dao 

		 giftmail-service 

		 giftmail-web 

	 

14.在giftmail-web的pom.xml中,增加了jetty插件.

    Base directory : ${workspace_loc:/giftmail-web}

    Goals          : jetty:run

附带一篇Maven工程模块化划分方法:

  1.Maven的父工程的packaging类型需要使用pom,所以,在先创建新的maven project,选择"Create a simple project".

  2.填写GAV,G:cn.giftmail A:giftmail-parent V:0.0.1-SNAPSHOT ,选择packaging为pom,此时生成的pom.xml文件应该是这样的:

 

	 4.0.0 

	 cn.giftmail 

	 giftmail-parent 

	 0.0.1-SNAPSHOT 

	 pom 

	 

		 giftmail-common 

		 giftmail-dao 

		 giftmail-service 

		 giftmail-web 

	 

         

		 giftmail-web 

		 

			 

				 maven-compiler-plugin 

				 3.0 

				 

					 1.7 

					 1.7 

					 UTF-8 

				 

			 

			 

				 org.apache.tomcat.maven 

				 tomcat7-maven-plugin 

				 2.1 

			 

		 

	 

 

    3.创建各个子模块,各模块之间通过webservice通信.简单创建common,dao,service,web模块.除了web模块的packaging类型是war,其他的都是jar,前三个创建的时候选择"quickstart",后一个创建的时候选择"webapp".

    4.鼠标右键父工程,使用"maven module",各pom.xml文件见项目详情.

    5.maven依赖的jar,我暂时都放在了giftmail-parent的pom.xml中,这样好处在于在依赖关系上不会出现循环依赖的问题.

    6.giftmail-common模块是一些基础类库 + 工具类 + 并且不涉及到业务的类 eg:系统日志监控,Excel导出,微信支付,session拦截,分页拦截器,自定义任务quartz等,在common模块中,也符合MVC模型,但与业务模块相对是独立的.

    7.业务模块的MVC模型,分别位于dao,service,web中(不再赘述原因),但将model层放在了common模块中的原因是:有部分公共类也会对model对象进行依赖,由于dao依赖common,service依赖dao,web依赖service,进而将model层放在common中,即可使dao,service,web都可以依赖到model层.

15.截止到2017.9.21日增加了spring对ActiveMQ的基础管理(生产者发送的消息是String文本类型的message)

增加spring对MQ的消息监听有三种,此配置SessionAwareMessageListener监听器(在原来MessageListener基础之上扩展了消息通知对方已经收到此消息的功能)

增加spring对MQ的消息监听有三种,此配置MessageListenerAdapter监听器(在原来MessageListener和SessionAwareMessageListener基础之上扩展了将接收到的消息进行类型转换，然后通过反射的形式把它交给一个普通的Java类进行处理)

修改了spring对MQ的MessageListenerAdapter消息监听,增加了在消息监听器中对回应ResponseQueueListener类,配置了返回的消息的目的地.

既可以将消息进行事务管理,也可以将消息事务和数据库事务,联合在一起做事务绑定.(本部分未提供代码,参考收藏的内容)



  



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)