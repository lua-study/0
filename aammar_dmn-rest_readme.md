# 决策表引擎 dmn-engine

[![Build Status](https://travis-ci.org/supermy/dmn-rest.svg?branch=master)](https://github.com/supermy/dmn-rest)

## 简介 
* 决策表引擎dmn engine；rest api 方式提供服务； 通过集群提升 QPS 能力。



## 特点
* Rest Api 方式提供服务；
* 在线发布与更新 dmn table;
* 支持 drd;

## 适用场景

1.精准获客规则定义；
2.渠道投放策略规则定义；


## 优势：

*  即开及用，在线发布维护决策模型； 

## 劣势：

*  后台由关系 DB 支撑，需要 DB 集群与 WEB 集群提升 QPS 能力    






## 快速试用
  发布 dmn table 脚本

```

mvn spring-boot:run

curl -i -X POST -H 'Cookie: JSESSIONID=kjcddrwwo1zo1ejsx4bbmek0u' -H 'Connection: keep-alive' -F "data=@/服务器文件路径/example-dmn-rest/target/classes/dmn/decision-model.dmn;tenant-id=1;deployment-source=process-application;deployment-name=abc" http://127.0.0.1:8080/rest/deployment/create

```

  执行 dmn table 脚本

```

curl -i -X POST -H 'Cookie: JSESSIONID=kjcddrwwo1zo1ejsx4bbmek0u' -H 'Connection: keep-alive ;Content-Type:application/jsons' http://127.0.0.1:8080/rest/engine/default/decision-definition/key/checkOrder/evaluate
        -d "{"variables" : 
              {"status" : { "value" : "silver", "type" : "String" },
              "sum" : { "value" : 900, "type" : "Integer" }}
              }" 

```


## 支持的 api


```
    决策表列表
    GET /decision-definition
    决策表数量
    GET /decision-definition/count
    单个决策表
    GET /decision-definition/{id} 
    单个决策表通过 key
    GET /decision-definition/key/{key} 
    租户
    GET /decision-definition/key/{key}/tenant-id/{tenant-id}
    通过 ID 获取XML格式决策表
    GET /decision-definition/{id}/xml 
    通过 KEY 获取XML 格式决策表
    GET /decision-definition/key/{key}/xml 
    获取租户
    GET /decision-definition/key/{key}/tenant-id/{tenant-id}/xml
    获取图标描述
    GET /decision-definition/{id}/diagram 
    
    GET /decision-definition/key/{key}/diagram 
    
    GET /decision-definition/key/{key}/tenant-id/{tenant-id}/diagram
    启动决策表进程
    POST /decision-definition/{id}/evaluate 
    启动决策表进程
    POST /decision-definition/key/{key}/evaluate 
    启动决策表进程
    POST /decision-definition/key/{key}/tenant-id/{tenant-id}/evaluate
    
    Update history time to live
    PUT /decision-definition/{id}/history-time-to-live 
    
    PUT /decision-definition/key/{key}/history-time-to-live 
    
    PUT /decision-definition/key/{key}/tenant-id/{tenant-id}/history-time-to-live
    
```

## 数据库配置，如测试使用，可注销数据库配置，默认使用 h2嵌入式数据库

```

    camunda.bpm:
      metrics.enabled: false
      history-level: auto
      database:
        schema-update: true
        type: mysql
    
    spring.datasource:
      url: jdbc:mysql://localhost:3306/camunda?useSSL=false
      username: camunda
      password: camunda
      driver-class-name: com.mysql.jdbc.Driver
    
    server:
      port: 8081
     
```

  
## 配合 dmn-js 实现 可视化编辑规则，进行决策表编辑，及时发布；所见及所得；

```
     
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)