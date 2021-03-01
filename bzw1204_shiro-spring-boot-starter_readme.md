# shiro-spring-boot-starter

[![License](https://img.shields.io/badge/license-Apache%202-4EB1BA.svg)](https://www.apache.org/licenses/LICENSE-2.0.html)

一、项目说明
-------
1. 为简化Apache Shiro权限框架和SpringBoot整合，本项目为SpringBoot和Shiro整合starter,引用shiro-spring-boot-starter即可自动配置（支持自动提示）Shiro。
2. 区分ajax请求和普通请求，普通请求通过跳转来响应未登陆和未授权，AJAX请求通过状态码和消息响应未登陆和未授权。
3. 集成jcaptcha验证码。
4. 密码输入错误，重试次数限制。
5. 账号唯一用户登陆，一个账号只允许一个用户登陆。
6. 与SpringCache无缝对接，支持guava、ehcache、redis等。
7. 提供认证\授权缓存数据同步接口，即时生效。
8. 支持动态URL过滤规则。
9. 无状态认证授权支持，共存有状态和无状态两种鉴权方式，无状态鉴权支持JWT(JSON WEB TOKEN)、HMAC(哈希消息认证码)两种协议。
10. 在线session管理，强制用户下线功能。

#### 使用说明
由于还没有maven坐标您可以下载源码自行编译或者直接下载jar包然后上传至本地仓库。
pom.xml中添加：
````
 
     com.scud 
     shiro-spring-boot-starter 
     1.0.0-SNAPSHOT 
 
````

二、配置说明
----------
**1. 配置文件**

强烈建议使用yml作为配置文件，以下也使用yml作为示例。目前该项目提供可配置的部分配置项如下：

待完善......

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)