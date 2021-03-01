# verifycenter

#### 介绍
检定中心后台服务

#### 软件架构
spring+dubbo框架，后台数据库sqlserver，包括三个子模块：实体、接口、实现。
配置为http+json类型。
按照内容定义并实现了多个微服务接口，包括批次、检定、用户、设置、报告、研究等。
前端采用C#+WPF+telerik组件库，通过http+json访问后台微服务。

#### 安装教程

1. 在sql server 2008 R2 中创建数据库: calib;
2. 在sql server 2008 R2 中创建用户: vc, 并赋予public角色及calib库的db_owner 角色。
3. 切换到calib库，依次执行 data/verify-center.sql, 10/20/30-...等其他脚本文件。
4. 拷贝 /conf/zoo_sample.cfg为zoo.cfg，并在文件中增加一行：
admin.serverPort=8081（避免跟tomcat端口冲突）
然后运行/bin/zkServer.cmd, 启动 zookeeper-3.5.x。
5. 修改 /conf/server.xml，保持默认端口8080.
6. 启动 tomcat-8.5.x, 并将 services.war 拷贝到  /webapps/ 目录下。
7. 简单验证： 用浏览器访问：http://localhost:8888/services/user/11 ，返回内容：
{"code":0,"error":null,"version":"v20190825.1","single":{"createBy":null,"createDate":null,"updateBy":null,"updateDate":null,"id":"11","name":"测试11","lastLoginIp":null,"lastLoginLoc":null,"loginCount":0,"lastLoginTime":null,"lastOperTime":null,"lastOperIp":null,"lastOperLoc":null,"createTime":null,"mobile":null,"email":null,"passHash":null,"status":"EXPIRED","firmId":"11","firmName":"水司演示","emailValid":null,"emailToken":null,"userToken":null,"dmaId":null,"dmaIdList":null,"firm":null,"roles":null,"statusObj":null},"list":null}
或者用浏览器访问：http://localhost:8080/services/swagger/ ，返回内容：
![services-swagger](file:///services-swagger.png)
8. 详情查阅测试用例 https://gitee.com/abelli/verifycenter/blob/master/verifymeter-webapi/src/test/kotlin/com/abel/bigwater/verifymeter/webapi/


#### 使用说明

1. mvn clean
2. mvn package -DskipTests
3. cp services/target/services.war &lt;tomcat&gt;/webapps/

#### 参与贡献

1. Fork 本仓库
2. 新建 Feat_xxx 分支
3. 提交代码
4. 新建 Pull Request


#### 码云特技

1. 使用 Readme\_XXX.md 来支持不同的语言，例如 Readme\_en.md, Readme\_zh.md
2. 码云官方博客 [blog.gitee.com](https://blog.gitee.com)
3. 你可以 [https://gitee.com/explore](https://gitee.com/explore) 这个地址来了解码云上的优秀开源项目
4. [GVP](https://gitee.com/gvp) 全称是码云最有价值开源项目，是码云综合评定出的优秀开源项目
5. 码云官方提供的使用手册 [https://gitee.com/help](https://gitee.com/help)
6. 码云封面人物是一档用来展示码云会员风采的栏目 [https://gitee.com/gitee-stars/](https://gitee.com/gitee-stars/)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)