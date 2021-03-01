## 目前本人主要从事架构开发，也就是闲散吹B人员。。。没事捣鼓捣鼓架构，如果你对架构有啥问题，或者找工作不会吹，可以来我的小圈子，一起
## 学习，我这里弄了个群：492056222。

## 一、微服务提出者
https://martinfowler.com/ 

## 二、介绍
 目前微服务主要是对RPC的进一步封装。SpringCloud所在的这家公司：Pivotal Software，也是着急了，为了抢占市场。把运维的事都搬过来了.... 
其他微服务提供者：这TM怎么玩？？？
开发者：好牛逼啊...... 
玩架构的小伙伴们：好多BUG。。。

## 三、本系列Spring Cloud介绍
本系列版本是：Spring Cloud  Finchley版本，看网上很多都是基于Spring Boot1.x的，Spring Cloud版本也是比较老，之前用的Dalston版，正好做个升级，这里做一个记录。如果您看到了，请留下宝贵的建议，看到必回。

还有一个背景就是，在公司实在没事，每天打游戏，我的王者荣耀都打到星耀快上王者了，大家都开始觉得我自会吹B不会干活了，正好改下架构，刷刷存在感......让大家有点事忙。

## 四、主要章节
1、服务的注册与发现（Eureka）
2、服务消费者（rest+ribbon）
3、服务消费者（Feign）
4、断路器（Hystrix）
5、路由网关(zuul)
6、分布式配置中心(Spring Cloud Config)
7、高可用的分布式配置中心(Spring Cloud Config)
8、消息总线(Spring Cloud Bus)
9、服务链路追踪(Spring Cloud Sleuth)
10、高可用的服务注册中心
11、docker部署spring cloud项目
12、断路器监控(Hystrix Dashboard)
13、断路器聚合监控(Hystrix Turbine)

14、服务注册(consul)

15、SrpingCloud集成mybatis、mysql
17、SrpingCloud集成redis
18、深入理解Feign之源码解析
19、深入理解Eureka之源码解析
20、深入理解Ribbon之源码解析
21、深入理解Zuul之源码解析
22、深入理解Hystrix之源码解析
23、深入理解Config之源码解析
24、深入理解Bus之源码解析
25、深入理解Sleuth之源码解析
26、SpringCloud分布式系统中实现分布式锁
27、Spring Security Oauth2和JWT保护微服务系统
28、docker中部署SpringCloud


## 五：关于微服务的个人想法
如果对大型架构不了解，微服务你可能只会用到RPC远程调用而已。推荐大家多看看大型架构方面的。

比如断路器，其实SpringCloud提供的这个，在实际中用处并不大。因为我们需要的是，当有1万台集群，其中500台不能用或者访问出错，需要自动跳转到其他集群节点，目前SpringCloud给的是每次都会访问错误节点，除非错误节点不能访问才会从注册中心剔除。

在比如链路追踪，对于双十一这样的活动，用法也需要具体考虑，因为他嵌入代码中了，用还是不用，还需要修改配置。

在比如配置中心，哪有把配置放在代码管理工具里面的？？？一般都是有配管、运管来配置的。

其他的嘛，也就没有了。。。。。

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)