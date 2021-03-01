springBoot 多模块开发脚手架
整合
   - mybatis-plus 持久化框架 自带分页
   -  swagger 接口整理工具
   -  druid 数据库连接池
   -  logback 日志
   -  rabbitmq 消息队列
   -  redis 缓存  
    // 本来是想把 Redis.properties 文件放在spring-boot-redis resource文件里
    但是RedisProperties类只能加载Controller模块下redis.properties
    @PropertySource(value ={"classpath:redis.properties"}
  -  shiro 权限控制
  -  websocket 消息推送
  -  xxl-job 定时任务
  -  solr  搜索服务器

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)