# spring cloud 微信商城

#### 介绍
基于spring cloud的微信商城

## docker启动
```
docker run --restart=always  -d --name nacos-standalone -e MODE=standalone -p 8848:8848 nacos/nacos-server:latest
nacos/nacos
docker run -d --restart=always --name redis -e REDIS_PASSWORD=123456 -p 6379:6379 bitnami/redis:latest

docker run -d --restart=always -p 61616:61616 -p 8161:8161 rmohr/activemq
admin/admin
docker run -d --name elasticsearch -p 9200:9200 -p 9300:9300 itzg/elasticsearch

docker run -d --link elasticsearch:elasticsearch --link rabbit:rabbit --name zipkin -e STORAGE_TYPE=elasticsearch -e ES_HOSTS=elasticsearch -e RABBIT_ADDRESSES=rabbit:5672 -p 9411:9411 openzipkin/zipkin

docker run --env MODE=standalone --name nacos-quick-start -d  -p 8848:8848  paderlol/nacos


```

#### 架构说明
my-dbpool: 手写数据库连接池
my-mybatis: 手写mybatis



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)