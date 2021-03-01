# Spring Cloud 基于网关的统一授权认证

 本项目基于[汪云飞记录本](http://www.wisely.top/2017/06/14/spring-cloud-oauth2-zuul/?d=3)[Github地址]( https://github.com/wiselyman/uaa-zuul)由于不好部署需要导入数据库等原因本人稍微做了一些改进,但总体上还是相似的,只是更容易部署省去了导数数据库等麻烦的操作。
 如果对Spring Boot开发感兴趣可以看看[JavaEE开发的颠覆者: Spring Boot实战](http://product.dangdang.com/23926195.html)作者也是`汪云飞`.
 
 使用OAuth2实现多个微服务的统一认证授权,通过向`OAUTH`服务发送某个类型的`grant type`进行集中认证和授权获得`access token`,这个`access token`是受其他微服务信任的。后续访问中可以通过这个`access token`来进行。
 
 * account: 用户微服务
 * xfauth:  OAUTH2认证授权中心
 * gateway: 边界网关
 * eureka:  服务注册和发现
 

## 基础环境
1. 开启MySql 修改`xfauth`配置文件`bootstrap.yml`中的`datasource`配置mysql用户名、密码、数据库名。
2. 开启Redis 修改`xfauth`配置文件`bootstrap.yml`中的`redis`如果默认端口号是6379 host为 localhost 则不用修改。

## 运行

1. 运行eureka 端口号8888

2. 运行gateway    端口号8088

3. 运行xfauth(因为使用了JPA会自动创建数据表不用导入数据库,只需要开启mysql) 端口号5000
   账户1: username:`fpf`    password:`fpf`
   账户2: username:`wl`     password:`wl`
   相关的设置可以在`xfauth`项目中的`Init`类中看到

4. 运行account    端口号8083

## 测试
1. 通关`zuul`网关访问认证服务获取 `access token` 8088是网关端口
![](https://ws4.sinaimg.cn/large/006tKfTcly1fjxbv9b9poj318o10en4m.jpg)

2. 通过`access token`访问`xfauth`中的`/user`API获取用户信息
![](https://ws4.sinaimg.cn/large/006tKfTcly1fjxby3oecyj3190106n3p.jpg)

3. 使用相同的`access token`访问`account`中的`/current`API获取用户信息
![](https://ws3.sinaimg.cn/large/006tKfTcly1fjxc3bnuzvj318w0zmq8s.jpg)
可以看到都是相同的用户信息

4. 使用`access token`访问`account`中带`权限`的`/query`API
![](https://ws3.sinaimg.cn/large/006tKfTcly1fjxc604ucmj319g0mygos.jpg)

5. 使用`wl`用户重新获取`access token`访问`account`中带`权限`的`/query`API
![](https://ws4.sinaimg.cn/large/006tKfTcly1fjxc8wrybwj318g0ren0r.jpg)

## 后序
想更清楚的了解OAuth2.0 可以看[阮一峰:理解OAuth 2.0](http://www.ruanyifeng.com/blog/2014/05/oauth_2_0.html)

如果对你有帮助点个Star把~ 
本人博客 [www.xingfly.com](http://www.xingfly.com)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)