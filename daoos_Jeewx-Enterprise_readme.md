JEEWX微信企业号管家
===============
捷微（微信企业号）是一款针对微信企业号的JAVA开发平台.
===============
当前最新版本： 1.1（发布日期：20160720）

平台介绍：

一、JEEWX微信企业号管家
-----------------------------------
JEEWX微信企业号管家是一个开源、高效、敏捷的微信企业号开发平台，采用JAVA语言基于Jeecg快速开发框架实现，实现了微信平台的基础功能，便于用户二次开发，支持插件开发机制。

主要特性
-----------------------------------
* 	1、基于快速开发平台jeecg 3.6.3版本，采用Maven+SpringMVC+Hibernate4+Easyui+Jquery+Ehcache等主流架构技术
* 	2、JEEWX插件框架技术，采用Maven+SpringMVC+Minidao+Velicity+Jquery等主流技术
*   3、支持企业快速开发，完善的用户组织机构，报表，强大的代码生成器快速有效的提高开发效率
*   4、开源免费，jeewx遵循Apache2开源协议(Jeewx提供开源版和商业版，开源版可以免费使用，可商业，无授权问题)
*   5、支持多用户多公众号管理
*   6、详细的二次开发文档，并不断更新增加相关开发案例提供学习参考
*   7、微信功能插件化开发，更易于定制和二次开发
*   8、支持author2.0机制

JEEWX企业号平台功能
-----------------------------------
*   1，微信企业号管理
*   2，微信应用管理
*   3，素材管理：文本素材
*   4，素材管理：图文素材
*   5，菜单管理
*   6，通讯录管理
*   7，用户管理
*   8，关键字管理
*   9，关注回复管理
*   10，微网站
*   11，系统用户角色管理
*   12，系统监控布
    
【项目说明】

	jeecg-framework            | 启动主项目（maven工程）
	jeecg-p3-biz-qywx          | 微信企业号插件（不能单独启动，pom方式引入主工程）

【标准开发环境】

    Eclipse + maven+ jdk7 + tomcat6 + mysql_5.0.37 

【开发入门】

    第一步：采用Mysql手工创建数据库jeewx-qiye 采用UTF-8编码
    第二步：执行jeewx数据初始化SQL脚本
              脚本位置：db\jeewx-qiye-mysql-20160424.sql
    第三步：采用eclipse导入maven项目，启动项目
    第四步：默认项目访问入口
             http://localhost/qywx
            输入验证码，默认账号admin/123456进行登录，进入捷微管家后台。
            说明：端口号，根据自己的配置，进行修改
	第五步：服务器部署，domain修改
	        src/main/resources/qywxconfig.properties
			修改参数：ftp_img_domain={真实项目访问地址} 例如：http://www.jeewx.com/jeewx
	特别提醒： JEEWX企业号插件依赖JEECG，更多资料参考：http://www.jeecg.org
	
技术文档
-----------------------------------
* JEEWX微信企业号平台myeclipse非maven版本 链接：[http://pan.baidu.com/s/1dFnykhz](http://pan.baidu.com/s/1dFnykhz)  密码：x35a
* [JEECG MAVEN开发环境搭建入门](http://blog.csdn.net/zhangdaiscott/article/details/50915206)
* [JEECG 常见问题必读](http://www.jeecg.org/forum.php?mod=viewthread&tid=1830&extra=page%3D1)
* [JEECG 开发入门视频](http://www.jeecg.org/forum.php?mod=viewthread&tid=197&extra=page%3D1)


* maven依赖下载有问题的，可以直接下载官方提供的 => [JEECG本地Maven仓库](http://git.oschina.net/jeecg/jeecg-local-maven)

技术交流
==========
* [1]. 演示地址： [http://www.jeewx.com/qywx](http://www.jeewx.com/qywx)
* [2]. QQ技术交流群： 390507007
* [3]. 技术论坛： [www.jeecg.org](http://www.jeecg.org)
* [4]. CSDN技术博客： [http://blog.csdn.net/zhangdaiscott](http://blog.csdn.net/zhangdaiscott)


![github](http://static.oschina.net/uploads/space/2016/0424/131025_trWY_930898.png "jeewx")
![github](http://static.oschina.net/uploads/space/2016/0424/131056_lr02_930898.png "jeewx")
![github](http://static.oschina.net/uploads/space/2016/0424/131105_BSlN_930898.png "jeewx")
![github](http://static.oschina.net/uploads/space/2016/0424/131036_oV7J_930898.png "jeewx")
![github](http://img.blog.csdn.net/20160424150826957?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQv/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center "jeewx")

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)