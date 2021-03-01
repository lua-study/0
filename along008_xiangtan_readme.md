arcgis服务器服务接口
----
- [服务在线管理](http://192.168.13.39:6080/arcgis/manager): arcgis zbzx****@
- 采样点接口：http://192.168.13.39:6080/arcgis/rest/services/samples_xt/MapServer
- 湘潭影像图：http://192.168.13.39:6080/arcgis/rest/services/xiangtan_image2/MapServer
- 行政边界：http://192.168.13.39:6080/arcgis/rest/services/xiangtan_map/MapServer

- arcgis rest api ：http://192.168.13.39:6080/arcgis/sdk/rest/index.html#/Add_Features/02ss0000009m000000/

---------
xiangtan_server配置
----
- applicationContext.xml定义了数据库的连接配置，bean的配置。
- webservice.xml中定义了webservice服务接口的配置

---------
简介
--
产地安全等级评价与禁产区边界确认分析平台

项目结构
----
> 根目录 
> ├ arcgis-viewer-flex-develop ：前端flex viewer源码 
> ├ docs ：项目文档 
> ├ Server ：服务器端源码 
> ├ Screenshot : 截图 
> ├ ArcGIS : ArcGIS服务工具箱等 

安装配置
----

**前端安装配置**

1. git clone源码到本地，将arcgis-viewer-flex-develop导入到Flash Builder 4.6([如何安装破解](http://blog.xlanlab.com/index.php/archives/7/))中;
2. 根据情况配置项目文件：
> \arcgis-viewer-flex-develop\src\config-admin.xml 管理员 
> \arcgis-viewer-flex-develop\src\config-user.xml  普通用户

3. 运行配置,运行：
![运行配置](http://t1.qpic.cn/mblogpic/32f142b5c18e7d70a0fe/2000)

**服务器端安装配置**

待加

更新记录
----

 - 2014.11.5：flex端源码工程，git配置  ---Ethan
 - 2014.11.14：Server端源码工程 ---Ethan
 - 2014.11.21: 插值功能v1.0 ---Ethan


演示截图
----

![工具箱截图](http://git.oschina.net/uploads/images/2014/1121/141445_743116a3_77541.png)

![发布服务](http://git.oschina.net/uploads/images/2014/1121/141509_5ac94da0_77541.png)

待加

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)