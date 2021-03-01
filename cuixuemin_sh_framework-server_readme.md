#framework-server

> 一个极简封装的Java平台快速开发框架

前端系统=> [http://git.oschina.net/backflow/framework-admin](http://git.oschina.net/backflow/framework-admin)

**注:如有功能更新, 一般需要同时更新两个项目 (若`src/main/resources/schema`下的SQL文件有变动, 也请一并导入数据库)**

## 系统结构
- 标准的SSM(Spring, SpringMVC, MyBatis)架构 
- 自带一个代码生成器：[http://git.oschina.net/backflow/framework-generator](http://git.oschina.net/backflow/framework-generator), 
  可生成从`mapper文件 > java实体 > dao > server > controller > view` 一条龙的代码, 生成器入口见`src/test/java/Generator.java`
- 极简的封装 (依赖于几个基类:`BaseEntity`, `BaseDao`, `BaseMybatisDao`, `BaseService`, `BaseController`),
  生成后无需编写一行代码即可拥有最基本的CRUD功能.
- 简化后的RBAC模型 ([**framework-admin**](http://git.oschina.net/backflow/framework-admin#基础功能) 中有说明) 
  通过一个注解`Permissions`与拦截器`PermissionInterceptor`便可实现对权限的控制, 不再需要依赖`apache-shiro`之类的权限框架 

运行步骤:
- clone项目, 以maven项目导入, 等待依赖下载完成
- 导入`src/main/webapp/WEB-INF/lib`下的两个`jar`包作为依赖(代码生成器与SQL美化)
- 执行`src/main/resources/schema`下的sql文件初始化数据库 (需本地安装MySQL, 并创建名为`admin`的数据库, 当然也可以为其它名字)
- 若MySQL没有跑在本地, 请修改`src/main/webapp/META-INF`下的`context.xml`(`tomcat`内置应用级别的数据源配置文件), 
  指向对应的数据库地址, 若数据源名称有改动, 还需要修改`web.xml`下的` `指向正确的数据源

管理员帐号/密码:`admin/admin`

项目刚刚发布完成度不高, 但后续会持续跟进, 也欢迎大家参与进来, 你的任何想法与建议我都很想知道! 快给我留言吧!!

交流QQ群: `240098272`


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)