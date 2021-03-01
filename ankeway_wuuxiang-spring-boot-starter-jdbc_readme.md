# wuuxiang-spring-boot-starter-jdbc

> 吾享移动WEB组定制使用JDBC数据源连接方式，封装DAO模块，自动配置Starter
> 基于SpringBoot2.0Release版本的JDBCDao，支持o2o,crm,o2oread,crmread多数据源，对接druid1.1.8版本，并基于druid-spring-boot-starter 1.1.8版本开发

> https://github.com/alibaba/druid/tree/master/druid-spring-boot-starter


> 配置参数与druid-spring-boot-starter的参数配置相同

> 使用时POM.xml中增加依赖
>  
> 	 com.wuuxiang 
> 	 wuuxiang-spring-boot-starter-jdbc 
> 	 0.0.1 
>  

#多数据源配置方式
### 单用某一个数据源，可直接配置
> spring.profiles.active=o2o
> spring.profiles.active=crm
### 同时使用多个数据源，可直接配置
> spring.profiles.active=o2o,crm,o2oread
> 由于业务需要目前只支持  o2o,crm,o2oread三个数据源


#JDBC 配置（对应数据源o2o示例，此部分为必填项）
> spring.datasource.druid.o2o.url=
> spring.datasource.druid.o2o.username=
> spring.datasource.druid.o2o.password=
> spring.datasource.druid.o2o.driver-class-name=

> spring.datasource.druid.crm.url=
> spring.datasource.druid.crm.username=
> spring.datasource.druid.crm.password=
> spring.datasource.druid.crm.driver-class-name=

> spring.datasource.druid.o2oread.url=
> spring.datasource.druid.o2oread.username=
> spring.datasource.druid.o2oread.password=
> spring.datasource.druid.o2oread.driver-class-name=

> 以下示例中 X--对应 的o2o,crm,o2oread

#连接池配置(强烈注意：由于Spring Boot 2.X的版本不再支持配置继承，多数据源的话每个数据源都需要单独配置，否则配置不会生效)
### 初始化大小，最小，最大
> spring.datasource.druid.X.initial-size=1
> spring.datasource.druid.X.min-idle=1
> spring.datasource.druid.X.max-active=10

### 配置获取连接等待超时的时间
> spring.datasource.druid.X.max-wait=60000
> spring.datasource.druid.X.pool-prepared-statements=true
> spring.datasource.druid.X.max-pool-prepared-statement-per-connection-size=20
> spring.datasource.druid.X.max-open-prepared-statements= 20 #和上面的等价
> spring.datasource.druid.X.validation-query=SELECT 1 FROM DUAL
> spring.datasource.druid.X.validation-query-timeout= 20
> spring.datasource.druid.X.test-on-borrow=false
> spring.datasource.druid.X.test-on-return=false
> spring.datasource.druid.X.test-while-idle=true
### 配置间隔多久才进行一次检测，检测需要关闭的空闲连接，单位是毫秒
> spring.datasource.druid.X.time-between-eviction-runs-millis=60000
### 配置一个连接在池中最小生存的时间，单位是毫秒
> spring.datasource.druid.X.min-evictable-idle-time-millis=30000
> spring.datasource.druid.X.max-evictable-idle-time-millis=60000
> spring.datasource.druid.X.filters= stat,wall,log4j #配置多个英文逗号分隔

#监控配置
### WebStatFilter配置，说明请参考Druid Wiki，配置_配置WebStatFilter
> spring.datasource.druid.X.web-stat-filter.enabled= #是否启用StatFilter默认值true
> spring.datasource.druid.X.web-stat-filter.url-pattern=
> spring.datasource.druid.X.web-stat-filter.exclusions=
> spring.datasource.druid.X.web-stat-filter.session-stat-enable=
> spring.datasource.druid.X.web-stat-filter.session-stat-max-count=
> spring.datasource.druid.X.web-stat-filter.principal-session-name=
> spring.datasource.druid.X.web-stat-filter.principal-cookie-name=
> spring.datasource.druid.X.web-stat-filter.profile-enable=

### StatViewServlet配置，说明请参考Druid Wiki，配置_StatViewServlet配置
> spring.datasource.druid.X.stat-view-servlet.enabled= #是否启用StatViewServlet默认值true
> spring.datasource.druid.X.stat-view-servlet.url-pattern=
> spring.datasource.druid.X.stat-view-servlet.reset-enable=
> spring.datasource.druid.X.stat-view-servlet.login-username=
> spring.datasource.druid.X.stat-view-servlet.login-password=
> spring.datasource.druid.X.stat-view-servlet.allow=
> spring.datasource.druid.X.stat-view-servlet.deny=

### Spring监控配置，说明请参考Druid Github Wiki，配置_Druid和Spring关联监控配置
> spring.datasource.druid.X.aop-patterns= # Spring监控AOP切入点，如x.y.z.service.*,配置多个英文逗号分隔




#客户端使用方法
> spring:
>   application:
>     name: client
>   cloud:
>     config:
>       name: db-conf,${spring.application.name}

> db-conf为polestar中默认的数据库地址，为加密地址

> spring:
>   datasource:
>     druid:
>       o2o:
>         enabled: true  #这里要指定数据源可用
>         driver-class-name: oracle.jdbc.OracleDriver
>         url: ${o2ourl}  #这里为 db-conf变量
>         username: ${o2ousername} #这里为 db-conf变量
>         password: ${o2opassword} #这里为 db-conf变量
>
> @Autowired
> 	private O2OJdbcRepository  o2oInteger;



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)