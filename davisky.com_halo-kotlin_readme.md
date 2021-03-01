现在开了两个分支，一个分支在做数据分析，一个分支是集成spring oauth2.0技术
之后会接入最新的技术和实现

这是一个后台管理系统
采用spring boot，集成freemarker，shiro，spring cache，spring data jpa
前端采用bootstrap，dataTables 等等一些跟bootstrap集成的插件


记住要编译过之后在执行下面的操作

访问地址：http://127.0.0.1/
账户名/密码：admin/admin

1. 这个项目是maven项目，需要本地安装maven才行
2. 然后在{project}/src/main/resources/application.yml文件中修改数据库配置

```
spring:
  datasource:
    type: com.alibaba.druid.pool.DruidDataSource
    driver-class-name: com.mysql.jdbc.Driver
    url: jdbc:mysql://localhost:3306/halo
    username: root
    password: 123456
```

4. 部署好之后运行
```
{project}/src/main/kotlin/com/control/back/halo/SampleSpringApplication.kt
```



 _（可选）数据库脚本：
 ```
 {project}/src/main/resources/init-data.sql_ 
```
###  根据部分人反应导入数据库问题，解决方案（已提交git库）
 application.yml
 ```
 hibernate: 
    ddl-auto: create 
 ```
 启动的时候会默认引入import.sql自动导入数据

界面浏览

![登录](http://git.oschina.net/uploads/images/2016/1228/164411_92da7c23_20816.png "登录")
![角色管理](http://git.oschina.net/uploads/images/2016/1228/165013_1506ddfd_20816.png "角色管理")
![角色权限](http://git.oschina.net/uploads/images/2016/1228/165221_fc7ffeab_20816.png "角色权限")

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)