# Spring cloud 负载均衡

#### Spring Cloud 负载均衡
## 服务失效的处理方案
### 服务注册中心剔除
+ server 
```
eureka:
  instance:
    hostname: localhost
  client:
    registerWithEureka: false
    fetchRegistry: false
    serviceUrl:
      defaultZone: http://${eureka.instance.hostname}:${server.port}/eureka/
  server:
    # 关闭保护机制，默认true
    enable-self-preservation: false
    # 剔除失效服务间隔，默认60000
    eviction-interval-timer-in-ms: 3000
  
````
+ client 

```
   eureka:
  instance:
    prefer-ip-address: true
    #Eureka客户端向服务端发送心跳的时间间隔，单位为秒（客户端告诉服务端自己会按照该规则），默认30
    lease-renewal-interval-in-seconds: 5
    #Eureka服务端在收到最后一次心跳之后等待的时间上限，单位为秒，超过则剔除（客户端告诉服务端按照此规则等待自己），默认90
    lease-expiration-duration-in-seconds: 7
  client:
    registry-fetch-interval-seconds: 5 #eureka client刷新本地缓存时间，默认30
    serviceUrl:
      defaultZone: http://localhost:8761/eureka/ 
 
```


### 负载均衡剔除服务

 +  AvailabilityFilteringRule

```
    RoundRobinRule(轮询算法)
    
    RandomRule(随机算法)
    
    AvailabilityFilteringRule()：会先过滤由于多次访问故障而处于断路器跳闸状态的服务，还有并发的连接数量超过阈值的服务，然后对剩余的服务列表按照轮询策略进行访问
    
    WeightedResponseTimeRule()：根据平均响应的时间计算所有服务的权重，响应时间越快服务权重越大被选中的概率越高，刚启动时如果统计信息不足，则使用RoundRobinRule策略，等统计信息足够会切换到WeightedResponseTimeRule
    
    RetryRule()：先按照RoundRobinRule的策略获取服务，如果获取失败则在制定时间内进行重试，获取可用的服务。
    
    BestAviableRule()：会先过滤掉由于多次访问故障而处于断路器跳闸状态的服务，然后选择一个并发量最小的服务
    
    ZoneAvoidanceRule()：默认规则，符合判断server所在区域的性能和server的可用性选择服务器 

```

### 服务注册中心剔除 与  负载均衡剔除服务 区别

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)