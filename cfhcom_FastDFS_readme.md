# FastDFS分布式文件系统访问中台

#### 介绍
基于fastdfs-client-java再次封装，使用Json定义进行传输，将返回文件对象，易于后续操作使其更符合项目开发
官方github地址：fastdfs-client-java fastdfs-client-java: https://github.com/happyfish100/fastdfs-client-java
项目fastDfs基于docker安装，参考链接https://www.cnblogs.com/provence666/p/10987156.html
因为我使用内网搭建，所以单独搭建一个访问中台。如果在阿里云ESC公网环境下需要开通端口，按照教程能够实现。

#### 软件架构
1、fdfs_client.conf中修改tracker_server = 127.0.0.1:22122
2、maven导报失败，可以使用github上的代码进行编译，进行本地导入或者本地maven仓库导入
3、修改FastDFSUtils中的TrackerUrl地址


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)