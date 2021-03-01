# SpringCloud示例
SpringCloud示例，版本为Finchley.M9。包括Netflit家族的几个部分，包括配置服务器、Eureka服务注册与发现、Ribbon负载均衡、Feign客户端、Hystrix服务熔断、Zuul网关等。 
不是很复杂，主要是这个版本是基于SpringBoot 2.0，和SpringBoot 1.X版本有点区别。网上挺多1.X配置的教程这里不过多说明 
 **1. 配置服务器**  
因为懒得在git上创建配置文件，所以配置成从本地读取配置文件： 
```
spring:
  profiles: 
    active: native
```
 **2. Eureka服务注册与发现**  
也比较简单，按照官方文档搭建好注册中心和服务，为了使配置服务器有所作用，将服务端口放在配置服务器上的配置文件上。 
主要是Eureka Server +Spring Security认证配置时出了问题，配置文件上：
```
1.X版本：

security:
  basic:
    enabled: true
  user:
    name:
    password: 

变成了：

spring:
  security:
    basic:
      enabled: true
    user:
      name:
      password: 

而且只要添加了Spring Security Starter依赖，spring.security.basic.enabled默认就是true，改成false也没用。
```
启动起来，客户端报异常：Cannot execute request on any known server。导致服务注册失败。 
各种检查配置，折腾了几个小时也没搞好，最后在GitHub上找到了[答案](https://github.com/spring-cloud/spring-cloud-netflix/issues/2754)，原来是SpringBoot从2.0.0.RC1升级到2.0.0.RELEASE的时候，有个类SpringBootWebSecurityConfiguration发生了变化： 
```
public class SpringBootWebSecurityConfiguration {

    @Configuration
    @Order(SecurityProperties.BASIC_AUTH_ORDER)
    static class DefaultConfigurerAdapter extends WebSecurityConfigurerAdapter {

        @Override
        protected void configure(HttpSecurity http) throws Exception {
            super.configure(http);
            http.csrf().disable();
        }
    }
}

```
新建这个类放在Eureka Server项目里面就可以了。或者将SpringCloud降到Finchley.M6及以下，同时SpringBoot降级到2.0.0.RC1，只能说尝鲜需谨慎。。。 
 **3. Ribbon负载均衡**  
这个也没什么好说的，太简单了。

 **4. Feign客户端**  
也没什么好说，官方把Feign改成了OpenFeign，用法和1.X基本没什么区别。

 **5. Hystrix服务熔断**  
在服务消费端规规矩矩改好配置，添加依赖：
```
 
     org.springframework.cloud 
     spring-cloud-starter-netflix-hystrix 
 
 
     org.springframework.boot 
     spring-boot-starter-actuator 
 
```
启动，又遇到坑了！！！ 
按照官方文档访问http://ip:port/hystrix.stream 查看断路由状态发现是404，根本就没有暴露hystrix.stream这个端点。又折腾了将近一个小时，才在另外一个官方文档上找到[答案](https://docs.spring.io/spring-boot/docs/current/reference/html/production-ready-endpoints.html)，原来是Actuator这个包变化了，默认只暴露health等几个端点，好吧，把配置加上： 
```
management:
  endpoints:
    web:
      exposure:
        include: hystrix.stream
```
启动后观察日志发现暴露的服务url竟然是/actuator/hystrix.stream，当然这也可以用，如果不想要/actuator，添加以下配置即可： 
```
management:
  endpoints:
    web:
      base-path: /
```
被SpringCloud官方文档坑了一把。
 
 **6. 配置更新**  
回头弄一下配置的刷新，配置服务器上的配置文件更新，其它服务可以不重启而获取最新配置。 
在服务消费端进行了修改，理所当然在post http://ip:port/refresh 时又是404，有了上面hystrix.stream的教训，马上在配置上增加： 
```
management:
  endpoints:
    web:
      exposure:
        include: refresh
```
OK，通过，配置刷新了。 
单个服务刷新没问题，再集成Spring Cloud Bus来批量刷新试试吧,这里用了Kafka： 
```
 
     org.springframework.cloud 
     spring-cloud-starter-bus-kafka 
 
```
这下我聪明了先改配置文件把bus/refresh端点暴露出来，启动，post http://ip:port/bus/refresh ，404！！！ 
好吧，不要过于相信官方文档，修改一下配置把所有端点暴露，观察启动日志发现有一个bus-refresh，post一下 http://ip:port/bus-refresh ，bingo，是想要的东西。
 
 **7. Zuul网关**  
没遇到什么问题了，主要是前面在服务上加了Spring Security，网关访问服务需要加上认证信息，具体看MyPreFilter.java
 
 **8.sleuth链路** 
 
本来想等zipkin-server支持springboot2.0的时候再弄的，但是一个多月过去了还没看到zipkin-server的支持，毕竟springboot1.x升级到2.0有不少类改名了之类的，修改zipkin-server源码改不过来，就随意搭建一个springboot1.x的，或者自己去官方下载一个zipkin-server的jar包运行。 
不过sleuth也不强制需要链路日志收集的服务器(比如zipkin-server)，可以输出到控制台，反正代码里面写了注释，这里不多说。
 

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)