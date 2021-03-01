# ace-cache
基于spring boot上的注解缓存，自带轻量级缓存管理页面。 
@Cache比spring cache更轻量的缓存，支持单个缓存设置过期时间，可以根据前缀移除缓存。 
采用fastjson序列化与反序列化，以json串存于缓存之中。 
ace-cache可以快速用于日常的spring boot应用之中。 

# 使用手册
## Maven依赖
```
 
     com.github.wxiaoqi 
     ace-cache 
     0.0.2 
 
```
## 缓存配置
1、配置redis数据源，application.yml文件
```
#redis-cache 相关
redis:
    pool:
         maxActive: 300
         maxIdle: 100
         maxWait: 1000
    host: 127.0.0.1
    port: 6379
    password:
    timeout: 2000
    # 服务或应用名
    sysName: ace
    enable: true
    database: 0
```
## 缓存开启
2、开启AOP扫描
```
@EnableAceCache
```
## 缓存使用
3、在Service上进行@Cache注解或@CacheClear注解
# 注解说明
## 配置缓存：@Cache
 注解参数 | 类型  | 说明
 -------------  |------------- | -----
 key  | 字符串                                | 缓存表达式，动态运算出key 
 expires        | 整形            |    缓存时长，单位：分钟 
 desc           | 描述            |   缓存说明              
 parser         | Class  |  缓存返回结果自定义处理类 
 generator      | Class  |  缓存键值自定义生成类 
## 清除缓存：@CacheClear
注解参数 | 类型  | 说明
 -------------  |------------- | -----
 pre	|字符串 |	清除某些前缀key缓存
key |	字符串 |	清除某个key缓存
keys |	字符串数组 |	清除某些前缀key缓存
generator      | Class  |  缓存键值自定义生成类 
## 默认key动态表达式说明
表达式举例 | 说明 | 举例
-------------  |------------- | -----
@Cache(key="user:{1}") public User getUserByAccount(String account) | {1}表示获取第一个参数值 {2}表示获取第二个参数值 ……依此类推 | 若：account = ace，则：key = user:ace
@CacheClear(pre="user{1.account}") User saveOrUpdate(User user)|{1}表示获取第一个参数值 {1.xx}表示获取第一个参数中的xxx属性|若：account=ace，则：key = user:ace
# 轻量管理端
访问地址：http://localhost:8080/cache
 管理端批量或前缀清除ace-cache注册的缓存，同时也可以快速预览缓存的数据内容，也可以对缓存的失效时间进行延长。
![img](http://ofsc32t59.bkt.clouddn.com/17-05-22/1495418425204.jpg)
# Demo
1、在src/main/test中展开的相关示例代码
>CacheTest是核心启动类
>>service包是缓存调用例子，包含自定义表达式和结果解析、注解的使用

# 2017年5月22日 
初次与大家见面，请多多指教！

# 2017年5月23日 兼容spring mvc模式

## 配置文文件
##### application.properties
```
redis.pool.maxActive = 300
redis.pool.maxIdle = 100
redis.pool.maxWait = 1000
redis.host = 127.0.0.1
redis.port = 6379
redis.password = 
redis.timeout = 2000
redis.database = 0
redis.sysName = ace
redis.enable = true
```
##### applicationContext.xml
```
 
xmlns:aop="http://www.springframework.org/schema/aop"
xmlns:context="http://www.springframework.org/schema/context"
xsi:schemaLocation="
	http://www.springframework.org/schema/aop http://www.springframework.org/schema/aop/spring-aop-3.1.xsd
	http://www.springframework.org/schema/context  
	http://www.springframework.org/schema/context/spring-context-3.0.xsd"	
 	
  
 
  
```
##### maven依赖
```
 
     
     4.1.3.RELEASE 
 
 
     
    	 org.springframework 
    	 spring-core 
    	 ${spring.version} 
     
     
    	 org.springframework 
    	 spring-beans 
    	 ${spring.version} 
     
     
    	 org.springframework 
    	 spring-context 
    	 ${spring.version} 
     
     
    	 org.springframework 
    	 spring-context-support 
    	 ${spring.version} 
     
     
    	 org.springframework 
    	 spring-aspects 
    	 ${spring.version} 
     
     
    	 org.springframework 
    	 spring-webmvc 
    	 ${spring.version} 
     
     
    	 org.aspectj 
    	 aspectjrt 
    	 ${aspectj.version} 
     
 
```
## 使用方式
使用方式与spring boot的方式一样，在方法上直接注解即可。


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)