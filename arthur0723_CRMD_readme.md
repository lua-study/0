#Spring Cloud Project

#架构
Spring Cloud + Spring Boot + Maven 多模块管理

#MAVEN模块
crmd-server           : (8761)服务注册中心
crmd-gateway          : (8080)服务网关(验证，负载请求)
crmd-web              : (8081)API接口
crmd-admin-service    : (8082)商品模块（集成当当网Sharding-jdbc）
crmd-wechat-service   : (8083)订单模块（集成当当网Sharding-jdbc）
crmd-model            : 所有模块的实体
crmd-common           : 公共模块（工具类,资源......）
crmd-config           : 暂时没有使用

#目前架构图(待完善)
![](http://chuantu.biz/t5/38/1476863611x1961023832.png)

#服务中心
两台服务服务注册中心(相互注册)
--ip239 192.168.1.239:8761
--ip251 192.168.1.251:8761

#熔断监控视图
运行附件里的standalone-hystrix-dashboard-1.5.6-all.jar包,打开监控页面：http://localhost:7979/hystrix-dashboard，
输入监控的参数地址：http://localhost:8080/hystrix.stream
点击Add Stream然后点击Monitor Streams:
![](http://chuantu.biz/t5/38/1476763679x1961023832.png)


#API文档视图（Swagger2）
功能：可以查看，调试暴露的API接口
地址：http://localhost:8080/swagger-ui.html
![](http://chuantu.biz/t5/38/1476674694x1961023832.png)


#测试分布式事务(未完成)
模拟业务场景：用户下单，订单模块添加一条数据，同时修改商品模块中商品的购买数量。


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)