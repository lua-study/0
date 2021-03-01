## Uncode-SpringCloud
Uncode-SpringCloud是Uncode家族一个最新成员，基于SpringCloud的微服务开发脚手架，用于快速构建中大型系统的基础框架。将开发中遇到的问题和生产中所碰到的各种坑整理归纳，形成相应的解决方案融合到框架中。可以快速完成基础平台搭建。

# 功能概述

- 配置中心：Apollo。
- 服务注册与发现：Eureka，支持开发可以对节点状态进行操作。计划支持Nacos。
- 服务网关：Spring Gateway，支持动态路由和灰度。
- 断路保护和流量控制：Sentinel。
- 服务监控：CAT、SpringCloud Admin。
- 服务安全：Uncode Session。
- 消息通知：RibbitMQ、Event。
- 分布式事务：计划集成seata/fescar。
- 日志：ELK。
- 依赖组件：Uncode-DAL、Uncode-Cache、Uncode-Schedule、Uncode-Session。

## 架构图

![输入图片说明](https://images.gitee.com/uploads/images/2019/0719/102332_5f2f16db_277761.jpeg "SpringCloud架构 (1).jpg")

## 技术文档
* 即将发布，敬请期待，请start项目，给作者一些写文档的支持。

## 核心依赖

| 依赖                 | 版本          |
| -------------------- | ------------- |
| Spring Boot          | 2.0.x.RELEASE |
| Spring Cloud         | Finchley      |
| Spring Cloud Alibaba | 0.2.x.RELEASE |
| Uncode-DAL           | 2.2.5         |
| Uncode-Cache         | 2.0.5         |
| Uncode-Session       | 2.1.0         |
| Uncode-Schedule      | 1.1.0         |

## 工程结构

``` 
uncode-springcloud
├── uncode-springcloud-dependencies -- 依赖定义
├── uncode-springcloud-eureka -- 注册中心
├── uncode-springcloud-gateway -- Spring Cloud 网关
├──  **uncode-springcloud-utils**   -- 工具类，与大量开源软件相似类极高，收藏时未标明出处，后期主要切换到Hutool，保留部分会添加出处。
├── uncode-springcloud-starter-boot -- 启动、配置加载相关封装
├── uncode-springcloud-starter-bus -- 消息、事件、通知相关封装
├── uncode-springcloud-starter-fuse -- 熔断、限流、降级及调用链相关封装
├── uncode-springcloud-starter-log -- 操作日志、ELK、系统日志相关封装
├── uncode-springcloud-starter-canary -- 灰度发布相关封装
├── uncode-springcloud-starter-monitor -- 监控相关封装
├── uncode-springcloud-starter-web -- web相关功能封装
├── uncode-springcloud-starter-security -- 认证和受权相关功能封装
├── uncode-springcloud-parent -- 子应用需要继承的父pom
├── uncode-springcloud-admin -- 管理后台&demo
├── uncode-springcloud-demo -- demo
├    ├── uncode-springcloud-provider-api -- 服务提供api 
├    ├── uncode-springcloud-provider-impl -- 服务提供实现
└──  └── uncode-springcloud-consumer -- 服务消费demo
```


# 个人申明

为了提高项目质量，项目开发过程中大量学习了开源社区JeeSpringCloud、SpringBlade等相关项目的成功经验，按照整体设计意图，尽量取各家所长，个人尊重每一位作者的辛勤付出，如有不妥，请及时找本人沟通。开发过程经过仔细考量，主要应对企业落地过程中的各种问题，仍有很多不完善之处，未来希望在devops部分有所突破，有相同想法的人欢迎沟通。



#  关于

作者：冶卫军（[ywj_316@qq.com](mailto:ywj_316@qq.com),微信:yeweijun）

技术支持QQ群：47306892


# 界面一览

![输入图片说明](https://images.gitee.com/uploads/images/2019/0719/102111_9fcf8a8a_277761.png "微信图片_20190718161017.png")
![输入图片说明](https://images.gitee.com/uploads/images/2019/0719/102130_2afd7233_277761.png "微信图片_20190718161136.png")

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)