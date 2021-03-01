##演示spring boot的基本用法

###注册三大组件
- servlet：ServletRegistrationBean
- Filter：FilterRegistrationBean
- Listener：ServletListenerRegistrationBean

###mvc配置
- @EnableWebMvc：是否接管springMVC
- 注入WebMvcConfigurer接口的实现类：可以映射视图、添加拦截器（HandlerInterceptor实现类）等

###整合druidDataSource
- 配置数据库监控工具：StatViewServlet、WebStatFilter

###自定义Error
- DefaultErrorAttributes
- 自定义错误处理器：@ExceptionHandler

###模版引擎
- thymeleaf
- 国际化

###自定义内嵌servlet容器配置
- 注入WebServerFactoryCustomizer 接口的实现类

###使用外部tomcat作为servlet容器
- 要使用SpringBootServletInitializer
- pom文件配置成war

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)