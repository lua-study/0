Jw-alipay （捷微支付窗平台）开源免费支付窗管理平台
==========
特点：捷微支付服务窗管理平台，开源免费，实现了支付窗管家基本功能：账号、菜单、文本素材，图文素材，粉丝管理、账号绑定，关键字触发，群发等功能。便于二次开发，采用jeecg-p3微服务框架技术。 

===============
当前最新版本：1.0.0（发布日期：20161117）


【项目说明】

	jeecg-p3-web               | 启动项目
	jeecg-p3-biz-alipay-single | 支付窗平台插件项目

	
【平台指南】

* 体验账号（手机支付宝扫一扫关注）

![github](http://img.blog.csdn.net/20161122135138088?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQv/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center "jeecg")
* [开发指南](http://blog.csdn.net/zhangdaiscott/article/details/53156710)
* 在线演示：[http://www.jeewx.com/jeewx/](http://www.jeewx.com/jeewx/)
* Maven依赖下载慢解决方案 => [享受一下mvn时飞的感觉，配置阿里云maven镜像](http://www.jeecg.org/forum.php?mod=viewthread&tid=3949)


【平台基础功能】

*   1，支付窗账号管理
*   2，关键字管理
*   3，素材管理：文本素材
*   4，素材管理：图文素材
*   5，关注回复
*   6，菜单管理
*   7，用户管理
*   8，用户消息


【搭建开发环境】

	☆快捷启动方式：
		第一步：创建Mysql数据库jw-alipay，采用UTF-8编码，执行数据库脚本
		第二步：双击运行bin\run-tomcat7.bat，
				启动Web服务器（第一次运行，需要下载依赖jar包，请耐心等待）。
		第三步：项目访问地址
				http://localhost/jeecg-p3-web
				
	☆开发准备：
		1.标准开发工具：eclipse + jdk7 + tomcat7 + mysql
		2.项目为maven工程，采用maven方式导入eclipse等IDE开发工具		
    ☆Eclipse运行方式：
		第一步：创建Mysql数据库jw-alipay，采用UTF-8编码，执行对应数据库脚本
		第二步：采用maven方式启动项目 (jeecg-p3-web)
				项目右建->debug as->debug configurations->选中jeecg-p3-web项目->输入命令：tomcat:run
				注意：[1].update snapshots需要选中，官方会不断更新底层包
					  [2].插件项目不能单独启动，需以maven方式引入jeecg-p3-web项目中，启动web主项目
		第四步：项目访问地址
				http://localhost/jeecg-p3-web

	    便捷工具：
		     本地Ｍaven仓库下载：链接: https://pan.baidu.com/s/1skZ8OUT 密码: itwq
	
技术交流
==========
* QQ交流群: 495450056
* 技术论坛：[www.jeecg.org](http://www.jeecg.org)


系统截图
==========
![github](http://dl2.iteye.com/upload/attachment/0121/3234/e4decd42-190b-3fc1-8f6a-ca15e07d052e.png "jeecg")
![github](http://dl2.iteye.com/upload/attachment/0121/3232/2c78cdaf-5b4d-30e6-b879-8881e59a5520.png "jeecg")

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)