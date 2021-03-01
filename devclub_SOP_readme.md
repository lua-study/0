# SOP(Simple Open Platform)

一个开放平台解决方案项目，基于Spring Cloud实现，目标让用户快速搭建自己的开放平台。

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

![架构图](https://images.gitee.com/uploads/images/2019/0821/201531_0f605f7c_332975.png "SOP架构图")

> 如上图所示，整个系统运行后，开发者只需关注微服务中的业务代码，接口变更后重新部署微服务应用即可

## 已完成列表

- 签名验证
- 统一异常处理
- 统一返回内容
- session管理
- 秘钥管理
- 微服务端自动验证（JSR-303）
- 支持Spring Cloud Gateway
- Admin管理平台，统一管理微服务配置，管理路由管理，微服务上下线
- 接入方管理+秘钥管理
- 接口权限分配
- 文件上传/下载
- SDK
- 接口限流
- 文档整合
- 应用授权
- 监控日志
- 支持nacos
- 网关动态修改参数

## 界面预览

![服务列表](https://images.gitee.com/uploads/images/2019/0711/174825_2856281f_332975.png "服务列表")

![路由管理](https://images.gitee.com/uploads/images/2019/0711/174843_1648591c_332975.png "路由管理")

![限流管理](https://images.gitee.com/uploads/images/2019/0711/174900_9315cc8e_332975.png "限流管理")

![秘钥信息](https://images.gitee.com/uploads/images/2019/0711/174921_bd817533_332975.png "秘钥信息")

![API文档](https://images.gitee.com/uploads/images/2019/0711/174939_97886883_332975.png "API文档")

![沙箱环境](https://images.gitee.com/uploads/images/2019/0711/175226_3f69346a_332975.png "沙箱环境")

## 工程说明

> 运行环境：JDK8，Maven3，[Nacos](https://nacos.io/zh-cn/docs/what-is-nacos.html)，Mysql

- doc：开发文档
- sop-common：公共模块，封装常用功能，包含签名校验、错误处理、限流等功能
- sop-gateway：网关，统一访问入口，Spring Cloud Zuul实现，可切换成Spring Cloud Gateway
- sop-example：微服务示例，含springboot,springmvc示例
- sop-website：开放平台对应网站，提供文档API、沙箱测试等内容
- sop-auth：应用授权服务
- sop-admin：后台管理
- sop-sdk：基础sdk，含Java、C#版本
- sop-test：接口调用测试用例

## 分支说明

- master：发版分支
- spring-cloud-gateway：Spring Cloud Gateway作为网关
- develop：日常开发分支
- eureka：使用eureka注册中心
- 1.x：老的1.x版本代码

## 相关文档

[开发文档](http://durcframework.gitee.io/sop)

## 沟通交流

Q群：328419269


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)