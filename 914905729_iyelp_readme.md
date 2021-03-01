## 去好店

> 去好店，让你快速的找到喜欢的店铺。


### 技术选型：

* **服务端**

* SSH (Spring、SpringMVC、Hibernate）
* 安全权限 Shiro
* 搜索工具 Lucene
* 缓存 Ehcache
* 视图模板 freemarker 
* 其它 Jsoup、gson
* [disconver](https://gitee.com/quhaodian/disconver)

### quhaodian 工程介绍

* data	工程的controller，数据模块
* web	视图工程，不放代码，使用freemarker作为视图



## 搭建步骤

1. 创建数据库。如使用MySQL，字符集选择为`utf8`或者`utf8mb4`（支持更多特殊字符，推荐）。
2. 执行数据库脚本。数据库脚本在`database`目录下。
3. 在idea中导入maven项目。点击idea菜单`File` - `open`，选择 `项目所在磁盘位置`。创建好maven项目后，会开始从maven服务器下载第三方jar包（如spring等），需要一定时间，请耐心等待。
4. 创建mysql数据库，导入`haodian.sql`
5. 修改数据库连接。打开`/web/src/main/resources/jdbc.propertis`文件，根据实际情况修改`jdbc.url`、`jdbc.username`、`jdbc.password`的值。
6. 运行程序。在idea中，点击idea菜单`Run` - `Run`，选择`Run` - `Edit Configurations...`，选择`+`，选择`Maven`，选择文件位置,在`comand line`填入`jetty:run`或`tomcat7:run`，然后点击`Run`。
7. 访问系统。前台地址：[http://localhost:8080/web](http://localhost:8080/)，手机站地址：[http://127.0.0.1:8080/](http://127.0.0.1:8080/)；后台地址：[http://localhost:8080/web/login.htm](http://localhost:8080/web/login.htm)，用户名：admin，密码：123456。



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)