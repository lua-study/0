# spring-cloud-demo

#### 介绍
This project is quick-start spring cloud project. Based on Spring Cloud Finchley(2.0.X)
Cover 
- Spring Cloud Config
- Spring Cloud Netflix
- Spring Cloud Bus
- Spring Cloud OpenFeign
- Spring Cloud Hystrix
- Spring Cloud Zuul

## Cloud-Server 8761

```
@SpringBootApplication
@EnableEurekaServer

spring:
  application:
    name: eureka-server
eureka:
  instance:
    hostname: localhost
  client:
    serviceUrl:
      defaultZone: http://${eureka.instance.hostname}:${server.port}/eureka/
    registerWithEureka: false
    fetchRegistry: false

netflix-eureka-server
```

## Config-Server 8030

```
@SpringBootApplication
@EnableEurekaClient
@EnableConfigServer
@EnableDiscoveryClient

spring:
  application:
    name: config-server
eureka:
  client:
    serviceUrl:
      defaultZone: http://localhost:8761/eureka/
  cloud:
    config:
      label: master
      server:
        git:
          uri: https://gitee.com/cyzink/config
          searchPaths: respo

config-server
```

## Data-Service 8001
 
```
@SpringBootApplication
@EnableEurekaClient

spring:
  application:
    name: product-data-service
eureka:
  client:
    serviceUrl:
      defaultZone: http://localhost:8761/eureka/


```

## View-Service-Feign 8012

```
@SpringBootApplication
@EnableEurekaClient
@EnableDiscoveryClient
@EnableFeignClients
@EnableCircuitBreaker

feign.hystrix.enabled: true
spring:
  application:
    name: product-view-service-feign
  cloud:
    config:
      label: master
      profile: dev
      discovery:
        enabled:  true
        serviceId:  config-server
  client:
    serviceUrl:
      defaultZone:  http://localhost:8761/eureka/
rabbitmq:
  host: localhost
  port: 5672
  username: guest
  password: guest

management:
  endpoints:
    web:
      exposure:
        include: "*"
      cors:
        allowed-origins: "*"
        allowed-methods: "*"

openfeign, config, actuator, bus-amqp, netflix-hystrix, 
```

## Zuul 8040

```
@SpringBootApplication
@EnableZuulProxy
@EnableEurekaClient
@EnableDiscoveryClient

eureka:
  client:
    serviceUrl:
      defaultZone: http://localhost:8761/eureka/
spring:
  application:
    name: product-service-zuul

zuul:
  routes:
    api-a:
      path: /api-data/**
      serviceId: PRODUCT-DATA-SERVICE
    api-b:
      path: /api-view/**
      serviceId: PRODUCT-VIEW-SERVICE-FEIGN

netflix-zuul
```

## Dashboard

```
@SpringBootApplication
@EnableHystrixDashboard

spring:
  application:
    name: hystrix-dashboard

actuaor, netflix-hystrix, netflix-hystrix-dashboard 
```

## Turbine 8021


```
@SpringBootApplication
@EnableTurbine

spring.application.name: turbine
turbine:
  aggregator:
    clusterConfig: default
  appConfig: product-view-service-feign
  clusterNameExpression: new String("default")

eureka:
  client:
    serviceUrl:
      defaultZone: http://localhost:8761/eureka/

actuaor, netflix-hystrix, netflix-hystrix-dashboard, netflix-turbine
```



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)