**shiro-redis**

shiro集成redis的适配器，为解决shiro-ehcache不利于集群而打造的缓存集群方案。

**Maven坐标**
```
 
     org.iherus.shiro 
     shiro-redis 
     1.1.0 
 
```
**shiro-redis使用说明**

1、基于ini的使用方式
```
    [main]
    #定义凭证匹配器
    credentialsMatcher=org.apache.shiro.authc.credential.HashedCredentialsMatcher
    #散列算法
    credentialsMatcher.hashAlgorithmName=MD5
    #散列次数
    credentialsMatcher.hashIterations=2

    #定义缓存池配置
    poolConfig=redis.clients.jedis.JedisPoolConfig
    poolConfig.minIdle=3
    poolConfig.maxIdle=20
    poolConfig.maxWaitMillis=1000
    poolConfig.maxTotal=300
    #定义缓存配置工厂
    configFactory=org.iherus.shiro.cache.redis.RedisCacheConfigFactory
    configFactory.poolConfig=$poolConfig
    #定义缓存管理器
    cacheManager=org.iherus.shiro.cache.redis.RedisCacheManager
    cacheManager.configFactory=$configFactory

    #将凭证匹配器设置到realm
    customRealm=org.iherus.shiro.tester.CustomRealm
    customRealm.credentialsMatcher=$credentialsMatcher
    securityManager.realms=$customRealm
    securityManager.cacheManager=$cacheManager
```
详细测试代码请看：src/test/java/org/iherus/shiro /tester/SimpleCacheTest.java

2、Shiro+Spring集成的方式
```
     
     
         
         
         
         
     
     
     
     
     
         
         
         
         
     
     
     
	 
     
     
     
         
     
     
     
         
         
     
     
     
         
     
     
     
         
         
         
         
         
     
     
     
         
         
         
         
     
```

更多正在补充中。。。。。 :smile:


**Features**

欢迎提出更好的意见，帮助完善 shiro-redis

**Copyright**

Apache License, Version 2.0

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)