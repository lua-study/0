###java-web-startup

基本上没有什么好介绍的地方,只是一个普通的springmvc+mongodb项目，列一些比较少用的用法:

- redis处理分布式session
- sitemesh 的excludes配置
- spring方法参数验证
- ControllerAdvice 注解配置全局异常处理
- spring data 使用AuditorAware 添加CreatedDate,LastModifiedDate,CreatedBy注解支持
- mongodb保存或更新时唯一值注解验证
- 使用maven的profile 来区分不同的环境。

sitemesh excludes配置时需要在排除的页面添加` `头, 具体参考error/40x.jsp页面
顺便说一句,[Amaze UI](http://amazeui.org/) 很好看啊。
另外，关于redis不得不看这个[江南白衣的“关于Redis的常识”](https://linux.cn/article-1565-1.html)
在appliaction-config.xml中，profile的配置会覆盖掉applicatoin.properties中的默认配置,profile.active值在pom.xml中设置。
```xml
 
     
     
     
         
             classpath:application.properties 
             classpath:${profile.active}/application.properties 
         
     
 
```

在打包的时候使用`maven package -P test`就可以使用test环境的配置。


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)