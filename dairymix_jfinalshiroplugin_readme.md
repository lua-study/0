#JFinalShiroPlugin
JFinal的Shiro插件，实现权限管理。 

升级说明
1）支持JFinal 2.0 版本。

dist里的文件，使用JFinal 1.x版本请使用 jfinal－shiro-1.0.0.jar。
使用JFinal 2.x版本，请使用jfinal－shiro-2.0.0.jar

如何使用请参照以下两篇篇文章

[给JFinal添加Shiro插件功能，支持Shiro所有注解-实现篇](http://my.oschina.net/myaniu/blog/137198)

[给JFinal添加Shiro插件功能，支持Shiro所有注解-使用篇](http://my.oschina.net/myaniu/blog/137205)

simple目录下有一些实际项目的零碎代码。

web.xml及shiro.ini是shiro的配置信息。

ShiroDbRealm.java 需要根据自己的业务来实现，可参考实现。

LoginController.java 也需要根据自己的业务进行订制，可参考其代码。

其他几个文件主要用来支持 待验证吗的登陆验证。


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)