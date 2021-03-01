# SOP(Simple Open Platform)

一个开放平台解决方案项目，基于Spring Cloud实现，目标是能够让用户快速得搭建起自己的开放平台。

SOP提供了两种接口调用方式，分别是：[支付宝开放平台](https://docs.open.alipay.com/api)的调用方式和[淘宝开放平台](http://open.taobao.com/api.htm?docId=285&docType=2)的调用方式。
通过简单的配置后，你的项目就具备了和支付宝开放平台的一样的接口提供能力。

SOP封装了开放平台大部分功能包括：签名验证、统一异常处理、统一返回内容 、业务参数验证（JSR-303）、秘钥管理等，未来还会实现更多功能。

## 项目特点

- 接入方式简单，与老项目不冲突，老项目注册到注册中心，然后在方法上加上注解即可。
- 架构松耦合，业务代码实现在各自微服务上，SOP不参与业务实现，这也是Spring Cloud微服务体系带来的好处。
- 扩展简单，开放平台对应的功能各自独立，可以自定义实现自己的需求，如：更改参数，更改签名规则等。

## 谁可以使用这个项目

- 有现成的项目，想改造成开放平台供他人调用
- 有现成的项目，想暴露其中几个接口并通过开放平台供他人调用
- 想搭一个开放平台新项目，并结合微服务的方式去维护
- 对开放平台感兴趣的朋友

以上情况都可以考虑使用SOP

## 架构图

![SOP架构图](https://images.gitee.com/uploads/images/2019/0309/093312_8afb4789_332975.png "sop.png")

## 已完成列表

- 签名验证
- 统一异常处理
- 统一返回内容
- session管理
- 秘钥管理
- 微服务端自动验证（JSR-303）
- 支持Spring Cloud Gateway
- 关闭签名校验功能
- 整合[easyopen](https://gitee.com/durcframework/easyopen)
- Admin管理平台，统一管理微服务配置，管理路由管理，微服务上下线

## 后期规划

- 完善admin功能
- Spring Cloud Config（Zookeeper）
- SDK

## admin界面预览

![admin预览](https://images.gitee.com/uploads/images/2019/0323/142555_30a0c87d_332975.png "admin1.png")

![admin预览](https://images.gitee.com/uploads/images/2019/0323/142623_2ce00e69_332975.png "admin2.png")

![admin预览](https://images.gitee.com/uploads/images/2019/0323/142643_6fc1b152_332975.png "admin3.png")

## 工程说明

> 运行环境：JDK8，Maven3，Zookeeper

- doc：开发文档
- sop-registry：注册中心，eureka实现
- sop-gateway：网关，统一访问入口，Spring Cloud Zuul实现，可切换成Spring Cloud Gateway
- sop-common：公共模块，封装常用功能，包含签名校验、错误处理等功能
- sop-story：微服务示例，story服务，同时作为Provider提供服务
- sop-book：微服务示例，book服务，也是Consumer，调用story提供的服务
- sop-test：接口调用测试用例


## 相关文档

[开发文档](http://durcframework.gitee.io/sop)

## 沟通交流

Q群：328419269


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)