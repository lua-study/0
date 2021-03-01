###Moba游戏服务器


###FAQ 常见问题

VS 使用 管理员权限开启 服务器， 这样就可以 解决服务器HTTP服务器开启的问题

###游戏视频

https://v.qq.com/x/page/w0523vg401v.html

###整个系统包括：

1：Moba 服务器端物理

2：Moba 客户端物理

3：moba 网络同步

4：moba技能系统实现

5：Moba AI 系统

###游戏元素包括： 塔

水晶

小兵

玩家

场景地图

###技术实现:

服务器采用c#实现 + mysql数据库

客户端采用Unity 2017.2.0f3 实现, 纯c#代码

###源码下载：

客户端

https://gitee.com/liyonghelpme/MobaKeHuDuan

服务器

https://gitee.com/liyonghelpme/MobaFuWuQi

网络协议

https://gitee.com/liyonghelpme/mobaXieYi

配置表

https://gitee.com/liyonghelpme/mobaPeiZhi

###交流群：

QQ: 390313628

###部署说明：

Unity 2017.2.0f3 版本

Mysql数据库

.NetFrame 4.6

Visual studio 2015 社区版

1：安装Mysql服务器

参考服务器下的 ServerConfig.json

创建数据库tank

账号root

密码123456

执行服务器目录下的

tankServer\SocketServer\ConfigData\Scripts\tank.sql 初始化数据库 tank

2：启动服务器工程

Visualstudio 打开tankServer SocketServer工程开始执行

3：复制两份Unity客户端工程，使用 Unity2017.2.0f3 打开工程

打开两个客户端工程

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)