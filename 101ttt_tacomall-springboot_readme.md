 
	   
 
 [power by 码上talk©] 
 
	 
		 
	 
     
		 
	 
	 
		 
	 
	 
		 
	 
 
 
基于springboot开发的maven多模块聚合商城后台，弹性的水平架构设计，适用于中大型项目的开发，同时让大家免于项目搭建的繁琐，将主要的精力用于业务开发。
 

 
基于spring cloud开发的微服务商城后台。 弹性的水平架构设计，优雅的代码，合理的注释，丰富的接口文档，适合想入门微服务，却又没有适合的项目练习的同学们。 =====>
 另有springcloud版本 
 

 
 tacomall并不是一个单纯的后台项目，你可能还需要跨平台小程序=====>
 tacomall-uniapp 
 

 
除此之外，你希望我们有一个完整的商城开源项目=====>
 商家管理后台 
 平台管理后台 
 

[TOC]

```
                                                                
                                                                
                                                                
 __  ___  ___      ___      ___      _   __      ___     // //  
  / /   //   ) ) //   ) ) //   ) ) // ) )  ) ) //   ) ) // //   
 / /   //   / / //       //   / / // / /  / / //   / / // //    
/ /   ((___( ( ((____   ((___/ / // / /  / / ((___( ( // //     

如果你发现项目不错，不要忘记给项目点个赞👍，你的支持是我们前进的动力 :)
```

## 项目结构

通过项目结构，你将清楚明白你即将入手的是一个怎么样的项目，你可能需要什么，如何快速的把它变成自己的产品。

### 核心业务

- [x] [公共依赖](https://gitee.com/running-cat/tacomall-springboot/tree/master/tacomall-common) 公共工具库、异常
- [x] [实体类](https://gitee.com/running-cat/tacomall-springboot/tree/master/tacomall-entity) java bean和数据库的映射
- [x] [代码生成](https://gitee.com/running-cat/tacomall-springboot/tree/master/tacomall-generator) 提供entity和mapper的快速生成
- [x] [数据库操作](https://gitee.com/running-cat/tacomall-springboot/tree/master/tacomall-mapper) 数据库操作
- [x] [任务调度](https://gitee.com/running-cat/tacomall-springboot/tree/master/tacomall-job) 提供任务调度创建，执行
- [x] [微信小程序接口](https://gitee.com/running-cat/tacomall-springboot/tree/master/tacomall-api/tacomall-api-portal) 微信小程序接口,提供用户，商品服务
- [x] [平台管理后台](https://gitee.com/running-cat/tacomall-springboot/tree/master/tacomall-api/tacomall-api-admin) 提供商家，商品, 会员管理
- [ ] [商家管理后台](https://gitee.com/running-cat/tacomall-springboot/tree/master/tacomall-api/tacomall-api-enterprise) 提供商品, 会员管理
- [x] [开放平台](https://gitee.com/running-cat/tacomall-springboot/tree/master/tacomall-api/tacomall-api-open) 开放接口

### 架构原理

通过maven聚合方式开发，将开发过程中可重复依赖的模块提升为公共依赖，从而实现“高内聚，低耦合”的效果。

### 代码描述

~~~
tacomall-springboot                             项目
├─tacomall-api                                  接口模块
│  ├─tacomall-api-admin                         平台管理后台
│  ├─tacomall-api-enterprise                    商家管理后台
│  ├─tacomall-api-open                          开放接口
│  ├─tacomall-api-portal                        小程序接口
├─tacomall-job                                  任务调度
│  ├─tacomall-job-admin                         调度接口
│  ├─tacomall-job-executor                      调度执行
├─tacomall-common                               公共依赖
├─tacomall-entity                               实体类
├─tacomall-generator                            代码生成
├─tacomall-mapper                               数据库操作
├─pom.xml                                       依赖构建配置
~~~

## 上手指南

我们希望开源的项目能够让每一个人都能够一看就懂，轻松上手，但这并不意味者我们不需要做任何东西，相反，在正式运行项目前，你必须完成以下步骤。

### 环境要求

为了避免运行开发中遇到一些意想不到的问题，我们推荐你安装如下环境。

1. Git
2. JDK1.8+
3. Maven3.5+
4. Mysql5.7+
5. Idea2019.3.3
6. Postman
7. mysql
### 安装步骤

通过以下步骤，你将很快看见项目运行起来了！

1. 克隆项目

```
git clone https://gitee.com/running-cat/tacomall-springboot.git
```
2. 配置idea

为了更好的运行项目，我们需要将idea的jdk环境路径配置为我们上面早已安装好的jdk1.8+,同时配置idea默认maven路径为我们上述安装好的maven并配置好国内源。

3. 导入idea

打开idea导入克隆下来的项目

4. maven依赖安装

右键根目录的pom.xml，maven->reimport

5. 导入数据

打开我们的数据库管理工具（navicat for mysql）。

```
创建数据库->tacomall(数据库名)->导入sql脚本（tacomall.sql）
```

6. 修改数据库配置

在每个接口模块项目中（src/main/resources/application-dev.yml）修改相应的数据库配置。

7. 运行服务

接口有多个模块，彼此相互独立，我们只需要像普通springboot项目一样启动。

## 测试

看到这里，我们认为你已经正确配置启动项目了，接下来你将通过postman看到实际效果。

```
http://localhost:4000/portal/member/login
```

##部署

我们提供了docker容器化部署方案，详情请查看[部署](https://gitee.com/running-cat/tacomall-springboot/blob/master/LICENSE)，但并不意味着你不得不选择docker部署，你仍然可以自由选择你喜欢的部署方式进行部署。

## 使用的框架

项目中使用到以下框架（不限于）

| 框架             | 说明                                                         |
| -------------------- | ------------------------------------------------------------ |
| springboot        | 提供web服务功能 |
| mybatis-plus    | 提供简化的数据库操作接口      |
| dynamic-datasource-spring-boot-starter    | 多数据源解决方案      |
| springfox-swagger2    | 接口文档      |
| weixin-java-miniapp   | 小程序sdk      |

## 版本控制

每个版本的发布我们将在[RELEASE.md](https://gitee.com/running-cat/tacomall-springboot/blob/master/RELEASE.md)记录跟踪。

## 版权声明

项目在[Apache License 2.0](https://gitee.com/running-cat/tacomall-springboot/blob/master/LICENSE)下自由使用。

## 社区

 
     
         关注“码上talk”微信公众号 
         tacomall QQ交流群 
         我的微信 
     
     
           
           
           
     
 

 如果您觉得有帮助，请点右上角 "Star" 支持一下谢谢 

 如果您对此项目感兴趣，请点右上角 "Star" 支持一下谢谢 

 如果需要帮助请留言或者加微信，晚上20：00后统一回复解决 

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)