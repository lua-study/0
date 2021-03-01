# eureka-server

#### 介绍
spring cloud初学eureka注册中心集群搭建

#### 软件架构
spring boot 
spring cloud eureka server

### 修改hosts文件（C:\Windows\System32\drivers\etc），添加
127.0.0.1 peer1 peer2 peer3

### maven打包
mvn clean package  -Dmaven.test.skip=true

### 依次启动eureka注册中心集群
java -jar target/eureka-server-0.0.1-SNAPSHOT.jar  --spring.profiles.active=peer1
java -jar target/eureka-server-0.0.1-SNAPSHOT.jar  --spring.profiles.active=peer2
java -jar target/eureka-server-0.0.1-SNAPSHOT.jar  --spring.profiles.active=peer3

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)