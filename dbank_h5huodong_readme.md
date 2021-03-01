捷微H5 | 开源免费微信活动平台
==========
特点：采用微服务架构，插件式开发、专业微信营销活动平台，具备大用户、高并发支撑能力


官方公众号（体验活动）
==========
![github](http://www.jeecg.org/data/attachment/forum/201601/25/180314mjvputsot6hhtvoa.jpg "jeewx521")



### 捷微 - H5活动源码列表（陆续更新..）
	  1.微信公众号管理   P3-Biz-commonweixin
	  2.摇一摇送卡券     P3-Biz-shaketicket
	  3.九宫格活动       P3-Biz-jiugongge
	  4.启动项目         P3-Web
	  
	  
	  
【架构说明】

    1.采用SpringMvc + Mybatis + Velocity + Maven(构建) 框架技术
    2.插件引入方式
        pom.xml文件中，引入新开发的插件
         
 	     
			 org.h5huodong 
			 P3-Biz-jiugongge 
			 1.0.0 
			 jar 
		 
	3.项目启动访问方式：
	  采用maven方式，启动Web项目
      http://localhost:8080/jeewx
    4.页面层面不能采用jsp，需要采用模板语言Velocity
    5.实现插件式开发，按照模块进行开发，每个模块可以单独达成jar包
	6.数据库配置文件：
	  src/main/resources/db.properties
	  
	  
技术交流
==========
* 捷微H5官网：[www.h5huodong.com](http://www.h5huodong.com)
* 技术论坛 ：[www.jeecg.org](http://www.jeecg.org)
* 捷微技术QQ群 : 97460170
* 在线开发文档： [http://jeewx-h5.mydoc.io](http://jeewx-h5.mydoc.io)




【开发入门】

	1.Eclipse + Maven + JDK7
    2.项目以Maven方式导入eclipse
	3.初始化数据库脚步
	    P3-Web\doc\db\jeewx-h5-mysql-20180810.sql
	4.采用maven方式，启动主项目P3-Web，命令：tomcat:run
      活动访问地址：
	     http://localhost:8080/jeewx
	  说明：插件不能单独启动，maven方式引入到Web项目
	5.系统默认登录账号 admin/123456
	  
	
【代码生成器】

	1.工具类：P3-Web/src/main/java/org/jeecgframework/p3/cg/util/CodeToolUtil.java
	2.配置文件：P3-Web/src/main/resources/p3-cg-config.properties





### 砍价活动-效果图
![github](http://www.jeecg.org/data/attachment/forum/201601/25/180710anjfgtn677nojgg0.png "jeecg")
### 九宫格活动-效果图
![github](https://static.oschina.net/uploads/img/201808/13105211_lMFh.jpg "jeecg")
### 斧头帮砍价-效果图
![github](http://www.jeecg.org/data/attachment/forum/201601/25/180500iwpg1agqm778wggp.png "jeecg")
### 摇一摇送卡券-效果图
![github](https://static.oschina.net/uploads/img/201808/11195358_bi9e.png "jeecg")


### H5活动之家（管理后台）
![github](https://static.oschina.net/uploads/img/201808/13105211_M0FW.png "jeecg")
![github](https://static.oschina.net/uploads/img/201808/13105211_AVY4.png "jeecg")
![github](https://static.oschina.net/uploads/img/201808/11172049_s7hH.png "jeecg")
![github](https://static.oschina.net/uploads/img/201808/11153109_73Aj.png "jeecg")
![github](https://static.oschina.net/uploads/img/201808/11221430_KZ1b.png "jeecg")


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)