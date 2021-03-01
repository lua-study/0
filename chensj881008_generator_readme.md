# J2EE工程开发实现代码生成工具

## SSM工程代码生成器

### master 分支为常规模式生成SSM需要的domain、dao、service和sqlmap文件

可以通过如下配置的选项来实现Lombok分支和redis分支的功能

#### 配置说明
* `config.isAutoPKs`  设置为true的话，表的主键使用UUID生成
* `config.isUseLombok`  设置为true的话，实体类生成的时候使用Lombok，项目中需要添加如下的依赖
```xml
 
     org.projectlombok 
     lombok 
     1.18.4 
 
```
* `config.isUseRedis` 设置为true的话，在Dao层使用Redis，会自动生成Redis配置文件，项目中必须添加如下的依赖和配置redis的properties

 *pom.xml*
```xml
     
         org.springframework.boot 
         spring-boot-starter-data-redis 
         
             
                 redis.clients 
                 jedis 
             
             
                 io.lettuce 
                 lettuce-core 
             
         
     
     
     
         redis.clients 
         jedis 
         
     
         org.apache.commons 
         commons-pool2 
         2.5.0 
     
```
*application.properties*
```properties
    # redis配置
    # Redis数据库索引（默认为0）
    spring.redis.database=0
    ## Redis服务器地址
    spring.redis.host=127.0.0.1
    ## Redis服务器连接端口
    spring.redis.port=6379
    ## Redis服务器连接密码（默认为空）
    spring.redis.password=123456
    ## 连接池最大连接数（使用负值表示没有限制）
    spring.redis.jedis.pool.max-active=-1
    ## 连接池最大阻塞等待时间（使用负值表示没有限制）
    spring.redis.jedis.pool.max-wait=-1
    ## 连接池中的最大空闲连接
    spring.redis.jedis.pool.max-idle=50
    ## 连接池中的最小空闲连接
    spring.redis.jedis.pool.min-idle=10
    ## 连接超时时间（毫秒）
    spring.redis.timeout=10000
```
### lombok 分支为生成内容与上述一样，只是domain没有get/set方法

增加新的依赖
```xml
     
       org.projectlombok 
       lombok 
       1.18.4 
     
```
### redis 分支为增加Redis的使用，与主分支的区别在于生成DAO层与增加Redis配置

增加新的依赖
```xml
         
         
         
             org.springframework.boot 
             spring-boot-starter-data-redis 
             
             
                 
                     redis.clients 
                     jedis 
                 
                 
                     io.lettuce 
                     lettuce-core 
                 
             
         
         
         
             redis.clients 
             jedis 
         
         
         
         
         
             org.apache.commons 
             commons-pool2 
             2.5.0 
         
```

配置application.properties 
```properties
# redis配置
# Redis数据库索引（默认为0）
spring.redis.database=0
## Redis服务器地址
spring.redis.host=127.0.0.1
## Redis服务器连接端口
spring.redis.port=6379
## Redis服务器连接密码（默认为空）
spring.redis.password=123456
## 连接池最大连接数（使用负值表示没有限制）
spring.redis.jedis.pool.max-active=-1
## 连接池最大阻塞等待时间（使用负值表示没有限制）
spring.redis.jedis.pool.max-wait=-1
## 连接池中的最大空闲连接
spring.redis.jedis.pool.max-idle=50
## 连接池中的最小空闲连接
spring.redis.jedis.pool.min-idle=10
## 连接超时时间（毫秒）
spring.redis.timeout=10000
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)