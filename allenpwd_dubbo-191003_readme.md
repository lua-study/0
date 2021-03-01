###dubbo帮助文档
http://dubbo.apache.org/zh-cn/docs/user/quick-start.html

###dubbo监控工具
github地址：https://github.com/apache/dubbo-admin/tree/master
develop分支是前后端分离的，前端vue后端springboot
拉取代码：git clone -b master https://github.com/apache/dubbo-admin.git
####dubbo-admin使用
打包成jar：mvn clean package
直接运行jar即可
zookeeper地址配置在application.properties文件中
####dubbo-monitor-simple使用
打包成jar后assembly.bin目录会有启动脚本，运行即可
zookeeper地址配置在conf/dubbo.properties
监控平台的端口配置dubbo.jetty.port


###zookeeper相关问题
2.6以前的版本引入zkClient操作zookeeper
2.6以后的版本引入curator操作zookeeper，客户端和服务端zookeeper的jar版本不一样的话可能会报错：d
org.apache.zookeeper.KeeperException$ConnectionLossException


###不同粒度配置的覆盖关系
方法级优先，接口级次之，全局配置再次之。
如果级别一样，则消费方优先，提供方次之。
例如timeout
reference-method > service-method > reference > service > consumer > provider

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)