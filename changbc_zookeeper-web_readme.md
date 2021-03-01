# zookeeper-web - 在线 zookeeper管理工具

------

    zookeeper-web是一个简单的、方便的zookeeper管理工具。我厌烦了通过命令行来管理zookeeper，同时需要一个我熟悉的框架来开发的工具。借鉴了github上一个用python写的管理工具（抱歉，我后来没有找到这个项目的地址）。
    使用主流的springmvc、freemarker、bootstrap和zkclient来开发。

开发的时间比较短，在三天的时间里，利用零零碎碎的时间把这个项目搞定。期望不要太高。

**简单一点 方便一点**

------

您可以使用 zookeeper web：
==

> * 方便的查看zookeeper的节点和节点数据
> * 快捷的添加、删除和级联删除节点
> * 快捷的编辑节点数据，目前只支持文本数据
> * 简单的权限控制，未登录的用户只能查看

Quick Start
==

如果你对源码有兴趣请从oscgit下载源码构建.

源码地址:

oscgit

    git clone https://git.oschina.net/crystony/zookeeper-web.git


如果你是gradle用户(2.0以上),请直接执行以下命令运行项目：

    gradle jettyRun

如果你没使用gralde,执行项目跟路径下的脚本,linux/windows用户执行

    gradlew/gradlew.bat jettyRun

自动下载gralde完成后,会自动使用jetty启动项目

如果想将项目导入IDE调试,eclipse用户执行

     gradlew/gradlew.bat eclipse

idea用户执行

     gradlew/gradlew.bat idea

项目启动后，访问 [http://localhost:8080/zookeeper-web][1]，显示如下
![ ][2]

------

问题和建议
==

hh.suse@gmail.com

------

作者 [@crystony]
2015-01-10

  [1]: http://localhost:8080/zookeeper-web
  [2]: ./doc/img/index.jpg

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)