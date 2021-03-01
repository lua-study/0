# logging-appender
##logback
###redis
-- pom.xml添加依赖
```xml
     
         org.redisson 
         redisson 
         3.2.3 
     
     
         net.myscloud.plugin 
         logging-appender 
         1.0-SNAPSHOT 
     
```
-- logback.xml添加Appender
```xml
     
         
             
                 10.2.81.93:6379 
             
         
         test-application 
         test 
         redis-log 
         test 
     
```

-- 日志格式
```json
    {
        "@timestamp": "2017-01-17T10:40:53.129+0800",
        "host": "10.2.85.49",
        "level": "WARN",
        "logger": "net.myscloud.plugin.logging.logback.redis.appender.LogbackRedisAppenderTest",
        "message": "test87",
        "source": "test-application",
        "thread": "main"
    }
```

-- https://www.elastic.co/guide/en/logstash/current/plugins-inputs-redis.html#plugins-inputs-redis

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)