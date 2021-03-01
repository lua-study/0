# Spring Cloud Alibaba Getting Started

###
I've become familiar with you leaving,I had to be better.
And looking forward to the next good girl.

### 
我已经慢慢熟悉你离开，我只好变得更好。
期待遇见下个美好。

## spring-cloud-starter-alibaba-nacos-discovery
### nacos-server  docker start
docker run --name nacos -d \
-e PREFER_HOST_MODE=hostname \
-e MODE=standalone \
-e SPRING_DATASOURCE_PLATFORM=mysql \
-e MYSQL_MASTER_SERVICE_HOST=192.168.9.118 \
-e MYSQL_MASTER_SERVICE_PORT=3306 \
-e MYSQL_MASTER_SERVICE_USER=root \
-e MYSQL_MASTER_SERVICE_PASSWORD=123456 \
-e MYSQL_MASTER_SERVICE_DB_NAME=nacos_config \
-e MYSQL_SLAVE_SERVICE_HOST=192.168.9.118 \
-e MYSQL_SLAVE_SERVICE_PORT=3306 \
-v /data/docker/nacos/logs:/home/nacos/logs \
-v /data/docker/nacos/conf:/home/nacos/conf \
-v /data/docker/nacos/data:/home/nacos/data \
-p 8848:8848 \
--restart=always \
nacos/nacos-server
### nacos-DiscoveryClient
@EnableDiscoveryClient


### nacos-config
spring.cloud.nacos.config.group 配置不同的组dev,test,prod
spring.cloud.nacos.config.file-extension 配置文件的后缀默认是properties,根据自己项目可修改为yml

### 负载均衡器
https://blog.csdn.net/beishuibo1517/article/details/100963825


### feigin
get请求传递对象时405错误，需要在对象之前加入注解@SpringQueryMap
优化：
默认情况下Feign的性能在RestTemplate的50%左右，虽然项目的瓶颈一般不会出现在Feign上，但如果能让Feign的性能更好一些，也只是有利无害，所以本小节简单谈谈Feign的性能优化。

默认情况下Feign底层是使用HttpURLConnection发送请求的，众所周知HttpURLConnection是没有使用连接池的，所以可以针对这点进行优化。例如，将底层的http请求客户端为更换为Apache的HttpClient或者OkHttp等使用了连接池的http客户端，据测试使用了连接池后可以提升15%左右的性能。

另一个优化的点就是设置合理的日志级别，之前已经介绍过日志级别的配置方式了，所以这里仅演示如何为Feign更换其他的http请求客户端及配置连接池。

## sentinel
### sentinel-dashboard docker start
docker run --name sentinel-dashboard -p 8858:8858 -d bladex/sentinel-dashboard:1.6.3
java -Dserver.port=8858 -Dcsp.sentinel.dashboard.server=172.16.1.198:8858 -Dproject.name=sentinel-dashboard \
-Dsentinel.dashboard.auth.username=sentinel -Dsentinel.dashboard.auth.password=123456 -jar sentinel-dashboard-1.6.3.jar &

For further reference, please consider the following sections:


## gatway
查看所有的过滤器：http://localhost:8000/actuator/gateway/globalfilters
查看所有的路由： http://localhost:8000/actuator/gateway/routes
自定义过滤器工厂： 
1.继承AbstractGatewayFilterFactory  -> RequestSizeGatewayFilterFactory
2.继承AbstractNameValueGatewayFilterFactory -> AddRequestHeaderGatewayFilterFactory


* [Official Gradle documentation](https://docs.gradle.org)
* [Spring Boot Gradle Plugin Reference Guide](https://docs.spring.io/spring-boot/docs/2.1.10.RELEASE/gradle-plugin/reference/html/)
* [Cloud Bootstrap](https://spring.io/projects/spring-cloud-commons)
## zipkin
### zipkin-server docker start
使用mysql数据库
https://github.com/openzipkin/zipkin/blob/master/zipkin-storage/mysql-v1/src/main/resources/mysql.sql

docker run -d \
--restart always \
-v /etc/localtime:/etc/localtime:ro \
-e MYSQL_USER=root \
-e MYSQL_PASS=123456 \
-e MYSQL_HOST=172.16.1.198 \
-e STORAGE_TYPE=mysql \
-e MYSQL_DB=zipkin \
-e MYSQL_TCP_PORT=3306 \
-p 9411:9411 \
--net host \
--name zipkin \
openzipkin/zipkin
### zipkin-client 
 
     org.springframework.cloud 
     spring-cloud-starter-zipkin 
 
### Additional Links
These additional references should also help you:

* [Gradle Build Scans – insights for your project's build](https://scans.gradle.com#gradle)



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)