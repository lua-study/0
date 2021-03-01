# Meteor(中文名流星)

#### 介绍

>流星划过，照亮整个天空，整个世界一片光明，虫子无处可藏。

+ 该项目基于阿里开源的Arthas基础之上完成，定位为：应用诊断工具,是线上问题定位的神器

+ 旨在:方便，快捷，安全的使用Arthas

+ 项目无侵入性，通过获取自动字节码的方式来工作，具体详见：[Arthas帮助文档](https://alibaba.github.io/arthas/)

 [实践文档下载](readme/Meteor-实践.pdf)
 
#### 软件架构


|栏目|内容|备注|
|:-|:-|:-|
|主体框架|SpringBoot|版本： 2.1.5.RELEASE|
|前端|freemarker模板引擎||
|UI|ace|WEB模板框架，项目的 resources/static/ace目录中|
|Agent|arthas|Agent用于数据的采集|
|Proxy|tunnelserver|用户Agent数据收集的代理|
|SSH|ganymed-ssh2|ssh协议用于连接linux服务器|
|数据库|H2|用于Meteor-console的数据库|

软件架构图：


![](readme/meteor.png)



#### 安装教程

1.  执行meteor-console进行打包
2.  运行meteor-console-0.0.1-SNAPSHOT,默认开启8884端口

执行命令：
```
java -jar meteor-console-0.0.1-SNAPSHOT &
   
```
   
3.  运行meteor-plugin中的arthas-tunnel-server-xxx.jar,启动了 7777端口 和 8080端口

```
java -jar arthas-tunnel-server-xxx.jar &
   
```

如果不想使用8080端口，可以进行修改,如：9999

```
java -jar -Dserver.port=9999 arthas-tunnel-server-xxx.jar &

```
#### 使用说明

1.  登录Meteor,请求地址：http://domain:8884 ,默认账号 admin/reywong


![](readme/login.png)


2.  Meteor主页功能介绍

![](readme/index.png)

>备注： 左边为功能区，中间为工作区，主页显示了帮助文档

3.  添加服务器

> 具体步骤查看，登录后首页的帮助文档

4. 初始化数据库

  项目启动前会检查${user.dir}目录下的 【meteordb】文件夹，如果不存在会生成数据库，该数据库在项目的 resources/db/h2 中
  
5. 初始化Agent

   在【服务器管理】中，设置好参数点击【初始化】的时候会上传agent到远程服务器的/tmp/meteor目录中，该agent在项目的resources/agent中
      

#### 功能列表

1. 查询JVM中加载的类

![](readme/work.png)

2. 代码在线编辑部署

![](readme/code.png)

3. 方法监控

![](readme/method.png)

4. 线程管理

![](readme/thread.png)

5. Dashboard

![](readme/dashboard.png)


#### 参与贡献

    该项目还是第一个版本，会面会持续更新，如果有问题可以给我留言，或者给我发邮件，邮箱：reywongc@163.com

  


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)