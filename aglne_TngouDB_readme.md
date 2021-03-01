#TngouDB


### 背景

TngouDB是天狗网（[tngou.net](http://www.tngou.net)）开发的中文搜索引擎数据库，用于天狗农业网的农业搜索引擎。
天狗希望基于开源的力量，把TngouDB打造成为一个专门的中文索引NoSQL数据库。



### 简介

    TngouDB是基于JAVA而开发的跨平台数据库，底层采用Lucene（存储引擎）、IK(分词)、Netty(通信)等 而打造的网络数据库。
TngouDB直接简化的Lucene的相关API的调用，使用SQL语句实现数据的CRUD操作。



### 特点

    TngouDB可以脱离Lucene单机的现在，通过网络可以把TngouDB部署在单独的服务器上，单独处理存储于查询业务。TngouDb同
时简化的Solr的复杂性，用户可以通过简单的SQL语句进行相关的数据操作。TngouDB可以完全抛开Lucene与Solr相关的知识，用常见
的SQL语句就可以实现。



### 文档

   文档地址：[http://www.tngou.net/doc/tndb ](http://www.tngou.net/doc/tndb) 支持完整的安装、配置、使用文档。


### 使用案例

    现在TngouDB暂且是内部测试版本，请先不用用于上线的项目！我们会不断的开发与更新，后期会发布相应的正式版本。
现在TngouDB用于天狗网的搜索业务 天狗农搜（[http://www.tngou.net/search](http://www.tngou.net/search)）


### 联系

    如果对该项目感兴趣，可以加入我们，成为开源软件的贡献者。
    邮箱：tngou@tngou.net
    QQ：397713572
    联系人：陈磊 @tngou 
    联系电话：13880334484 (成都)

### 更新

**0.2版本主要改进：**


1. 数据存储引擎Lucene4更新到Lucene5。
1. 增加了并发增、删、改的功能。
1. 添加了返回状态码
1. 重构了回收链接已经关闭链接功能。


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)