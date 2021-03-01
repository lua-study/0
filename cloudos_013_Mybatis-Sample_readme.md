#Mybatis分页插件测试项目  

###说明   

该项目是一个针对分页插件进行测试的项目，可以对分页插件进行修改，通过测试来查看结果。  

**为了和新版本保持同步，使用了maven版本的分页插件**  

使用的maven依赖配置：  
```xml
 
   com.github.pagehelper 
   pagehelper 
   4.0.0 
 
 
   com.github.jsqlparser 
   jsqlparser 
   0.9.1 
 
```  

**如果您需要修改插件来进行测试，请将分页插件的三个代码文件放到本项目中，然后修改插件的配置信息即可**  

修改`mybatis-config.xml`和`mybatis-config-rowbounds.xml`：  
```xml
 
   
     
   
 
```   

将`com.github.pagehelper.PageHelper`改为您导入的`PageHelper`文件。  

###由于测试类隐藏的比较深，这里直接附上地址：  

- Web测试类：[CountryServlet.java][2]

- 配置文件：[mybatis-config.xml][3]  

###项目更新为Web  

由于多数人需要在EL中使用分页数据，所以将此项目改成了Web项目。  

下载该项目后，在目录内执行下面代码:  
```
mvn jetty:run  
```

然后就可以打开浏览器：  
```
http://localhost:8080/  
```

效果如下（这是一个简单的JSP）：

![查询页面][4]

输入页码18，页面大小10后查询：

![查询结果][5]

###分页插件地址  

[http://git.oschina.net/free/Mybatis_PageHelper][6]


###Mybatis相关内容

Mybatis项目：https://github.com/mybatis/mybatis-3

Mybatis文档：http://mybatis.github.io/mybatis-3/zh/index.html  

###Mybatis专栏  

- [Mybatis示例][7]
- [Mybatis问题集][8]  

###作者博客 

- [http://my.oschina.net/flags/blog][9]
- [http://blog.csdn.net/isea533][10] 

  [2]: http://git.oschina.net/free/Mybatis-Sample/blob/master/src/main/java/isea533/mybatis/servlet/CountryServlet.java
  [3]: http://git.oschina.net/free/Mybatis-Sample/blob/master/src/main/resources/mybatis-config.xml
  [4]: http://git.oschina.net/free/Mybatis-Sample/raw/master/src/main/resources/index.png
  [5]: http://git.oschina.net/free/Mybatis-Sample/raw/master/src/main/resources/result.png
  [6]: http://git.oschina.net/free/Mybatis_PageHelper
  [7]: http://blog.csdn.net/column/details/mybatis-sample.html
  [8]: http://blog.csdn.net/column/details/mybatisqa.html
  [9]: http://my.oschina.net/flags/blog
  [10]: http://blog.csdn.net/isea533

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)