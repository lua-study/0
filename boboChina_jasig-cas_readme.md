# 基于jasig-cas 4.0.4的单点登录, 主要做了以下修改:
1. 数据库认证, 使用MD5带salt的方式
2. 登录界面美化
3. 记住账号/密码
4. 登录成功后, 返回更多用户信息

# 使用方法: 
1. check out代码
2. 将项目cas-server-webapp导入到eclipse
3. 导入数据库脚本
4. 配置数据源: /cas-server-webapp/src/main/webapp/WEB-INF/deployerConfigContext.xml
5. mvn clean package
6. tomcat7:run
7. 访问:https://localhost:8443/cas/login



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)