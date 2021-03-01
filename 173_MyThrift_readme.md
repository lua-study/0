#MyThrift

![输入图片说明](http://git.oschina.net/uploads/images/2016/0424/082138_3e988315_70679.png "在这里输入图片标题")


![输入图片说明](http://static.oschina.net/uploads/space/2015/0823/103926_huTM_1382024.png "在这里输入图片标题")

敬请关注！

**提出问题：**

各种存储越来越多(redis,mysql,hdfs,hbase,mq)，

让web开发人员自己访问存储，并保证性能，是一件高要求的事情。

造成的结果就是软件开发进度缓慢，性能低下，各种bug.






**分析问题：**

RPC框架：考虑到本人看过thrift的源码，尤其是针对网络模块非常熟悉，并在实际生产环境中使用过，thrift性能不错。

TCP/IP：有过2年的TCP/IP报文分析经验，从链路层到应用层都很熟悉。

ZooKeeper:在MySQL-Binlog项目中攒出了一些使用经验,同时积极吸收Motan,JACK,HArpc等兄弟软件的优秀理念部分。

连接池：使用commons-pool连接池组件。


**解决问题：**

糅合thrift,zookeeper,commons-pool打造一款轻量级、性能高、上手容易的rpc调用框架，

使得架构师和后台开发人员可以将各种复杂存储的IO访问对外暴露为服务(其实就是跨机器的普通函数调用)

这样web开发人员可以专注于业务逻辑，加速产品迭代,对企业带来的好处不用多说！




**---欢迎朋友们加入QQ群528941497 ，更欢迎提出需求！**



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)