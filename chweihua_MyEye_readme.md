#MyEye

公司内部接入了64个产品，每天写入HBase数据量(100G/天).水平扩展就可以支持日TB级数据量。
上线12个月非常稳定！

#官方QQ群: 120734278 

### 技术选型如下：(其中MyThrift请参考本人的另外一个RPC服务框架MyThrift.)
==================配置信息======================================
前端:JQuery EasyUI(1.5) + Bootstrap 

Web容器：Tomcat(9.0.0) + SpringMVC(4.3.0)

RPC: MyThrift(0.4.9,内置Thrift版本0.9.3) + ZK(3.4.6)

配置信息存储: Dbutils(1.6) + Druid(1.0.27) + mysql-connector-java (5.1.39) + MySQL

==================监控数据上报===================================

Java语言上报客户端 自研 + Metrics(3.0.2)     VS     非Java语言上报: Netty(4.0.36) + UDP +QUIC

Web容器: Netty(4.0.36)

RPC: MyThrift(0.4.9) + ZK(3.4.6)

大数据存储: HBase-client(1.2.4)|AsyncHBase(1.7.2未用)|Phoenix(未用)  +  HBase(1.1.2)  + Redis(存储加速)  
           ---  ( 大数据安装: Ambari[2.2.2] )

消息队列:Redis/Kafka

=================监控数据实时分析================================

实时分析:Storm/Flink/Heron (主要使用storm,后续考虑支持Flink&Heron)

=================调用链分析======================================

调用链分析:Zipkin/brave + Pinpoint

=================界面小样Demo====================================
后台配置界面如下：
![输入图片说明](http://git.oschina.net/uploads/images/2016/1223/223111_9e43779b_70679.png "在这里输入图片标题")
![输入图片说明](http://git.oschina.net/uploads/images/2016/1223/223500_ca8e9931_70679.png "在这里输入图片标题")

=================客户端client_metrics采集结果demo=================
![输入图片说明](http://git.oschina.net/uploads/images/2016/1228/152058_0b9854be_70679.png "在这里输入图片标题")
![输入图片说明](http://git.oschina.net/uploads/images/2016/1228/152110_06fe7a60_70679.png "在这里输入图片标题")

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)