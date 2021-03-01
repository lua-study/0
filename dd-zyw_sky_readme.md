### 项目结构

* sky-core 基础工具配置包
* sky-codegen 代码生成,考虑到前后端分离不提供生成页面
* sky-security 权限包,基于shiro实现
* sky-module 基础模块包,包含系统管理、字典管理、菜单管理和用户管理等相关功能
* sky-webapp 管理控制台, 存放管理控制端页面
* sky-webboot springweb工程主入口[启动工程包，只包含工程配置]
* sky-boot springboot 工程主入口[启动工程包，只包含工程配置]
* db 数据库初始化脚本文件
* doc 文档，包含接口文档，功能说明等文档

### 功能说明

* 提供后台 controller,service,dao,mapper生成
* 提供便捷的配置文件读取
* 提供异常统一处理机制，规避不友好的异常展示
* 提供统一的API协议处理机制，规范开发
* 提供字典配置管理功能
* 基于shiro实现分布式session，支持web表单登录,app认证,第三方认证等

### 项目启动

项目支持使用 spring-boot 启动以及普通web项目启动方式

#### spring-boot 启动方式

由于采用了mvn多module方式构建项目，导致mvnw spring-boot:run无法直接调试启动项目
解决方案如下:

##### 方案一:
```
1、打包
mvnw clean package

2、使用java -jar 方式执行
java -jar ./sky-boot/target/sky-boot.jar com.zyw.SkyBoot
或者
java -cp ./sky-boot/target/sky-boot.jar com.zyw.SkyBoot
```
##### 方案二:
```
1、安装到本地
mvnw install

2、进入sky-boot，执行spring-boot:run
cd sky-boot
mvnw spring-boot:run
```

#### web项目启动方式
```
部署到IDE tomcat server 中即可
```

### 服务认证策略

#### 游客访问

```text
    游客访问，即在不需要认证就可以访问的公共内容。这种情况下，可以利
用客户端的mac地址、ip地址，判断是否同一用户访问，或者在第一次访问后存
储服务端返回的唯一码，在访问后续的请求时带上该参数。

    如：请求服务端后，返回响应头，rid[即 request id]=xxxx,下次访
问时，在请求头中，添加该请求头 rid=xxxx，这样服务端也能知道是同一个访
客在访问。
```

#### 用户访问
>1. 客户端使用用户输入的用户名密码登录服务器。
>2. 服务器根据用户名密码进行验证，验证通过，返回给客户端生成的临时加密秘钥并存储该秘钥。
>3. 客户端再访问服务器，利用秘钥对参数进行HBASE-MAC加密。
>4. 服务器根据加密串，来验证是否有效访问。


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)