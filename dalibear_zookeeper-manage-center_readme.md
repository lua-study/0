#zookeeper-manage-center

本开源项目是采用java语言，基于spring boot进行开发的，依赖maven，mysql数据库

安装方法：
1、安装 zk服务器
2、安装maven
3、安装mysql数据库
4、在src/main/resourses/sql下面有用于创建数据库表的脚本，初始化三条数据，zk服务器的三个集群节点
5、在src/main/resourses/application.properties里面修改数据库链接信息，修改zk服务器集群的连接地址信息
6、使用spring boot的方式启动系统
7、切换到server管理节点，修改记录所对应的zk服务器集群节点所在主机地址，端口，配置文件所在地址，然后启动服务器即可。

也可以在外部使用zk脚本直接启动服务器，就不用在系统中进行启动了。
需要注意的是，如果在系统中启动zk服务器，那么在系统管理时，zk服务器也会停止。
![输入图片说明](http://git.oschina.net/uploads/images/2017/0212/125050_66cd500e_118656.png "在这里输入图片标题")
![输入图片说明](http://git.oschina.net/uploads/images/2017/0212/125109_a82a4ae4_118656.png "在这里输入图片标题")
![输入图片说明](http://git.oschina.net/uploads/images/2017/0212/125127_30aa2f80_118656.png "在这里输入图片标题")
![输入图片说明](http://git.oschina.net/uploads/images/2017/0212/125140_bcd78ead_118656.png "在这里输入图片标题")

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)