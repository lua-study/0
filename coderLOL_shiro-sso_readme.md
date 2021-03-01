# shiro-sso

#### 项目介绍
1. springBoot shiro reids 实现session共享sso单点登录，  
2. 模块分为 shiro-auth  （shiro 认证中心），
 shiro-project-a  （A工程），
 shiro-project-b  （B工程），
 common-service   （service dao模块）

#### 软件架构
springBoot, shiro, redis, thymeleaf

#### 使用说明

 端口号：
1. shiro-auth           // 8810
2. shiro-project-a      // 8811
3. shiro-project-b      // 8812
4. common-service       // 无

#################################################

 使用步骤：
 ！！！ 运行 db.sql 数据库脚本文件
一、 common-service 模块。 依次执行：
1. mvn clean
2. mvn package
3. mvn install
二、 分别启动
    shiro-auth ==》 ShiroAuthApplication.java
    shiro-project-a ==》 ShiroProjectAApplication
    shiro-project-b ==》 ShiroProjectBApplication
三、 浏览器分别访问
1. 127.0.0.1:8011/test
2. 127.0.0.1:8012/test
四、 登陆
1. 随便登陆一个网址 输入admin, 123456，刷新另一个


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)