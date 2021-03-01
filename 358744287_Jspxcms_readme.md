 本源码包采用maven结构，和普通eclipse的web项目结构不一样，且不包含lib目录下的第三方jar包。

## 环境要求

- JDK1.6或更高版本（支持JDK7、JDK8）。
- Servlet2.5或更高版本（如Tomcat6或更高版本）。
- MySQL5.0或更高版本。
- Maven3.0或更高版本。

## 搭建步骤

1. 创建数据库，数据库字符集选择为utf8或者utf8mb4(支持更多特殊字符，推荐)。
2. 执行数据库脚本。数据库脚本在database目录下，按先后顺序分别执行1_table_sql.txt、2_data_sql.txt、3_reference_sql.txt。
3. 在eclipse中导入maven项目。点击eclipse菜单File - Import，选择Maven - Existing Maven Projects。创建好maven项目后，会开始从maven服务器下载第三方jar包（如spring等），需要一定时间，请耐心等待。
4. 修改数据库连接。打开/src/main/resources/custom.propertis文件，根据实际情况修改jdbc.url、jdbc.username、jdbc.password的值。
5. 运行程序。在eclipse中，右键点击项目名，选择Run as - Maven build...，Goals填入tomcat6:run，然后点击Run。
6. 访问系统。前台地址：http://localhost:8080/，手机站地址：http://127.0.0.1:8080/；后台地址：http://localhost:8080/cmscp/index.do，用户名：admin，密码：空。


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)