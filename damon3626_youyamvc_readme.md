# youyamvc
优雅MVC 网站地址：http://www.magicalcoder.com

声明 此项目中的所有demo代码全是MagicalCoder自动生成 如有疑问 请加QQ群323237052

简介：
youyamvc 由MagicalCoder网站开发的一款基于SpringMvc搭建的javaWeb框架，
配合MagicalCoder提供的在线编程工具，通过拖拽快速完成您的业务功能，为我们开发者节省大量的时间，
使用了这个，或许您再也不用加班啦，那将是我们最大的荣幸与目标

技术选型：
1 技术框架 springMvc + MyBatis + Jsp
2 其他技术 tomcat maven  memcache或ehcache
3 jdk1.6以上 默认1.8 如需更改请查询pom.xml

项目搭建过程
1 下载项目
2 安装maven
3 导入工程
4 安装mysql5.0以上版本
5 安装memcache 默认使用ehcache无需安装
    linux apt-get install memcached
    window 1. 下载memcache的windows稳定版，解压放某个盘下面，比如在c:\memcached
           2. 在终端（也即cmd命令界面）下输入 'c:\memcached\memcached.exe -d install' 安装
           3. 再输入： 'c:\memcached\memcached.exe -d start' 启动。NOTE: 以后memcached将作为windows的一个服务每次开机时自动启动。这样服务器端已经安装完毕了。
6 配置
src/main/resources/jdbc.properties
src/main/resources/xmemcached.properties 使用ehcache可忽略此配置

7 导入项目sql
  youyamvc.sql

8 tomcat启动项目
  后台：http://localhost:8080/admin     用户名密码 admin/admin

9 至此您完成了youyamvc的部署

10 youyamvc只是一个MVC框架，真正能帮助您的 请访问 http://www.magicalcoder.com/ 下载客户端自动编程工具 还是亲自来尝试一下吧

YouyaMvc更新日志

2016-3-25
    1 ProjectUtil迁移至core 便于升级管理
    2 更改默认缓存服务器为ehcache，刚下载工程可以不安装memcache导入表结构后直接启动
2016-4-21
    1 优化了很多功能 配合最新版神奇码农pc客户端

2016-5-8
    1 增加模板工具类
    2 增加首页模板
    3 支持API接口
2016-8-5
    1 增删改最难做的其实就是外键的处理，本次整体优化外键表单操作
    2 增加另一种详情页外键关联处理
    3 修复若干bug

MagicalCoder客户端更新日志

2016-3-17
    新增关联表方式：搜索下拉方式解决多表关联外键功能
2016-3-23
    每个表增加 是否作为外键下拉查询展示(一处设置处处剩下节省劳动力) 同时兼容现有的自定义外键下拉属性
2016-8-5
    1全新版本的客户端 网页版功能全部迁移至客户端 强大的外键关联操作 表单增加
    2支持自定义接口快速编写
    3多版本控制 不升级也能继续使用youyamvc老版本



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)