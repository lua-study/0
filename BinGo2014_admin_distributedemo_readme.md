#DistributeDemo
zookeeper ＋ dubbo ＋ spring boot

 1. zookeeper的安装与启动  
[zookeeper下载地址](http://www.apache.org/dyn/closer.cgi/zookeeper)，下载完成之后，解压，进入到"conf"目录下，新建一个"zoo.cfg"，  
内容如下：
```
tickTime=2000  
dataDir= /Users/chenqimiao/zookeeper-3.4.8/data   
dataLogDir=/Users/chenqimiao/zookeeper-3.4.8/logs    
clientPort=2181   
```
启动服务zookeeper:  
![输入图片说明](https://git.oschina.net/uploads/images/2017/0601/004347_f5ec9d77_858268.png "在这里输入图片标题")  

2.dubbo-admin的部署  

[dubbo-admin下载地址](http://github.com/alibaba/dubbo)

![输入图片说明](https://git.oschina.net/uploads/images/2017/0601/003908_c8c1cfe7_858268.png "在这里输入图片标题")

3.利用IDEA构建spring boot生产者和消费者

![输入图片说明](https://git.oschina.net/uploads/images/2017/0601/004042_95201401_858268.png "在这里输入图片标题")
![输入图片说明](https://git.oschina.net/uploads/images/2017/0601/004057_faf5c07b_858268.png "在这里输入图片标题")
![输入图片说明](https://git.oschina.net/uploads/images/2017/0601/004121_5451c0c2_858268.png "在这里输入图片标题")


感谢 [该博客](http://www.cnblogs.com/think-in-java/p/6611249.html) 提供支持！

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)