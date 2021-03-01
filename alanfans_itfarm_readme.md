#itfarm
一个技术分享的内容网站，包括web端用于用户浏览操作，和后台文章管理
项目的结构如下：
![项目的结构](http://git.oschina.net/uploads/images/2016/0829/092438_14a865df_724638.png "项目的结构")
itfarm-admin
itfarm-api
itfarm-cache
itfarm-commons
itfarm-provider
itfarm-service
itfarm-web

为了学习dubbo和其它技术，所以故意将web和admin分开。

itfarm-admin 后台管理，包括文章，分类，评论，日志，权限等。
itfarm-api 一些工具类、异常、枚举、常量、注解等
itfarm-cache 缓存工具 redis
itfarm-commons 通用的类，拦截器，mybatis生成代码插件、权限所需的model
itfarm-provider dubbo用于提供接口给admin和web远程调用
itfarm-service 持久层和业务接口
itfarm-web  web端，展示页面用户浏览文章

###  **项目使用的技术
 
springMVC、mybatis（自定义插件自动生成代码，包括分页）、shiro权限管理（spring-security也可以）、redis缓存、dubbo、              zookeeper、poi导出excel、velocity导出word、jasig.cas单点登录、solr搜索引擎、kindeditor富文本编辑器


项目一直更新，主要用于学习新技术，界面比较简洁
项目地址：http://itfarm.oschina.mopaasapp.com/ 
后台     http://itfarm-admin.oschina.mopaasapp.com/admin/index.do
      文章管理，只能管理文章和分类。用户名wdd，密码123.界面不是最新的效果、由于前台和后台分离，还有一些问题要解决，没有部署最新
        用户管理包括权限管理

有兴趣的伙伴可以一起学习 :relaxed:  :grinning: 

###  **项目运行步骤 
    1、修改db.properties数据库连接
    2、若不使用dubbo，则在application-Context.xml引入service-context.xml，使用则引入META-INF/applicationContext-dubbo.xml
           并修改配置dubbo地址（和provider注册地址一致）
    3、若使用dubbo，则在itfarm-provider子项目中修改db.properties
        修改dubbo.xml dubbo:registry address（使用zookeeper则输入zookeeper地址，不使用则multicast://224.5.6.7:1234）
    4、若不使用dubbo则直接启动web项目
       若使用dubbo，先运行itfarm-provider类App的main方法，然后启动web项目    

web运行效果图：
![效果图](http://git.oschina.net/uploads/images/2016/0829/092920_6c9a4c1a_724638.png "效果图")

admin效果图（很多功能都未实现）：
![admin效果图](http://git.oschina.net/uploads/images/2016/0829/093041_88f6679b_724638.png "admin效果图")

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)