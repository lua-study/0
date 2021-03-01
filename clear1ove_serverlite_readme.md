# 应用层服务器

demo展示：http://www.hut-idea.top/canvas/index.html

#### 介绍
该项目为一个轻量级，高性能的应用层服务器。以Netty4为基础，结合网络编程、Http、websocket协议、SpringMVC以及多种设计模式实现了以下功能：

1. 支持RESTFul，支持应用层协议：Http/s，websocket
2. 集成自实现的简易版SpringMVC。并使用了基于前缀树的动态路由来实现对SpringMVC动态路由
匹配的优化，性能提高60%
3. 实现请求过滤器拦截器
4. 自实现Cookie，Session，其中将Session以Hash的⽅式存储在Redis中从而实现Session共享 
#### 安装教程
1. 安装Jdk8，安装Maven
1. 安装Netty相关依赖
```
    
         
             io.netty 
             netty-all 
             4.1.6.Final 
         
         
             org.json 
             json 
             20160810 
          
     
```

2. 运行MyServerApplication出现Hello Netty则启动成功
3. 通过配置端口可进行http访问

#### 代码架构
> core模块为服务器核心模块，其余部分为对业务逻辑的封装。基于外观模式与约定即配置的原则，使用者只需实现非core目录即可使用。

``` 
.
├── /action （外观action模块，自实现类请是继承+实现AbstractAction类抽象类且加注解@Controller，对具体路由请注解@RequestMapping，过滤器相关请注解@HttpFilter）
├── /filter  (外观filter模块)
├── /service (外观service模块)
├── /dao     (外观dao模块)
├── /utils   (utils帮助类)
├── /entity  (实体类目录，自实现类如果将会被用于作为返回值，请继承CommonResult类)
└── /core    (核心基础模块)
    ├── /anno      (注解相关)
    ├── /exception (异常基本类)
    ├── /enums     (枚举相关类)
    ├── /server    (Netty主配置类，入口ui相关)
    ├── /init      (服务初始化相关)
    ├── /filter    (过滤器相关)
    ├── /handle    (Netty底层handle)
    ├── /domain    (底层实体类)
    └── /config    (基本服务器配置)
``` 


#### 涉及较多的设计模式
1. 模版模式
2. 代理模式
3. build模式
4. 工厂模式
5. 单例模式
6. 策略模式
7. 组合模式

#### 注解
1. @RequestMapping
标记一个方法作为控制器。
2. @Controller
标记一个类为控制器
3. @HttpFilter
标记一个action处理自身业务逻辑前将会被过滤器前置处理


#### 一些数据结构
1. 基数树 Trie  (https://baike.baidu.com/item/%E5%9F%BA%E6%95%B0%E6%A0%91/22853708?fr=aladdin)

#### 一些细节 
1. 服务器相关的配置，需要在config.properties里进行，可对包括服务器端口，https，等等进行配置
 
 
#### 一些坏味道（逃～）


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)