# cjlgb-cloud-platform

## 项目地址
- 在线预览：http://admin.cjlgb.com/
- 前端代码：https://gitee.com/cjlgb_admin/cjlgb-design-upms
- 后端代码：https://gitee.com/cjlgb_admin/cjlgb-cloud-platform

## 本地运行需要配置Hosts
~~~
127.0.0.1	cjlgb-design-gateway
127.0.0.1	cjlgb-design-nacos
127.0.0.1	cjlgb-design-rabbitmq
127.0.0.1	cjlgb-design-redis
127.0.0.1	cjlgb-design-mysql
~~~

## 先运行Nacos服务端
部署文档：https://nacos.io/zh-cn/docs/quick-start.html

## Nacos Config配置
application.yaml
~~~
spring:
  datasource:
    url: jdbc:mysql://cjlgb-design-mysql:3306/cjlgb_cloud_platform?characterEncoding=utf8&useSSL=false&serverTimezone=GMT%2B8
    username: root
    password: 2e564ee5-d9ed-11e9-bab6-0242ac170005
    driver-class-name: com.mysql.cj.jdbc.Driver
  redis:
    host: cjlgb-design-redis
    port: 6379
    password:
  rabbitmq:
    host: cjlgb-design-rabbitmq
    port: 5672
    username: guest
    password: guest
    virtual-host: cjlgb-cloud-platform
~~~

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)