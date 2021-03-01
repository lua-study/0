[TOC]

# public-comment

#### 介绍

##### dianping-comment

[后台管理界面](http://localhost:8010/admin/seller/index)
[c端访问地址](http://localhost:8010/static/index.html)

##### csv-imports

数据导入工具类
tmdb_5000_movies.csv 整理好的用于测试的数据

- [https://www.themoviedb.org](https://www.themoviedb.org)
- [https://www.kaggle.com/tmdb/tmdb-movie-metadata](https://www.kaggle.com/tmdb/tmdb-movie-metadata)

##### es-kibana-config
v 7.3.0
es cluster + kibana
[canal](https://github.com/alibaba/canal)

#### 项目启动方式

#### canal 的下载，安装及使用

##### 下载

- [canal官方github](git@github.com:alibaba/canal.git)
- 文档参阅地址
    1. [https://github.com/alibaba/canal/wiki/QuickStart](https://github.com/alibaba/canal/wiki/QuickStart)
    2. [https://github.com/alibaba/canal/wiki/ClientExample](https://github.com/alibaba/canal/wiki/ClientExample)


##### 安装及使用

###### 概述
canal-deployer 相当于 server，
canal-adapter 相当于 client，
server 将自己伪装成一个 mysql slave，将变化通过消息组件（如：kafaka，RocketMQ等）
发送给 client，client接收后再做处理。（详细内容可以参阅官方文档）

对应 canal-adapter 的两种使用方式

0. 前置设置，[参考](https://github.com/alibaba/canal/wiki/QuickStart)

- 本项目mysql使用8.0,配置如下，可以使用修改后的编译好的包
```

# 下载地址
https://github.com/Auzqy/canal/archive/canal-for-mysql8-au.zip

# 打包命令
解压后，进入目录，执行 mvn clean package -DskipTests

# 项目位置
## canal-deployer
./deployer/target/canal
## canal-adapter
./client-adapter/launcher/target/canal-adapter


或者直接下载 1.1.4 版本，然后将数据库的驱动替换为数据库对应的版本
```
- canal-deployer/conf/instance.properties

```
# 设置成与 mysql master server_id 不同的值
# 不过，对于这行内容该配置文件的注释，au 认为好像不设置也可以，不过我实际没有测试
canal.instance.mysql.slaveId=123

# 检查下述内容是否与自己的设置相符合，不符合的话则修改
canal.instance.master.address=127.0.0.1:3306

canal.instance.dbUsername=canal
canal.instance.dbPassword=canal

# 其余配置默认就可以
```

如果启动报错，提示连接错误，提示`caching_sha2_password`即密码验证的问题的话，修改登录用户解密方式
```
# 修改加密方式
ALTER USER 'canal'@'%' IDENTIFIED WITH mysql_native_password BY 'canal';

# 刷新
FLUSH PRIVILEGES;
```

1. 只使用官方提供的 canal-adapter，来完成自己的业务，
[具体参考,直接使用canal.example工程](https://github.com/alibaba/canal/wiki/ClientExample)，
本项目做法简要如下：
- 1.1 配置 canal-adapter/conf/application.yml
```
server:
  port: 8081
spring:
  jackson:
    date-format: yyyy-MM-dd HH:mm:ss
    time-zone: GMT+8
    default-property-inclusion: non_null

canal.conf:
  mode: tcp # kafka rocketMQ
  canalServerHost: 127.0.0.1:11111
#  zookeeperHosts: slave1:2181
#  mqServers: 127.0.0.1:9092 #or rocketmq
#  flatMessage: true
  batchSize: 500
  syncBatchSize: 1000
  retries: 0
  timeout:
  accessKey:
  secretKey:
  srcDataSources:
    defaultDS:
      url: jdbc:mysql://127.0.0.1:3306/dianpingdb?useUnicode=true&characterEncoding=UTF-8&useSSL=false
      username: canal
      password: canal
  canalAdapters:
  - instance: example # canal instance Name or mq topic name
    groups:
    - groupId: g1
      outerAdapters:
      - name: logger
#      - name: rdb
#        key: mysql1
#        properties:
#          jdbc.driverClassName: com.mysql.jdbc.Driver
#          jdbc.url: jdbc:mysql://127.0.0.1:3306/mytest2?useUnicode=true
#          jdbc.username: root
#          jdbc.password: 121212
#      - name: rdb
#        key: oracle1
#        properties:
#          jdbc.driverClassName: oracle.jdbc.OracleDriver
#          jdbc.url: jdbc:oracle:thin:@localhost:49161:XE
#          jdbc.username: mytest
#          jdbc.password: m121212
#      - name: rdb
#        key: postgres1
#        properties:
#          jdbc.driverClassName: org.postgresql.Driver
#          jdbc.url: jdbc:postgresql://localhost:5432/postgres
#          jdbc.username: postgres
#          jdbc.password: 121212
#          threads: 1
#          commitSize: 3000
#      - name: hbase
#        properties:
#          hbase.zookeeper.quorum: 127.0.0.1
#          hbase.zookeeper.property.clientPort: 2181
#          zookeeper.znode.parent: /hbase
      - name: es
        hosts: 127.0.0.1:9300 # 127.0.0.1:9200 for rest mode
        properties:
#          mode: transport # or rest
#          # security.auth: test:123456 #  only used for rest mode
          cluster.name: dianping
```

- 1.2 添加 canal-adapter/conf/shop.yml
```
dataSourceKey: defaultDS
destination: example
groupId: 
esMapping:
  _index: shop
  _type: _doc
  _id: id
  upsert: true
  sql: "select a.id,a.name,a.tags,concat(a.latitude,',',a.longitude) as location,a.remark_score,a.price_per_man,a.category_id,b.name as category_name,a.seller_id,c.remark_score as seller_remark_score, c.disabled_flag as seller_disabled_flag from shop a inner join category b on a.category_id = b.id inner join seller c on c.id = a.seller_id"
  commitBatch: 3000
```

`mysql的驱动包如果应该与数据库版本一致`

2. 引入 canal-adapter 相关依赖，实现定制化需求（本项目采用这种），
[具体参考,从头创建工程](https://github.com/alibaba/canal/wiki/ClientExample)，
本项目做法简要如下：

- 2.1 引入 maven 依赖
```
 
     1.1.4 
 
    
 
     com.alibaba.otter 
     canal.client 
     ${canal.version} 
 
 
     com.alibaba.otter 
     canal.common 
     ${canal.version} 
 
 
     com.alibaba.otter 
     canal.protocol 
     ${canal.version} 
 
```

- 2.2 相关的类
```
# 参见本项目 dianping-comment 模块中的如下类：
top.auzqy.comment.canal.CanalClient
top.auzqy.comment.canal.CanalScheduling
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)