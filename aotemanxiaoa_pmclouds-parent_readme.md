工程云
====

# 项目主体的技术结构
使用spring-boot +spring-mvc + mybatis + dubbo作为项目主体的技术框架。
其中，mybatis作为orm，druid作为数据库连接池管理工具，dubbo作为远程调用、分布式服务治理工具。
主要的缓存服务器采用redis，现阶段，如果缓存服务器不可用，将会导致部分应用启动失败。
其余的与特殊业务相关的技术，在相应模块中阐述。

# 项目结构
目前的项目结构如下：
1. dubbo-starter dubbo向spring-boot注册需要的配置，源自[teaey/spring-boot-starter-dubbo](git@github.com:teaey/spring-boot-starter-dubbo.git)

2. pmclouds-web pc端的前端工程，需要使用node.js构建，构建后，将自动输出到pmclouds-custormer的resouce/static下

3. pmclouds-api 服务端与请求响应端交互约定的接口及数据结构

4. pmclouds-server 服务提供者，业务逻辑处理的主体，所有的数据由这里负责最终的查询、持久化

5. pmclouds-customer 负责响应并处理前端的请求，将数据转化为系统使用的数据结构，并且调用相应的服务

# 项目的编译运行

整体的编译打包以及依赖管理使用maven3.5.0。 
运行如下命令，可以直接完成全工程的编译打包。
```sh
mvn clean install
```
可运行的jar包位于server和customer的target文件夹下。
日常开发，可以在相应模块下使用
```sh
mvn spring-boot:run
```
命令直接启动。

# 工程云的开发wiki

工程云整体的编码规范、常用工具请参考[工程云开发wiki](http://git.yonyou.com/pmclouds/pmclouds/wikis/home)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)