### jad-cache
此项目是对是Spring3中缓存模块的扩展，除了沿用原来的Spring缓存注解之外，还增加了对MemCache、EhCache、redis的实现，并且提供了一些新新的功能，本项目具有以下特点：  
1.提供统一的缓存操作api；  
2.支持同时使用EhCache、MemCache和redis等多种缓存实现；  
3.提供灵活的配置；  
4.可以防止缓存穿透；  
5.可以灵活指定缓存存活时间；  
6.任意控制缓存的停用或启用。  

### 使用手册与其它参考文档

 _JAD-CACHE缓存框架，使用手册_ 
[https://my.oschina.net/u/1415710/blog/857238](https://my.oschina.net/u/1415710/blog/857238)

JAD-CACHE架构设计
[https://my.oschina.net/u/1415710/blog/855923](https://my.oschina.net/u/1415710/blog/855923)

 _JAD-CACHE集成 memcache 原理_ 
[https://my.oschina.net/u/1415710/blog/857246](https://my.oschina.net/u/1415710/blog/857246)

 _JAD-CACHE集成 EhCache 原理_ 
[https://my.oschina.net/u/1415710/blog/857245](https://my.oschina.net/u/1415710/blog/857245)


 **本项目附件中有详细的使用册及其它参考文档可打包下载** ，在本项目wiki首页中也有相关连接，包括本项目的架构设计，源码解读等等。
关注最下方作者公众号，可获得最新信息。

###  快速集成

JAD-CACHE目前暂时只支持Map本地缓存、EhCache、MemCache和redis四种，开发人员可以单独使用其中一种，也可以同时使用这几种。  
JAD-CACHE是典型的Maven项目，下分四个子模块jad-cache-api、jad-cache-ehcache、jad-cache-memcache、jad-cache-redis。  
其中jad-cache-api为公用部分及相关api，jad-cache-ehcache为与Ehcache的集成模块，jad-cache-memcache为与memcache的集成模块。  
开发人员在将本框架集成到项目中时，可以选择性的使用自己想集成的缓存实现，如果只使用Map本地缓存，就加入以下依赖：

```
 
			 com.jad.infr 
			 jad-cache-api 
			 1.0.2-RELEASE 
 
```
如果你想用ehcache缓存，就用加入以下依赖：
```
 
			 com.jad.infr 
			 jad-cache-ehcache 
			 1.0.2-RELEASE 
 
```
如果用memcache，就用以下依赖
```
 
			 com.jad.infr 
			 jad-cache-memcache 
			 1.0.2-RELEASE 
 
```
如果用redis，就用以下依赖
```
 
			 com.jad.infr 
			 jad-cache-memcache 
			 1.0.2-redis 
 
```
 _提示：用ehcache或memcahce时，jad-cache-ehcache或jad-cache-memcache会自动把它相关依赖添加进来（包括本框架的jad-cache-api），用户无须再额外配置。_ 

### 常用配置案例

本框架的配置总体上比较简单，但是比较灵活，而且很多参数都可以缺省配置，以下跟据不同的业务场景提供了几种极简的默认配置，开发人员可以在这个基础上进行配置。

 _项目中只使用EhCache的配置_ 
```
 
 
 
          
 
 
```

 _项目中只使用MemCache的配置_ 
```
 
 
 
          
 
 

```
 _项目中同时使用EhCache和MemCache的配置_ 
```
 
 
 
              
               
                 
                     
                     
                 
             
       
 
         
             
                 ehCache1   
                 ehCache2   
             
         
 
 
 
         
             
                 memCache1   
                 memCache2   
             
         
 
```
### 基本使用

 _注解方式_   
    注解方式跟使用SpringCache自身的缓存注解方式一模一样，这里不再介绍。  
 _api方式_   
本框架两个两个类作为开放的操作缓存的api，分别是：  
 **com.jad.cache.common.api.CacheClientHelper** 和 **com.jad.cache.common.api.CacheHelper**   
其中CacheClientHelper类操作缓存客户端实例的启停，CacheHelper类可以从给定名称的Cache中读取缓存数据。  
 **CacheClientHelper常用api**   
    CacheClientHelper常用的方法如下：  
 **getInstance()** 获得此类的实例（此类的构造函数已经私有化了，需要通过此方法来获得它的实例）。  
 **init(MasterCacheManager)** 初始化，这个方法系统会自动调用，开发人员无需理会  
 **getClientNames()** 获得系统中所有缓存客户端的名称列表  
 **start(String)** 启动一个客户端，参数为客户端名称  
 **stop(String)** 停止一个客户端，参数为客户端名称  
 **isStarted(String)** 检查客户端是否启动，参数为客户端名称  
   
CacheHelper常用api  
 **getInstance(String)** 跟据缓存名称获得此类的实例（此类的构造函数已经私有化了，需要通过此方法来获得它的实例），参数为需要操作的 Cache的名称。  
 **get(String)** 从缓存中读取数，参数为key  
 **put(String, Serializable)** 往缓存中插入数据  
 **put(String, Serializable, int)** 往缓存中插入数据，并指定存活时间  
 **evict(String)** 跟据key从缓存中删除数据  
 **clear()** 清空缓存数据  

### 关于单元测试  
本框架源码中每个模块都有对应的单元测试类，代码在src/test/java下面，配置在src/test/resources。本人是通过testng进行测试的，建议开发人员安装testng插件进行测试。

### 关于日志输出配置

本框架采用log4j输出日志，配置如下：
```
#alisoft memcache   
log4j.logger.com.alisoft.xplatform.asf.cache=ERROR  
#ehcache  
log4j.logger.net.sf.ehcache=ERROR
```  
以上两行分别是阿里memcache 客户端中的日志配置以及ehcache的配置  
跟本框架相关的日志配置如下
```  
#jad-cache-api  
log4j.logger.com.jad.cache.common=DEBUG  
#jad-cache-ehcache  
log4j.logger.com.jad.cache.ehcache=DEBUG  
#jad-cache-memcache  
log4j.logger.com.jad.cache.memcache=DEBUG  
```  
其它具体的详细配置可参见源码的测试用例，开发人员可跟据自己的需要来指定相应的日志输出级别

### 关于作者  
想了解更多详细信息，可用微信扫一下二维码关注本人的公众号  
![欢迎关注本人公众号：JAVA践行者](http://git.oschina.net/uploads/images/2017/0312/195840_c6f58f1a_72884.jpeg "在这里输入图片标题")



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)