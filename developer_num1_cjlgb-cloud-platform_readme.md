# cjlgb-cloud-platform

## 项目地址
试用账号：admin,admin
- 在线预览：http://oauth.cjlgb.com:8888/
- 前端代码：https://gitee.com/cjlgb/cjlgb-design-upms
- 后端代码：https://gitee.com/cjlgb/cjlgb-cloud-platform

## 本地运行需要配置Hosts
~~~
127.0.0.1	cjlgb-design-gateway
127.0.0.1	cjlgb-design-nacos
127.0.0.1	cjlgb-design-rabbitmq
127.0.0.1	cjlgb-design-redis
127.0.0.1	cjlgb-design-mysql
~~~

## Nacos Docker 
docker-compose.yaml
~~~
version: "3"
networks:
  default:
    external:
      name: cjlgb-cloud-platform
services:
  cjlgb-design-nacos:
    image: nacos/nacos-server:1.1.4
    container_name: cjlgb-design-nacos
    environment:
      - PREFER_HOST_MODE=hostname
      - MODE=standalone
    restart: on-failure
~~~

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
mybatis-plus:
  configuration:
    log-impl: org.apache.ibatis.logging.stdout.StdOutImpl
~~~

## Redis Docker
docker-compose.yaml
~~~
version: '3'
networks:
  default:
    external:
      name: cjlgb-cloud-platform
services:
  cjlgb-design-redis:
    restart: always
    image: redis
    hostname: cjlgb-design-redis
    container_name: cjlgb-design-redis
~~~

## RabbitMq Docker
docker-compose.yaml
~~~
version: '3'
networks:
  default:
    external:
      name: cjlgb-cloud-platform
services:
  cjlgb-design-rabbitmq:
    restart: always
    image: rabbitmq:latest
    container_name: cjlgb-design-rabbitmq
    hostname: cjlgb-design-rabbitmq
    environment:
      RABBITMQ_DEFAULT_USER: guest
      RABBITMQ_DEFAULT_PASS: 2e564ee5-d9ed-11e9-bab6-0242ac170005
      RABBITMQ_DEFAULT_VHOST: cjlgb-cloud-platform
~~~

## Nginx Docker
docker-compose.yaml
~~~
version: '3'
networks:
  default:
    external:
      name: cjlgb-cloud-platform
services:
  cjlgb-design-nginx:
    container_name: cjlgb-design-nginx
    image: nginx
    volumes:
      - /opt/apps/docker-container/cjlgb-design-nginx/conf/nginx.conf:/etc/nginx/nginx.conf
      - /opt/apps/docker-container/cjlgb-design-nginx/website:/usr/share/nginx/html
    ports:
      - 80:80
~~~

## Nginx Config
~~~
worker_processes  1;
events {
    worker_connections  1024;
}

http {
    include       mime.types;
    default_type  application/octet-stream;

    sendfile        on;

    keepalive_timeout  65;

    access_log off;

    gzip  on;

    server {
        listen       80;
        server_name  nacos.cjlgb.com;

        location / {
            proxy_pass    http://cjlgb-design-nacos:8848/nacos/;
        }
    }

    server {
        listen       80;
        server_name  admin.cjlgb.com;

        location /apis/ {
            proxy_pass    http://cjlgb-design-gateway:10001/;
        }

        location / {
            root   /usr/share/nginx/html;
            index  index.html index.htm;
        }
    }
}
~~~

## 启动顺序
- UpmsApplication.java
- SystemApplication.java
- OauthApplication.java
- GatewayApplication.java

## 功能截图
![images](https://cjlgb-design-upms.cdn.bcebos.com/img%2F1585133264011.png)

![images](https://cjlgb-design-upms.cdn.bcebos.com/img%2F1585133264012.png)

![images](https://cjlgb-design-upms.cdn.bcebos.com/img%2F1585133264013.png)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)