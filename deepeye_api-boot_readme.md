
# ApiBoot
[![Maven Central](https://img.shields.io/maven-central/v/org.minbox.framework/api-boot.svg?label=Maven%20Central)](https://search.maven.org/search?q=g:%22org.minbox.framework%22%20AND%20a:%22api-boot%22) [![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://github.com/weibocom/motan/blob/master/LICENSE) ![](https://img.shields.io/badge/JDK-1.8+-green.svg) ![](https://img.shields.io/badge/SpringBoot-1.5+_2.0+-green.svg)

`ApiBoot`是一款基于`SpringBoot1.x`、`SpringBoot2.x`的接口服务集成基础框架，内部提供了框架的封装集成，让接口开发者完成开箱即用，不再为搭建接口框架而犯愁，从而极大的提高开发效率。
通过在我的`SpringBoot`系列教程中得到的学习者的反馈，才决定来封装一套对应我文章的基础框架，`ApiBoot`内的每一个框架的具体讲解都在文章内进行了详细说明，如果有不明白的可以通过如下途径访问我的文章：

- [我的博客 - 恒宇少年De成长之路](http://blog.yuqiyu.com)
- [我的简书](https://www.jianshu.com/u/092df3f77bca)

## 主要功能

- **服务资源安全** ：通过整合`SpringSecurity` + `Oauth2`来完成接口服务的安全性，安全拦截路径内的请求必须携带`请求令牌`才可以访问到资源内容，资源内容可配置指定身份、权限访问。
- **服务授权认证中心**：服务授权以及认证是由`Oauth2`来担任，通过`password`授权模式获取`请求令牌`后访问资源服务，一个配置即可开启`Jwt`格式化`AccessToken`
- **文档自动生成**：通过集成`Swagger2`来完成文档的侵入式生成，侵入式文档后期会被替代，`ApiBoot Security Oauth`已默认排除`swagger2`相关的资源路径。
- **返回JSON格式化**：使用阿里巴巴的`FastJson`来完成返回`Json`字符串的格式化，自动扫描装载自定义的`ValueFilter`实现类，用于自定义返回格式化。
- **数据库ORM框架**：`mybatis-enhance`是一款由我开源的数据库持久化框架，基于`mybatis`进行封装编写，可以完成动态查询数据，语法与`SQL`语法几乎一致，内置常用方法提供直接调用，支持方法命名规则查询，一个接口方法就可以自动完成查询，不再编写`SQL`语句。
- **动态数据源**：完成项目的多数据源配置、内部集成`druid`、`HikariCP`数据源实现方式，配置主从数据源、多数据库类型数据源、多种数据源实现方式集成。
- **自动分页插件**：`mybatis-pageable`是一款由我开源的自动化分页插件，直接摆脱编写`分页代码`，仅仅需要传递的分页参数就可以自动进行查询，目前支持主流的**12**种数据库。
- **代码生成插件**：`code-builder`是一款由我开源的代码生成插件，直接摆脱实体类的生成，支持自定义`freemarker`模板来完成自定义生成类文件，比如：`Service`、`Controller`、`Mapper`等。
- **七牛云资源处理**：集成七牛云提供的SDK来完成文件的上传、下载等方法实现，开箱即用。
- **阿里云OSS资源处理**：集成阿里云OSS提供的SDK来完成文件的上传、下载等方法实现，开箱即用。
- **阿里云短信**：集成阿里云提供的SMS服务，简单配置即可完成短信发送，覆盖全球的短信服务，友好、高效、智能的互联化通讯能力，帮助企业迅速搭建客户触达通道。

更多功能请参考 [更多功能列表](https://github.com/hengboy/api-boot/tree/master/api-boot-project/api-boot-starters)

## 组件

- **[Spring Security](https://docs.spring.io/spring-security/site/docs/current/reference/htmlsingle/)**：Spring提供的安全框架，Spring家族式的设计，无缝整合SpringBoot
- **[OAuth2](https://oauth.net/2/)**：OAuth是一个网络授权的标准。
- **[JWT](https://jwt.io/)**：JSON Web Token是目前流行的跨域认证解决方案，用于格式化OAuth2生成的Token。
- **[Quartz](http://www.quartz-scheduler.org)**：分布式定时任务调度框架
- **[Swagger2](https://swagger.io/)**：Swagger是一款API文档生成工具，自动扫描代码进行生成可运行测试的文档。
- **[Mybatis Enhance](https://github.com/hengboy/mybatis-enhance)**：`Enhance`是对于原生的`MyBatis`的增强编写，不影响任何原生的使用，使用后完全替代`mybatis-core`、`mybatis-spring`以及`mybatis-spring-boot-starter`，可以使用`SpringBoot`配置文件的形式进行配置相关的内容，尽可能强大的方便快速的集成`MyBatis`。
- **[DataSource Switch](https://github.com/hengboy/api-boot/tree/master/api-boot-project/api-boot-plugins/api-boot-plugin-datasource-switch)**：一款多数据源自动切换框架，可配置多种数据库类型数据源集成、主从数据源配置。
- **[Mybatis Pageable](https://github.com/hengboy/mybatis-pageable)**：`MyBatis-Pageable`是一款自动化分页的插件，基于`MyBatis`内部的插件`Interceptor`拦截器编写完成，拦截`Executor.query`的两个重载方法计算出分页的信息以及根据配置的数据库`Dialect`自动执行不同的查询语句完成总数量的统计。
- **[Code Builder](https://github.com/hengboy/code-builder)**：`code-builder`是一款代码生成`maven mojo`插件，通过简单的配置就可以完成数据库内`Table`转换`Entity`或者其他实体类，想怎么生成完全根据你的个人业务逻辑，`code-builder`尽可能的完善的提供数据库内的一些定义的信息，让你更方便更灵活的来生成`Java`文件。

更多组件请参考[更多集成组件](https://github.com/hengboy/api-boot/tree/master/api-boot-project/api-boot-starters)

## 怎么使用？

### 添加版本依赖

在使用`ApiBoot`时需要再`pom.xml`文件内的`dependencyManagement`标签内添加如下配置：

```xml
 
   
     
       org.minbox.framework 
       api-boot-dependencies 
       2.0.5.RELEASE 
       pom 
       import 
     
   
 
```

由于`ApiBoot`内后期规划集成的内容比较多，所以根据了`SpringBoot`的版本规划来进行了管理维护，这样在添加使用`ApiBoot`的依赖时就不再需要添加`版本号`，统一交由`api-boot-dependencies`进行管理。

> 注意：该版本默认添加了`spring-boot-dependencies`依赖。

## 使用Demo

`ApiBoot`会为每一个依赖提供一个演示代码集成子项目，都在`api-boot-samples`项目下，为了更好地解释`ApiBoot`的每一个依赖功能，恒宇少年会在每一个`sample`下添加当前项目的`readme`进行详细介绍。

Demo列表：

- [ApiBoot Security Oauth](https://github.com/hengboy/api-boot/tree/master/api-boot-samples/api-boot-sample-security-oauth-jwt)
- [ApiBoot Swagger](https://github.com/hengboy/api-boot/tree/master/api-boot-samples/api-boot-sample-swagger)
- [ApiBoot Http Converter](https://github.com/hengboy/api-boot/tree/master/api-boot-samples/api-boot-sample-http-converter)
- [ApiBoot Alibaba OSS](https://github.com/hengboy/api-boot/tree/master/api-boot-samples/api-boot-sample-alibaba-oss)
- [ApiBoot Alibaba SMS](https://github.com/hengboy/api-boot/tree/master/api-boot-samples/api-boot-sample-alibaba-sms)
- [ApiBoot Quartz](https://github.com/hengboy/api-boot/tree/master/api-boot-samples/api-boot-sample-quartz)
- [ApiBoot DataSource Switch](https://github.com/hengboy/api-boot/tree/master/api-boot-samples/api-boot-sample-datasource-switch)
- [ApiBoot Resource Load](https://github.com/hengboy/api-boot/tree/master/api-boot-samples/api-boot-sample-resource-load)
- [ApiBoot Message Push](https://github.com/hengboy/api-boot/tree/master/api-boot-samples/api-boot-sample-message-push)

## 更新日志

`ApiBoot`每一次发版都会有相应的更新日志，点击访问[更新日志wiki]( )

## 版本管理规范

项目的版本号格式为 x.x.x 的形式，其中 x 的数值类型为数字，从 0 开始取值，且不限于 0~9 这个范围。

- SpringBoot1.x版本对应ApiBoot版本1.x.x
- SpringBoot2.x版本对应ApiBoot版本2.x.x

集成新的第三方框架为小版本更新，对应修改第三位版本数值，如：2.0.1 -> 2.0.2

## 开源交流

### 社区交流

#### 恒宇少年邮件

[jnyuqy@gmail.com](mailto:jnyuqy@gmail.com)

#### 恒宇少年微信

yuqiyu999

#### 钉钉群

![](https://github.com/hengboy/api-boot/blob/master/dingding_group.JPG)

### 项目结构

```
. api-boot
├── api-boot-projects
│   ├── api-boot-autoconfigure
│   ├── api-boot-common
│   ├── api-boot-dependencies
│   ├── api-boot-parent
│   └── api-boot-starters
├── api-boot-samples
│   ├── api-boot-sample-alibaba-oss
│   ├── api-boot-sample-alibaba-sms
│   ├── api-boot-sample-http-converter
│   ├── api-boot-sample-datasource-switch
│   ├── api-boot-sample-security-oauth-jwt
│   ├── api-boot-sample-quartz    
│   └── api-boot-sample-swagger
└── tools
```

### 开源许可

`ApiBoot`采用`Apache2`开源许可。


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)