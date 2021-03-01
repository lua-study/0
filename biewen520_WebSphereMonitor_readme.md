### 简介
该项目监控WebSphere Application Server的重要性能指标，包括（JVM/THREAD）

### 采用技术
在WAS server上部署PerfServletApp.ear项目，该项目能可适时监控SERVER的运行情况，包括JVM、线程、JDBC、EJB等重要指标
通过python脚本来解析PerfServletApp项目返回的XML文件，并入到sqlite 数据库中，每天一张表
前端显示使用Hibernate、Struts2、Spring技术和百度的echarts图表插件

### 项目搭建
1、在要监控的SERVER上安装PerfServletApp.ear项目 
2、部署/Monitor/python目录中的脚本文件在WAS的主机上并把 monitor.py加入到定时任务中   
3、python脚本部署完成之后会根据你设置的定时任务入SQLITE数据库 
4、部署Monitor工程，该工程为JAVA开发需要TOMCAT容器的支撑 
5、需要修改spring.xml文件中的数据库配置如下图： 
![输入图片说明](http://git.oschina.net/uploads/images/2016/0122/105629_154c8fb6_356887.png "在这里输入图片标题")


### 项目图片
![输入图片说明](http://git.oschina.net/uploads/images/2016/0121/180258_baa865fa_356887.png "在这里输入图片标题")

![输入图片说明](http://git.oschina.net/uploads/images/2016/0121/180314_a7c2b8a0_356887.png "在这里输入图片标题")

![输入图片说明](http://git.oschina.net/uploads/images/2016/0121/180329_09b544b4_356887.png "在这里输入图片标题")

### 项目版权
site:http://www.timotai.net 
url: 
    https://git.oschina.net/olives/WebSphereMonitor.git  
    git@git.oschina.net:olives/WebSphereMonitor.git  
    svn://git.oschina.net/olives/WebSphereMonitor  

### 联系方式
QQ:327512450@qq.com

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)