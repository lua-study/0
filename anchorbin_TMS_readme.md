# 项目启动步骤

1. 使用 `SQL_Scripts/tms.sql` 中的 sql 语句创建数据库与数据库表(数据库建立中，暂无)

2. 修改 `src/a_little_config.txt` 文件，填入正确的数据库连接用户名、密码

3. 将项目导入 IntelliJ IDEA 或 eclipse。

4. 打开 `cn.findix.tms.bin` 包下的 WWW 文件，右键单击该文件并选择 Debug As ---> Java Application。
        其它启动项目的方式见 《JFinal手册》。除此之外，项目还可以与其它普通java web 项目一样使用 tomcat
   jetty 等 web server 来启动，启动方式与非jfinal项目完全一样。

5. 打开浏览器输入`localhost` 即可查看运行效果

> 注意： 请确保您安装了 JavaSE 1.6 或更高版本，tomcat下运行项目需要先删除 `jetty-server-xxx.jar`，否则会有冲突



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)