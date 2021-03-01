[![Maven Central](https://maven-badges.herokuapp.com/maven-central/org.tinygroup/bizframe2/badge.svg)](https://maven-badges.herokuapp.com/maven-central/org.tinygroup/bizframe2)
#bizframe2 业务权限框架
如何运行业务权限框架
1.首先，mvn clean install
2.install 成功后修改jdbc.properties web/src/main/resources/jdbc.properties
  修改数据库用户名、密码。确保数据库连接的上即可。
3.web目录下mvn jetty:run 即可启动应用。数据库表结构以及初始化数据会自动安装。
4.登录页面。默认用户名admin,密码abcdef。

注意：
默认是mysql实现。
如果需要改成其他数据库。除了需要修改jdbc.properties文件，还需要修改application.xml文件中的database-install-processor/database-installer/database的type属性。目前可支持h2、mysql、oracle数据库。




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)