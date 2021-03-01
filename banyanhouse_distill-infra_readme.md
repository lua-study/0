# distill-infra

[![star](https://gitee.com/banyanhouse/distill-infra/badge/star.svg?theme=dark)](https://gitee.com/banyanhouse/distill-infra/stargazers)
[![fork](https://gitee.com/banyanhouse/distill-infra/badge/fork.svg?theme=dark)](https://gitee.com/banyanhouse/distill-infra/members)

## 介绍

一种Go基础设施框架，启动过程类似于java的spring boot，然而逻辑加载和处理过程要强于前者。将各种基础设施封装于Starter组件之中，通过实现starter.go中的Starter接口，通过协程方式初始化各类基础设置中间件的集成。项目默认封装了**toml**配置、**iris**框架、**casbin**权限管理、**jwt-go**认证管理、**xormplus**持久框架、**logrus**日志引擎、以及整合了**go-micro**框架，可以采用**etcdv3**、k8s、consul等注册中心，当然也可以使用go-micro框架集成的熔断、限流等组件，作为微服务框架的基础设置层实现。可参考banyanhouse本人项目列表中的baixing项目，因本人工作繁忙，文档更新较慢，欢迎有志之士star或fork。

## 使用教程

1. [distill-base](https://gitee.com/banyanhouse/distill-base)第一个基础web框架教程，结合distill-infra框架，且提供docker编译镜像，容器运行步骤。
2. [distill-db-tx](https://gitee.com/banyanhouse/distill-db-tx)集成了xormplus实现的一些事务操作场景
3. [distill-micro-http](https://gitee.com/banyanhouse/distill-micro-http)采用http协议构建的微服务
4. [distill-micro-grpc](https://gitee.com/banyanhouse/ditill-micro-grpc)采用grpc协议构建的微服务
5. [distill-micro-grpc-hystrix](https://gitee.com/banyanhouse/distill-micro-grpc-hystrix)远程grpc协议结合hystrix-go构建支持熔断调用的微服务
6. 微服务教程后续更新...

## 安装教程

建议采用go.mod文件直接引用，即可使用本框架。

go mod tidy

go build

## 使用说明

1.  在项目框架中提供了brun包，作为项目启动样例。
2.  可以在项目中创建一个配置包，本项目样例在brun/boot目录中app.go文件中
3.  将所使用到的基础设置Starter在此文件中进行配置，再将app.go所处的包引入到main.go文件中即可完成配置启动。

## 参与贡献

1.  目前只有我一个人在做
2.  ...

## 码云特技

1.  使用 Readme\_XXX.md 来支持不同的语言，例如 Readme\_en.md, Readme\_zh.md
2.  码云官方博客 [blog.gitee.com](https://blog.gitee.com)
3.  你可以 [https://gitee.com/explore](https://gitee.com/explore) 这个地址来了解码云上的优秀开源项目
4.  [GVP](https://gitee.com/gvp) 全称是码云最有价值开源项目，是码云综合评定出的优秀开源项目
5.  码云官方提供的使用手册 [https://gitee.com/help](https://gitee.com/help)
6.  码云封面人物是一档用来展示码云会员风采的栏目 [https://gitee.com/gitee-stars/](https://gitee.com/gitee-stars/)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)