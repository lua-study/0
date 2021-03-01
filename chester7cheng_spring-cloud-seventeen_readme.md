# 项目介绍
基于 spring-cloud:Finchley.RELEASE, spring-boot:2.0.3.RELEASE 的 demo 项目。
## 架构图
![架构图](doc/架构图.jpg)
> ### 从上图可以看出 Spring Cloud 各个组件协作关系：
> * 其中 Eureka 负责服务的注册与发现，很好将各服务连接起来
> * Hystrix 负责监控服务之间的调用情况，连续多次失败进行熔断保护
> * Hystrix dashboard，Turbine 负责监控 Hystrix 的熔断情况，并给予图形化的展示
> * Spring Cloud Config 提供了统一的配置中心服务
> * 当配置文件发生变化的时候，Spring Cloud Bus 负责通知各服务去获取最新的配置信息
> * 所有对外的请求和服务，我们都通过 Zuul 来进行转发，起到 API 网关的作用
> * 最后我们使用 Sleuth+Zipkin 将所有的请求数据记录下来，方便我们进行后续分析
## Dubbo vs Spring Cloud
|                   | Dubbo         | Spring Cloud                  
 --------           | -----:        | ----:                        
注册中心	            | Zookeeper	    | Spring Cloud Netflix Eureka   
调用方式	            | RPC	        | REST API                      
监控	                | Dubbo-monitor | Spring Boot Admin             
断路器	            | 不完善	        | Spring Cloud Netflix Hystrix  
服务网关		        | 无	            | Spring Cloud Netflix Zuul     
分布式配置	        | 无	            | Spring Cloud Config           
服务跟踪		        | 无         	| Spring Cloud Sleuth           
消息总线		        | 无	            | Spring Cloud Bus              
数据流		        | 无	            | Spring Cloud Stream           
批量任务		        | 无	            | Spring Cloud Task             
 ……	                | ……	        | ……
## Eureka vs Consul vs Zookeeper vs Etcd
Feature	           | euerka                      | Consul	            | zookeeper	                | etcd	            
--------           | ----:                       | -----:                | -----:                    | -----:            
服务健康检查	       | 可配支持                     | 服务状态，内存，硬盘等	| (弱)长连接，keepalive	    | 连接心跳	        
多数据中心	       | —                           | 支持	                | —	                        | —	                
kv存储服务          | —                           | 支持	                | 支持	                    | 支持	            
一致性	           | —                           | raft	                | paxos	                    | raft	            
cap	               | ap                          | ca	                | cp	                    | cp	            
使用接口(多语言能力)  | http（sidecar）             | 支持http和dns	        | 客户端	                    | http/grpc	        
watch支持	       | 支持 long polling/大部分增量  | 全量/支持long polling	| 支持	                    | 支持 long polling	
自身监控	           | metrics                     | metrics	            | —	                        | metrics	        
安全	               | 	—                        | acl /https	        | acl	                    | https支持(弱)      
spring cloud集成	   | 已支持                       | 已支持	                | 已支持	                    | 已支持	           
## 服务注册/发现
- [x] Eureka
    - [x] Eureka Server 集群
    - [x] Eureka Provider 集群 
- [ ] Consul
- [ ] ~~Zookeeper~~
## 服务消费
![turbine-stream-rabbitmq](doc/turbine-stream-rabbitmq.jpg)
- [x] Feign
    - [x] Ribbon 负载均衡
        - [ ] BestAvailableRule
        - [ ] AvailabilityFilteringRule
        - [ ] WeightedResponseTimeRule
        - [ ] RetryRule
        - [x] RoundRobinRule（默认）
        - [ ] RandomRule
        - [ ] ZoneAvoidanceRule
    - [x] Hystrix 熔断降级
        - [x] 服务降级
        - [x] 依赖隔离
        - [x] 断路器
        - [x] 监控面板
        - [x] Turbine+RabbitMQ 监控数据聚合
    - [x] Feign 文件上传
## 配置中心
- [ ] ~~git~~
    - [ ] ~~Spring Cloud Bus~~
- [x] database
    - [ ] Spring Cloud Bus

## 服务网关
![spring-cloud-gateway](doc/spring-cloud-gateway.jpg)
- [x] Spring Cloud Gateway
    - [x] 路由
    - [x] 过滤器
    - [x] 限流
    - [x] 熔断
    - [x] ~~路由重试~~（不可用）
    - [x] 高可用
- [ ] ~~Zuul~~
## 链路跟踪
![spring-cloud-sleuth](doc/spring-cloud-sleuth.jpg)
![zipkin](doc/zipkin.jpg)
- [ ] Sleuth&Zipkin
    - [ ] HTTP
    - [ ] RabbitMQ
## 响应式微服务
- [ ] Spring Data Reactive
    - [ ] Flux
    - [ ] Mono
    - [ ] MongoDB
    - [ ] Redis

------
[java知识体系-20](http://naotu.baidu.com/file/ba9d75734d5ff6ee9ff81928e0d3d90a?token=b78d70dc1c612538)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)