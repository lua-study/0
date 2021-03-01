# antdsp 前后端分离的后台管理开发框架

#### 介绍
基于 ant design ( react ) + spring-boot + spring-mvc + apache shiro + spring-data-jpa 等框架，旨在快速开发，轻松部署，为您节约开发时间与成本。包含 用户管理、菜单管理、角色管理、权限授权 、系统日志、SQL监控等常用功能模块。

#### 功能模块

   > 系统管理  
   >> 用户管理  
   >> 菜单管理  
   >> 角色管理  

   > 运维管理  
   >> 操作日志  
   >> 文章管理  
   >> SQL监控  

#### 开发工具
* **Mysql**             数据库  
* **Eclipse**           java编辑  
* **VScode**           js(es5)编辑  
* **Git**               版本管理  
* **Nginx**             反向代理服务器  
* **Navicat**           数据库可视化工具  

#### 项目环境

* [Nodejs](https://nodejs.org/en/download/): v10+  
* [JDK](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html): 1.8+  
* [Mysql](https://www.mysql.com/downloads/): v5.5+  

#### 技术选型

* 前端框架：Ant Design of React  
* 后台核心：Spring-Boot  
* mvc框架：Spring-MVC  
* 持久层框架：Spring-Data-JPA  
* 安全框架：Apache-Shiro  
* 数据库连接池：Druid  
* Excel工具：Apache-POI
* JSON工具： Alibaba-Fastjson
* 云存储： qiniu

#### 如何运行

首先在项目的根目录打开命令行工具

&emsp;1.运行后台  
    &emsp;&emsp; `mvn clean package`  
    &emsp;&emsp; `java -jar antdsp-admin/target/antdsp-admin-x.x.x.jar`  

&emsp;2.运行前端  
    &emsp;&emsp; `cd antdsp-admin/src/main/web`  
    &emsp;&emsp; `npm install`  
    &emsp;&emsp; `npm start`  
&emsp;start 成功后，会自动在默认浏览器打开项目页面


如果您也喜欢这个项目，或者您有更好的更好的idea和意见，您可以在[gitee](https://gitee.com/loving_stranges/Antd-Spring)上 star 或者fork这个项目，期待大牛的指点、协作，共同进步。

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)