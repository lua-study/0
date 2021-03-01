# fo-ssm
### &emsp;&emsp;一个集成SpringMVC、Spring、Mybatis等框架的快速开发的项目，需要根据自己需要简单修改配置即可作为自己项目的开发基本架构。  


基于约定大于配置原则。

规范约定：
    1. 数据库表字段使用下划线(_)分割单词，对应Java实体使用驼峰命名法，这里`mybatis-config.xml`中的配置项：
    ``` ```
    会自动将驼峰命名法的属性与数据库中的下划线命名法的字段关联起来，而不需要手动去写`resultMap`。

需要自定义修改的地方为：
项目的包名，原包名为`com.panhainan`，修改成你的包名；
    由于项目包名在配置中需要使用，因此在`src/main/resources/spring/`中的`spring-service.xml`和`spring-web.xml`文件中的`context:component-scan`将其中的包名改为你的包名；以及在`spring-dao.xml`里面的配置`mybatis`的注入`dao`接口配置处和实体自动扫描处将包名修改。

其他的根据自己的需要进行修改，比如数据库配置，日志配置等等；
 

 
 
 
部署配置过程中遇到问题可以联系作者，作者联系方式如下：  
 
    潘海南   
    网站： panhainan.com    
    邮箱：panhainan@yeah.net   
    Q Q ：1016593477  
 



# 如果觉得好，就请支持一下，谢谢！  

 
    

    

 


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)