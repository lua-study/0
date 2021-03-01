# com.abcijkxyz.mybatis-boot

参考mybatis-spring-boot-samples

	https://github.com/mybatis/spring-boot-starter/mybatis-spring-boot-samples

技术预研mybatis-spring-boot

spring boot + mybatis boot 

包含:

    h2、mysql数据库用例

    mybatis xml + annotation两种混合实现方式

    logging日志级别

application.properties

```

# H2
#spring.datasource.schema=classpath:import.sql

# MySQL
spring.datasource.url=jdbc:mysql://localhost:3306/test?useUnicode=true&characterEncoding=utf8&characterSetResults=utf8&autoReconnect=true&autoReconnectForPools=true&rewriteBatchedStatements=true&zeroDateTimeBehavior=convertToNull&useSSL=false
spring.datasource.username=root
spring.datasource.password=
spring.datasource.driver-class-name=com.mysql.jdbc.Driver


#mybatis.config-location=classpath:mybatis-config.xml

# 没有MyBatis配置文件
mybatis.type-aliases-package=com.abcijkxyz.domain
mybatis.mapper-locations=classpath*:com/abcijkxyz/mapper/*Mapper.xml


#日志级别：TRACE<DEBUG<INFO<WARN<ERROR<FATAL
logging.level.root=WARN
logging.level.com.abcijkxyz.mapper=TRACE

```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)