# Distributor (常用分布式组件)

### 介绍 (why)
分布式技术提升了系统的运行效率，但是也产生了新的问题(如分布式锁、全局唯一序列等)

这些问题不能直接用Java原生的技术解决，但在分布式系统中却不可或缺

Distributor基于Redis实现常用的分布式组件，简单、可靠、开箱即用

### 实现功能 (what)
 1. Lock( 基于Redis的分布式锁，支持可重入锁 )
 
 2. Sequence( 序列生成器，基于雪花算法、Redis )
 
 3. Limit( 限流工具 )
 
 4. CacheClient( 缓存客户端，目前支持Redis ) 
 
 5. 敬请期待

###  如何使用 (how)
[详细的文档点这里](https://gitee.com/HappyChicken/Distributor/wikis)

初始化Distributor 
```java
    // 获得实例
    Distributor  distributor  = Distributor.getInstance();

    /* 连接配置(使用雪花算法生成序列可以不配置)
     可以根据实际情况选择不同的配置方式 */
    
    // 配置1 主机 + 端口 + 密码（如果有） + 默认连接池配置
    distributor.initJedisConfig("xxx", 6379, "");
    
    // 配置2 主机 + 端口 + 密码 + 自定义连接池配置
    distributor.initJedisConfig(String host, int port, String auth,JedisPoolConfig jedisPoolConfig)
    
    // 配置3 自定义连接池
    distributor.initJedisConfig(JedisPool jedisPool)
```

回收Distributor 
```java
    // 回收资源，在结束使用时调用
    distributor.destory();
```

Lock的使用
```java
    // 获得锁对象, 只指定了锁名
    IDtorLock lock = Distributor.newRedisLock("myLock");
    // 还可以手动指定锁的过期时间
    IDtorLock lock = Distributor.newRedisLock("myLock", 2000);
    
    /* 加锁方式有3种 */
    
    // 1. lock()方法, 直到获取锁成功为止
    String lockId = lock.lock(); 
    // 2. tryLock()方法，尝试加锁，2s内未成功返回
    String lockId = lock.tryLock(); 
    // 3. tryLock(long tryLockTime, TimeUnit unit)，尝试加锁，指定尝试时间
    String lockId = lock.tryLock(2000, TimeUnit.MILLISECONDS);
    
    // ----> 业务处理
    
    // 最后释放锁
    lock.unLock(lockId);
```

生成全局唯一序列
```java
    /* 如果使用雪花序列生成器的话，不需要初始化Redis
       直接new出来就可以用 也支持自定义工作ID和数据中心ID 
     */
    // 初始化方法1 
    ISequence sequence = Distributor.newSnowflakeSeq();
    // 初始化方法2 
    ISequence sequence = Distributor.newSnowflakeSeq(long workerId, long datacenterId);
    // 直接获取id即可
    long id = sequence.nextId();
    
    /* 如果使用Redis序列生成器的话，那么要先初始化Distributor 
       可以参照上面初始化的例子，然后new出来，就可以使用了
     */
    // 初始化方法1 只指定key
    ISequence sequence = Distributor.newRedisSeq("seq");
    // 初始化方法2 指定key 单元长度 开始位置
    ISequence sequence = 
        Distributor.newRedisSeq(String key, int step, long stepStart);
```

Limit限流
```java
    /* 由于使用了Redis，请参考初始化部分获得实例，
       并且配置Redis连接
    */
    
    // 获得限流器
    ILimit limit = Distributor.newAccessLimit();
    
    // 进行限流，如果未超过流量限制返回true，否则返回false
    // 3个参数的意义：Redis的key，单位时间内执行次数，单位时间
    limit.accessLimit("limit", 2, 1)
    
```

### 测试 (test)
测试代码可以在测试类中看到(src/test)

- #### Lock：开启20个线程，每个线程获取10次锁，运行正常无死锁
![Lock测试图](./img/Lock测试图.png "屏幕截图.png")

- #### Sequence: 
##### 1. 利用雪花算法生成序列，10W个大概需要0.9秒
![雪花算法测试图腾](./img/Snowflake算法测试图.png "屏幕截图.png")
##### 2. 利用Redis生成序列，连接远程Redis服务，生成10W个序列大概需要1.1秒
![Redis序列测试图腾](./img/Redis序列测试图.png "屏幕截图.png")

### 友情链接 (friends)
 + [水不要鱼 & 码云](https://gitee.com/FishGoddess)

 + [Mackyhuang & 码云](https://gitee.com/Mackyhuang)

 + [MaDao & 码云](https://gitee.com/mdaovo)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)