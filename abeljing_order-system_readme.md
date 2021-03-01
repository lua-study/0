# springCloud全家桶技术集合解决高并发难题

#### 介绍
用户购买商品的流程，涉及到的服务有用户服务，账户服务，产品服务，订单服务，支付服务，网关服务。
   技术点：使用spring webFlux + 通用mybatis + spring cloud Config + spring Cloud Netflix的相关Eureka、Hystrix实现服务降级，服务熔断，服务隔离、Zuul、Ribbon和Feign、ELK（日志聚合）、Spring Cloud Sleuth(服务跟踪)、事务方面使用BASE、订单服务使用当当网的Sharding-JDBC进行分表，部署方面使用docker的方式进行自动化部署。为中小企业用户打造微服务全套技术整合，实现中小企业的快速开发。限时秒杀，团购等高并发场景，以及主流的分布式事务技术。

#### 软件架构
项目机构关系：
order-system
    order-system-common：公共模块
    order-system-config :配置中心 （port:8888）
    order-system-eureka  注册中心
    order-system-registration-master   注册中心使用两天机器做集群-主
    order-system-registration-backup   注册中心使用两天机器做集群-备
    order-system-monitor:监控系统
    order-system-gateway:	网关
    order-system-service:     服务
    order-system-customerService:	用户系统
    order-system-orderService:		订单系统
    order-system-accountService:		账户系统
    order-system-productService:		产品系统


#### 安装教程

1. xxxx
2. xxxx
3. xxxx

#### 使用说明

1. xxxx
2. xxxx
3. xxxx

#### 参与贡献

1. Fork 本仓库
2. 新建 Feat_xxx 分支
3. 提交代码
4. 新建 Pull Request


#### 码云特技

1. 使用 Readme\_XXX.md 来支持不同的语言，例如 Readme\_en.md, Readme\_zh.md
2. 码云官方博客 [blog.gitee.com](https://blog.gitee.com)
3. 你可以 [https://gitee.com/explore](https://gitee.com/explore) 这个地址来了解码云上的优秀开源项目
4. [GVP](https://gitee.com/gvp) 全称是码云最有价值开源项目，是码云综合评定出的优秀开源项目
5. 码云官方提供的使用手册 [https://gitee.com/help](https://gitee.com/help)
6. 码云封面人物是一档用来展示码云会员风采的栏目 [https://gitee.com/gitee-stars/](https://gitee.com/gitee-stars/)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)