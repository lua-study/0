
# spring-boot-starter-redisplus



项目spel 业务key代码参考了该项目

[spring-boot-klock-starter](http://https://gitee.com/kekingcn/spring-boot-klock-starter)



项目特点：

已实现 分布式锁

1、使用原生spring提供的 RedisTemplate 未引入第三方redis client

2、基于LUA脚本，保证了原子性，减少网络传输

3、使用spring aop 实现拦截自定义注解方法

4、自定义尝试获取锁时间、超时时间

5、支持单机/集群模式


未实现 分布式限流

计划：

1、基于IP数组限流

2、基于用户限流

3、支持springmvc




> springboot接入

1.添加starter依赖,请自行build到本地仓库。
```
 
     com.hong.redisplus 
     spring-boot-starter-redisplus 
     0.0.1-SNAPSHOT 
 

```
2.配置application.properties

单机
```
spring.redis.host=127.0.0.1
spring.redis.port=6379
```
OR

集群
```
spring.redis.cluster.nodes=127.0.0.1:6380,127.0.0.1:6381,127.0.0.1:6382,127.0.0.1:6383,127.0.0.1:6384,127.0.0.1:6385
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)