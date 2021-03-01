### springboot-web

该工程使用springboot 打造传统的war方式，jsp页面放在了src/main/webapp目录下，所以在debug的时候很不好调试，不能采用直接运行`Application`的方法，所以在debug的时候是debug gradle 项目,而不是debug Application类。

运行该系统之前，需要用户自行配置mysql数据库，添加user表。配置文件神马的只有一个,就是application.properties

该系统的一些的特性:

1. 集成shiro,添加密码salt支持
2. 集成sitemesh
3. 添加自定义的interceptor
4. 使用自定义的error页面，及自定义的异常处理
5. 自定义的JpaSpecificationExecutor的查找, 其实也就是把springside中的类搞过来。

需要添加完善的一些东西有：

1. 研究spring actuator，添加自定义的actuator.
2. 其他的一些集成。

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)