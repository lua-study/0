# FlyShop

#### 项目介绍
FlyShop是国内第一个基于JAVA编程语言开发的开源网店购物系统，采用Spring Boot、freemark、Bootstrap等开源技术和自主框架技术开发。以其开源、免费；安全、稳定；强大、易用；高效、专业等优势占据了国内JAVA电子商务系统领域的主导地位，提供在线帮助、视频教程、支持论坛、在线客服等多种完善的技术支持和服务，定位营销型、互动型、赢利型、安全、稳定的企业级网上商城系统。

核心框架：Spring Boot 1.58 
持久层框架：mybatis 3.4.6 
定时器：Quartz 2.3 
数据库连接池：Druid 1.1.5 
日志管理：SLF4J 1.7、Log4j 

#### 目前完成说明
目前正在开发管理后台中！ **QQ交流群：211378508** 


#### 技术选型：

* JDK8
* MySQL
* Spring-boot
* mybatis
* Ehcache
* Freemarker
* Bootstrap
* SeaJs


#### 打包部署开发环境

- 将项目config目录里的webdata.properties数据库名，用户名，密码设置成你自己的
- 导入doc目录里flyshop.sql导入到你MySql里进行执行
- 运行 `mvn clean compile package`
- 开发者用户将 target目录下的FlyShop.jar和config、uploadfiles、views三个目录到你想存放的地方
- 直接下载运行包的用户忽略上一步操作，直接将压缩包解压到自己存放网站目录下按下面操作
- 运行 `java -jar FlyShop.jar --spring.profiles.active=prod > logs/FlyShop.log 2>&1 &` 项目就在后台运行了
- 关闭服务运行 `ps -ef | grep FlyShop.jar | grep -v grep | cut -c 9-15 | xargs kill -s 9`
- 查看日志运行 `tail -200f logs/FlyShop.log`

#### 目录结构说明：
    1. 程序打包后，config(数据库配置文件)、uploadfiles（图片上传目录）、views（静态资源和模板，静态如：css、js，模板后台模板前台PC和移动端）、FlyShop.jar
    2. 配置和模板写在包外是为了让不懂java的也可以使用，只要会HTML就可以编写模板，输入运行命令直接就可以运行了

### 图片演示 
*权限分配
![权限分配](doc/权限分配.png "权限分配.png")

### 在线文档

- [JDK7英文文档](http://tool.oschina.net/apidocs/apidoc?api=jdk_7u4 "JDK7英文文档")

- [Spring4.x文档](http://spring.oschina.mopaas.com/ "Spring4.x文档")

- [Mybatis3官网](http://www.mybatis.org/mybatis-3/zh/index.html "Mybatis3官网")

- [Nginx中文文档](http://tool.oschina.net/apidocs/apidoc?api=nginx-zh "Nginx中文文档")

- [Freemarker在线手册](http://freemarker.foofun.cn/ "Freemarker在线中文手册")

- [Bootstrap在线手册](http://www.bootcss.com/ "Bootstrap在线手册")

- [Git官网中文文档](https://git-scm.com/book/zh/v2 "Git官网中文文档")


## 许可证

[MIT](LICENSE "MIT")

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)