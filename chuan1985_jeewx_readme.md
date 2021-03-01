捷微H5 | 免费微信活动平台
==========
捷微H5，是一款开源免费的微信运营平台，是jeewx的新一代产品，平台涵盖了：微信公众号管理、各种微信活动、小程序、微网站、微商城、分销商城、小程序商城、小程序网站、砍价、投票、会员等等功能，是一套成熟的互联网运营产品。架构层面，采用JAVA语言，具备更高的并发能力和大数据能力，采用微服务架构，插件式开发模块化、UI体验更好；另外强大的代码生成器，显著提高开发效率，便于用户二次开发；最大的优势： 插件模式，每个功能模块以插件方式提供，方便插拔集成，个性化定制。

当前最新版本： 4.1.0（发布日期：20181112）

老版本下载：[Jeewx3.0老版本下载](https://github.com/zhangdaiscott/jeewx)

架构演变：

	  JEEWX 从4.0版本开始，技术架构全新换代，采用微服务架构插件式开发，每个业务模块都是独立的JAR包，
	  方便用户集成，可插拔的模式。框架技术：SpringMvc + Mybatis + Velocity + Bootstrap + Maven
	  老版本JEEWX是基于jeecg开发，如果你更喜欢老版，请在这里下载：https://github.com/zhangdaiscott/jeewx
	  
	  
	  
### 公众号体验（小程序）

![github](http://www.jeecg.org/data/attachment/forum/201601/25/180314mjvputsot6hhtvoa.jpg "jeewx521")
![github](https://static.oschina.net/uploads/img/201810/15180859_25Ok.jpg "jeewx521")
	  
	  
### 一、平台功能

【微信公众号】
*   1、微信公众号管理
*   2、微信自定义菜单
*   3、关注欢迎语
*   4、未识别回复语
*   5、关键字管理
*   6、菜单支持小程序链接
*   7、文本素材管理
*   8、图文素材管理
*   9、强大图文编辑器
*   10、粉丝管理
*   11、同步粉丝功能
*   12、粉丝打标签功能
*   13、微信消息管理
*   14、接受微信消息
*   15、Oauth2.0链接
*   16、微信第三方平台（全网发布）

【系统管理】
*   1、系统用户管理
*   2、系统角色管理
*   3、系统菜单管理
*   4、项目管理（活动插件）
	
【微信活动】
*   1、九宫格
*   2、摇一摇
*   3、微信砍价



### 二、项目说明
	  1.微信公众号管理   P3-Biz-commonweixin
	  2.摇一摇活动       P3-Biz-shaketicket
	  3.九宫格活动       P3-Biz-jiugongge
	  4.新年砍价         P3-Biz-gzbargain
	  5.启动项目         P3-Web
	  
	  
### 三、小程序源码下载
	  1.小程序商城地址:    https://gitee.com/jeecg/weixin-app-cms
	  2.小程序官网地址:    https://gitee.com/jeecg/weixin-app-shop

	  	  
	  
### 四、架构说明

    1.采用SpringMvc + Mybatis + Velocity + Maven(构建) 框架技术
    2.插件引入方式
        pom.xml文件中，引入新开发的插件
         
 	     
			 org.h5huodong 
			 P3-Biz-jiugongge 
			 1.0.0 
			 jar 
		 
	3.项目启动访问方式：
	  采用maven方式，启动Web项目
      http://localhost/jeewx
    4.页面采用模板语言Velocity,不允许用jsp
    5.插件式开发，每个模块独立打成jar
	6.数据库配置文件：
	  P3-Web/src/main/resources/db.properties
	7.redis配置文件
	  P3-Web/src/main/resources/redis.properties
	 

  
### 五、技术交流

* 在线体验：[http://www.h5huodong.com/system/login.do](http://www.h5huodong.com/system/login.do)
* 技术论坛 ：[www.jeecg.org](http://www.jeecg.org)
* 技术QQ群 : 97460170
* 视频教程 : [https://pan.baidu.com/s/1gYDNvRWkritKb6sOMOx4hg](https://pan.baidu.com/s/1gYDNvRWkritKb6sOMOx4hg) (提取码：wq8d)




### 六、快速入门

【开发入门】

	1.Eclipse + Maven + JDK7
    2.项目以Maven方式导入eclipse
	3.初始化数据库脚步
	    P3-Web\doc\db\jeewx-h5-mysql-20181028.sql
	4.采用maven方式，启动主项目P3-Web，命令：tomcat:run
      活动访问地址：
	     http://localhost/jeewx
	  说明：插件不能单独启动，maven方式引入到Web项目
	5.系统默认登录账号 admin/123456
	  
	
【代码生成器】

	1.代码生成器工具类：P3-Web/src/main/java/org/jeecgframework/p3/cg/util/CodeToolUtil.java
	2.代码生成配置文件：P3-Web/src/main/resources/p3-cg-config.properties




### 捷微H5活动平台（管理后台）
![github](https://static.oschina.net/uploads/img/201808/13105211_M0FW.png "jeecg")
![github](https://static.oschina.net/uploads/img/201808/13105211_AVY4.png "jeecg")
![github](https://static.oschina.net/uploads/img/201808/11172049_s7hH.png "jeecg")
![github](https://static.oschina.net/uploads/img/201808/11153109_73Aj.png "jeecg")
![github](https://static.oschina.net/uploads/img/201808/11221430_KZ1b.png "jeecg")

### 捷微H5活动平台（H5微信活动）
1.砍价活动-效果图

![github](http://www.jeecg.org/data/attachment/forum/201601/25/180710anjfgtn677nojgg0.png "jeecg")

2.九宫格活动-效果图

![github](https://static.oschina.net/uploads/img/201808/13105211_lMFh.jpg "jeecg")

3.斧头帮砍价-效果图

![github](http://www.jeecg.org/data/attachment/forum/201601/25/180500iwpg1agqm778wggp.png "jeecg")

4.摇一摇送卡券-效果图

![github](https://static.oschina.net/uploads/img/201808/11195358_bi9e.png "jeecg")

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)