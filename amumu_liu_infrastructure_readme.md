# infrastructure
以Spring Boot整理一些基础架构集合（聚合工程）

# 使用说明
 item-parent： 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp; 是一个父级项目，打包方式是POM，作用：控制其下所有子项目的jar包版本，利于项目包版本统一、项目版本统一升级，降低所用包版本迭代快的影响。 

 item-common: 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp; 这个就不用多介绍了，你认为你每个项目都用的到的，就可以扔进去，包括JAR包。 
        
 springboot-mybatis： 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;集成最全的代码生成工具：entity集成lombok、格式校验，swagger；dao自动加@mapper，service自动注释和依赖；Controller实现restful 增删改查API，并集成swagger与生成配置文件。

 webFluxTest： 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;主要是对spring5的新web框架webflux做了测试性的使用，包含redis-reactive整合与使用，mongodb-reactive的整合与使用。
 webFlux_websocket： 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;主要是对spring5的新web框架webflux和websocket整合使用，使添加消息处理，和定点消息交互更加简单。


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)