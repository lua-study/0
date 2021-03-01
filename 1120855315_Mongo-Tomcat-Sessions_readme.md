# Mongo-Tomcat-Sessions

#### 项目介绍
这是一个Tomcat会话管理器，可以在MongoDB中保存会话。它由MongoManager构成，它提供了保存/加载函数，以及控制保存时间的MongoSessionTrackerValve。
此项目依赖于tomcat 7.0.90开发，由于Mongo-Tomcat-Sessions长时间没有更新，因此开发此项目。

#### 软件架构
软件架构说明


#### 安装教程



#### 使用说明

Add the following into your tomcat server.xml, or context.xml

```
 
 
```
The Valve must be before the Manager.

The following parameters are available on the Manager :-

1.  **maxInactiveInterval**  The initial maximum time interval, in seconds, between client requests before a session is invalidated. A negative value will result in sessions never timing out. If the attribute is not provided, a default of 60 seconds is used.
2.  **processExpiresFrequency**     Frequency of the session expiration, and related manager operations. Manager operations will be done once for the specified amount of backgrondProcess calls (i.e., the lower the amount, the more often the checks will occur). The minimum value is 1, and the default value is 6.
3.  **host**     The database hostnames(s). Multiple hosts can be entered, seperated by a comma
4.  **port**     The database port to connect to. The same port will be used for each database host. The default is 27017
5.  **database**     The database used to store sessions in, the default is 'sessions'


#### 参与贡献

mongodb

#### 码云特技


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)