# redis-util

#### 介绍
老项目专用redis工具

整合RedisTemplate与StringRedisTemplate，提供更友好的API，更方便的调用，让redis小白也可以轻松操作redis

#### 软件架构
依赖spring-data-redis 1.5.2.RELEASE版本，兼容spring 4.0

#### 安装教程

```
 
     wiki.xsx 
     redis-util 
     1.0.0 
 
```

#### 文档地址
https://apidoc.gitee.com/xsxgit/redis-util

#### 使用说明
快速开始

方式一：
```
 
```

方式二：
```
@Bean
public RedisAutoConfiguration redisAutoConfiguration(){
    return new RedisAutoConfiguration();
}
```

默认配置(redis.properties)：
```
#info基础配置
redis.database=0
redis.url=
redis.host=localhost
redis.port=6379
redis.password=
redis.timeout=1000
redis.ssl=false


#pool连接池配置
#redis.pool.usePool=true
#redis.pool.jedisConfig=false
#redis.pool.lettuceConfig=true
#redis.pool.maxIdle=8
#redis.pool.minIdle=0
#redis.pool.maxActive=8
#redis.pool.maxWait=-1
#redis.pool.shutdownTimeout=100


#sentinel哨兵配置
redis.sentinel.master=
redis.sentinel.nodes=


#cluster集群配置
redis.cluster.maxRedirects=
redis.cluster.nodes=
```


调用 wiki.xsx.core.util.RedisUtil.getXXXHandler 方法获取对应类型实例

1.  getStringTypeHandler：获取字符串类型实例(String)
2.  getHashTypeHandler： 获取哈希类型实例(Hash)
3.  getListTypeHandler： 获取列表类型实例(List)
4.  getSetTypeHandler：获取无序集合类型实例(Set)
5.  getZsetTypeHandler：获取有序集合类型实例(Zset)
6.  getHyperLogLogTypeHandler：获取基数类型实例(HyperLogLog)
7.  getBitmapHandler：获取位图类型实例(Bitmap)
8.  getDBHandler： 获取数据库实例(db)
9. getKeyHandler： 获取键实例(key)


**特别说明：XXXAsObj为对象类型序列化相关方法，XXX为字符串类型序列化相关方法**

@since 为redis版本所支持的方法，例如@since redis 1.0.0表示1.0.0的redis版本即可使用该方法

#### spring-boot版本
https://gitee.com/xsxgit/spring-boot-starter-fast-redis

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)