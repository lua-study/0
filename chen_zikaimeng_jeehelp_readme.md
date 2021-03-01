# 简介
jeehelp 是一款基于SpringMVC+Spring+Mybatis+MybatisPlus+Redis 的敏捷开发系统；是以Spring Framework为核心容器，Spring MVC为模型视图控制器，Mybatis为数据访问层， Apache Shiro为权限授权层，Ehcahe和Redis对常用数据进行缓存，使用Redis 实现Session共享支持分布式部署，Bootstrap作为前端框架的优秀 开源 系统。
  
# 技术选型
1、后端

- 核心框架：Spring Framework
- 安全框架：Apache Shiro
- 视图框架：Spring MVC
- 服务端验证：Hibernate Validator
- 任务调度：Quartz 支持集群
- 持久层框架：Mybatis
- 数据库连接池：Alibaba Druid
- 缓存框架：Ehcache和Redis
- 日志管理：SLF4J、Log4j
- 工具类：Apache Commons、Jackson、Xstream、

2、前端

- JS框架：jQuery。
- CSS框架：Bootstrap
- 客户端验证：bootstrapvalidator。
- 富文本在线编辑：kindeditor
- 文件上传工具:Webuploader
- 数据表格：Bootstrap-Table
- 对话框：layer
- 树结构控件：jQuery zTree
- 日期控件： My97 

# 开发说明
- 系统可通过main方法对表名动态生成指定模板对应的jsp、controller、service和dao等
- 运行地址src/test/java/ com.jeehelp.generator
- 修改数据库配置文件config/application.properties 数据库账号密码
- 启动项目,默认管理员账号admin/密码admin

# 运行说明
- 导入database/jeehelp-v1.3.sql文件到mysql数据库
- 修改数据库配置文件config/application.properties 数据库账号密码
- 启动项目,默认管理员账号admin/密码admin

# 系统截图 
  ![image](https://git.oschina.net/uploads/images/2017/0731/222459_26954cf7_1404218.png )
  
  ![image](https://git.oschina.net/uploads/images/2017/0731/223032_e4ed9536_1404218.png)
  
  ![image](https://git.oschina.net/uploads/images/2017/0731/223108_80685179_1404218.png)
  
  ![image](https://git.oschina.net/uploads/images/2017/0731/223142_40428588_1404218.png)
  
  ![image](https://git.oschina.net/uploads/images/2017/0731/223204_7a840b40_1404218.png)
# 演示网址
 http://jeehelp.qsgl365.com 
 
 管理员账号：admin  密码：admin

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)