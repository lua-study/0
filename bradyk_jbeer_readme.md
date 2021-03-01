##JBEER##
**JBeer_framework重在实现当前流行的J2EE开发框架思想，同时加入作者自己的理解，并不是为了替换某个框架而开发，只是总结一下自己的想法** 
相关项目文档地址：[http://my.oschina.net/bieber/blog?catalog=411371](http://my.oschina.net/bieber/blog?catalog=411371)

##主要包括模块##
>###MVC###
>1、支持restful风格的请求路径 
>2、支持自动封装请求参数到Controller中，当是单例模式，只支持将restful请求路径的变量值复制到方法参数中，通过框架提供的工具类，或者集成框架的BaseController类，手动从框架中获取前端请求参数对象信息 
>3、简易的文件上传支持 
>4、支持多种前端展示模板以及格式支持，当前支持JSON,JSONP，JSTL,FREEMARKER,VELOCITY后续可能为对其他进行兼容，比如PDF，EXCEL等等 
>5、对Controller支持单例和非单例的模式，单例更省内存 
>###IOC###
>1、如果你习惯了Spring的IOC风格，那么JBEER，你一定会习惯，采取注解配置的方式，声明BEAN 
>2、支持第三方切入Bean的实例化过程，提供了 InitializingBean , InitializingPostBeanProcessor ,以及对Facotry的注入等接口，方便第三方接入IOC中
>###AOP###
>1、声明式AOP 
>2、通过装饰模式实现整个AOP切入过程 
>3、采用JDK或者CGLIB进行代理 
>###Resource###
>1、对配置文件支持classpath搜索，并支持通过注解注入到Bean或者方法参数中 
>2、对IN18支持占位符替换以及整个classpath搜索，同样也支持通过注解注入到Bean或者方法参数 
>###DB###
>1、支持声明式事务 
>2、支持系统默认数据源，也可以使用第三方数据源，默认数据经过测试支持一定量的并发 
>3、友好的DAO访问接口设计 
>###关于插件###
>1、支持对需要切面的插件以及普通插件扩展
>2、框架提供了充分的接口，来支持插件的扩展，比如对渲染试图的扩展

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)