
## ![avatar](/logo.png) Shiro-Redis

Shiro集成Redis的适配器，为解决shiro-ehcache不利于集群而打造的集中式缓存方案。

[![License](https://img.shields.io/badge/license-Apache%202-4EB1BA.svg)](https://www.apache.org/licenses/LICENSE-2.0.html)
[![Maven Central](https://img.shields.io/maven-central/v/org.iherus.shiro/shiro-redis)](https://mvnrepository.com/artifact/org.iherus.shiro/shiro-redis)


**Maven坐标**
```
 
     org.iherus.shiro 
     shiro-redis 
     2.2.0 
 
```

## 更新日志

**v2.2.0:**

**Change Log** 
1）加入scope策略.  


**v2.1.0:**

**Change Log** 
1）修复bug.  
2）增强兼容性  
3）发布[shiro-redis-spring-boot-web-starter](https://gitee.com/iherus/shiro-redis-spring-boot-web-starter)  


**v2.0.0:**

**Note**  
此版本为重构版本，API不兼容v1.x。

**Change Log** 
1）在v1.x仅支持单机模式的基础上，新增了对 哨兵（Sentinel）、集群（Cluster）模式的支持。  
2）支持Lettuce客户端、Redisson客户端  
3）兼容Spring-data-redis  
4）非集群模式，可设置独立的database  
5）支持设置缓存失效时间  
6）优化性能  
7）新增RedisSessionDAO用于降低请求Redis的频率




## Shiro-Redis使用说明

**1、基于ini的使用方式**
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
poolConfig.maxIdle=10
poolConfig.maxWaitMillis=1500
poolConfig.maxTotal=100

#定义连接配置
## Standalone
configuration=org.iherus.shiro.cache.redis.config.RedisStandaloneConfiguration
configuration.host=127.0.0.1
configuration.port=6379
configuration.database=2
#configuration.password=

## Sentinel
#configuration=org.iherus.shiro.cache.redis.config.RedisSentinelConfiguration
#configuration.masterName=mymaster
#configuration.sentinelsFromText=127.0.0.1:56379,127.0.0.1:56479,127.0.0.1:56579
#configuration.database=2
#configuration.password=

## Cluster
#configuration=org.iherus.shiro.cache.redis.config.RedisClusterConfiguration
#configuration.clusterNodesFromText=127.0.0.1:16379, 127.0.0.1:16380, 127.0.0.1:16381, 127.0.0.1:16382, 127.0.0.1:16383, 127.0.0.1:16384
#configuration.password=

#定义连接工厂
## Jedis
connectionFactory=org.iherus.shiro.cache.redis.connection.jedis.JedisConnectionFactory
connectionFactory.poolConfig=$poolConfig
connectionFactory.configuration=$configuration
#connectionFactory.clientName=
#connectionFactory.connectTimeoutMillis=
#connectionFactory.soTimeoutMillis=

## Lettuce
#connectionFactory=org.iherus.shiro.cache.redis.connection.lettuce.LettuceConnectionFactory
#connectionFactory.poolConfig=$poolConfig
#connectionFactory.configuration=$configuration
#connectionFactory.clientName=
#connectionFactory.timeoutMillis=

## Redisson
#connectionFactory=org.iherus.shiro.cache.redis.connection.redisson.RedissonConnectionFactory
#connectionFactory.configuration=$configuration
#connectionFactory.clientName=
#connectionFactory.connectTimeoutMillis=
#connectionFactory.soTimeoutMillis=

#定义缓存管理器
cacheManager=org.iherus.shiro.cache.redis.RedisCacheManager
cacheManager.connectionFactory=$connectionFactory
cacheManager.expirationMillis=900000
cacheManager.keyPrefix=shiro:test:cache:
#cacheManager.scanBatchSize=3000
#cacheManager.deleteBatchSize=5000
#cacheManager.fetchBatchSize=50
#cacheManager.database=5

#将凭证匹配器设置到realm
customRealm=org.iherus.shiro.tester.CustomRealm
customRealm.credentialsMatcher=$credentialsMatcher
securityManager.realms=$customRealm
securityManager.cacheManager=$cacheManager
```
详细测试代码请看：src/test/java/org/iherus/shiro /tester/SimpleCacheTest.java

**2、Spring集成的方式**
```
     
     
         
         
         
         
     

     
     

     
     
         
         
         
         
     

     
     
	 
     

     
     
         
     

     
     
         
         
     

     
     
         
         
         
         
         
         
         
     

     
     
	 
	 
	 
	 
	 
	  -->
	   -->
     

     
     
	 
	 
	 
	  -->
     

     
     
	 
	 
	  -->
     

     
     
	 
	 
	  -->
     

     
     
         
         
         
         
     

```

**3、关于缓存key的特别说明**

&nbsp;
&nbsp; 针对非 byte[] 和 String 类型的缓存key，采用的是生成MD5作为key的策略，这样就要求AuthorizingRealm#doGetAuthenticationInfo返回的[PrincipalCollection principals]必须是一成不变的，这样一来，如果后续需要动态修改principals的属性，则会导致缓存key的变化。 

所以，建议重写这两个方法来应对这种变化：

1）AuthorizingRealm #getAuthorizationCacheKey(PrincipalCollection principals)  
2）AuthorizingRealm #getAuthenticationCacheKey(PrincipalCollection principals)  

eg:

```
	/**
	 * 建议重写此方法，提供唯一的缓存Key
	 */
	@Override
	protected Object getAuthorizationCacheKey(PrincipalCollection principals) {
		return this.getAuthenticationCacheKey(principals);
	}

	/**
	 * 建议重写此方法，提供唯一的缓存Key
	 */
	@SuppressWarnings("unchecked")
	@Override
	protected Object getAuthenticationCacheKey(PrincipalCollection principals) {
		StringBuilder sb = new StringBuilder();
		principals.forEach(principal -> {
			sb.append(((User) principal).getId());
		});

		return sb.toString();
	}
```

更多正在补充中。。。。。 :smile:


**Features**

欢迎提出更好的意见，帮助完善 shiro-redis

**Copyright**

Apache License, Version 2.0

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)