# DelayQueue延迟消息队列

#### 介绍

架构：

SpringCloud-Stream + RocketMQ + RocksDB/LevelDB (可以使用Nacos，Eureka作为注册中心,作为单独的延迟消息服务使用)


基于Apache RocketMQ的一种延迟消息队列。

由于Apache RocketMQ不支持自定义延迟消息队列，为了支持延时消息队列特开此项目进行对Apache RocketMQ进行补充。以至于达到可以实现自定义延迟的一种方式。

相关Apache RocketMQ消息队列：

TOPIC_SYSTEM_QUEUE_REALTIME: 实时消息队列（当消息到期后，此队列消息增加1个）

TOPIC_SYSTEM_QUEUE_DELAY: 延迟队列（用于接收延迟消息请求）

![OpenDelayQueue 调用流程](https://files.gitee.com/group1/M00/0E/05/wKgCNF67SJKAAjnjAABE3rx8uRc074.svg?disposition=inline "在这里输入图片标题")


#### 1.0.0支持功能项：

1、支持水平扩展DelayServer

2、支持自定义延迟消息，可以精确到毫秒级。

#### 请求过程：

1、应用调用请求 

2、发起延时消息 

3、应用方将消息写入 TOPIC_SYSTEM_QUEUE_DELAY  

4、延时服务方监听TOPIC_SYSTEM_QUEUE_DELAY 将消息读取出来写入RocksDB 

5、延时服务方循环遍历RocksDB检测延时消息是否需要发送 

6、如果需要发送则将消息放入TOPIC_SYSTEM_QUEUE_REALTIME

7、应用监听TOPIC_SYSTEM_QUEUE_REALTIME 进行业务操作。
  
#### 如何扩展？

完全沿袭Apache RocketMQ高可用、高性能、低延迟、高可靠的优点，如果RocketMQ性能不够，则增加RocketMQ Broker节点。

如果是消息消费性能不够，则将此服务复制一份，消费组配置成TOPIC_SYSTEM_QUEUE_DELAY 同一个即可。

当然可以改造成Eureka服务，或者Nacos服务，使其Restful也支持高可用。

![OpenDelayQueue 高可用](https://files.gitee.com/group1/M00/0E/06/wKgCNF67S42AAsxtAAApiCfLBrU859.svg?disposition=inline "在这里输入图片标题")


#### 如何调用

提供2种模式，一种是Restful接口，一种是SpringCloudStream

##### Restful接口模式：

GET 1.1 http://delay-server:port/send/message

参数：

key ： 唯一ID

delayTime : 延迟发送的时间

content ： 消息内容

例子：

GET 1.1 http://delay-server:port/send/message?key=1&delayTime=2020-05-11 17:43:00&content=消息内容

##### SpringCloudStream模式

配置消息生产通道Topic, Topic TOPIC_SYSTEM_QUEUE_DELAY


```
spring:
  cloud:
    stream:
      rocketmq:
        binder:
          #新版使用该地址
          name-server: rocketmq-server:9876
      bindings:
        #发送通道
        system_topic_queue_realtime_output:
          #目的地：主题（Topic）
          destination: TOPIC_SYSTEM_QUEUE_REALTIME
        #发送通道
        system_topic_queue_delay_output:
          #目的地：主题（Topic）
          destination: TOPIC_SYSTEM_QUEUE_DELAY
        #接收通道
        system_topic_queue_delay_input:
          #目的地：主题（Topic）
          destination: TOPIC_SYSTEM_QUEUE_DELAY
          #MessageConvert 类型， JSON协议
          content-type: application/json
          #消费组
          group: TOPIC_SYSTEM_QUEUE_DELAY_GROUP
  application:
    name: omuao-delay-queue
  jackson:
    date-format: yyyy-MM-dd HH:mm:ss
    time-zone: GMT+8
    default-property-inclusion: non_null
  mvc:
    date-format: yyyy-MM-dd HH:mm:ss
  servlet:
    multipart:
      max-file-size: 10MB
      max-request-size: 10MB
```









 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)