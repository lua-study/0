![输入图片说明](https://gitee.com/uploads/images/2018/0424/195910_a7fe354d_907621.png "logo.png")



# xlauch
  xlauch 是基于springboot + mybatis + beetls 快速开发脚手架, 包含了用户管理，组织机构管理，角色管理，功能点管理，菜单管理，权限分配，数据权限分配，代码生成，二次开发等功能

  系统基于Spring Boot 1.5技术，前端采用了easyUI。数据库以MySQL为实例 .
  
  QQ 交流群（224708661）

  gitee下载地址：git@gitee.com:huangxy3/xlauch.git

### 1 使用说明

1.1 安装说明
 
1.1.1 导入doc/xlauch.sql (目前只提供mysql版本）
   
1.1.2 修改application-*.properties 中数据库连接

```
# 主数据源
spring.datasource.druid.primary.url=jdbc:mysql://localhost/xlauch?useUnicode=true&characterEncoding=utf-8&tinyInt1isBit=false

spring.datasource.druid.primary.username=
spring.datasource.druid.primary.password= 
spring.datasource.druid.primary.driver-class-name=com.mysql.jdbc.Driver

# 测试数据源（用于后面测试生成功能）
spring.datasource.druid.second.url=jdbc:mysql://192.168.1.250:3306/jeeframe?useUnicode=true&characterEncoding=utf-8&tinyInt1isBit=false
spring.datasource.druid.second.username=root
spring.datasource.druid.second.password=bNVOqb7WKLX5Bjnw+LMv92taj25KOxDimXxILPQjw42wgv+1lHzOH8kr97xDwWdhpY67QuYCS7sWN4W46YbkFA==
spring.datasource.druid.second.driver-class-name=com.mysql.jdbc.Driver
```    
* 密码有经过druid加密，可以使用DruidUtil生成
 ![输入图片说明](https://gitee.com/uploads/images/2018/0424/164727_22f3aaca_907621.png "屏幕截图.png")

1.1.3
配置redis

```
spring.redis.host=192.168.1.207
spring.redis.port=6379
spring.redis.password=5i841qaz
spring.redis.database=0
spring.redis.timeout=20000
```

1.1.4 发布到tomcat
![输入图片说明](https://gitee.com/uploads/images/2018/0424/164941_b2eb68c3_907621.png "屏幕截图.png")

1.1.5 登录系统，用户名/密码（admin/123456）.
![输入图片说明](https://gitee.com/uploads/images/2018/0424/165225_b84c6370_907621.png "屏幕截图.png")

1.2 功能说明

1.2.1 权限管理

* 菜单管理：可以配置到按钮

![输入图片说明](https://gitee.com/uploads/images/2018/0426/170413_c213fc7a_907621.png "屏幕截图.png")

* 角色管理：
![输入图片说明](https://gitee.com/uploads/images/2018/0426/170550_76f05d4e_907621.png "屏幕截图.png")

* 管理员管理：新增后台管理用户
![输入图片说明](https://gitee.com/uploads/images/2018/0426/170636_0d931d6d_907621.png "屏幕截图.png")

1.2.2 二次开发

* 查询导出：只需配置SQL及参数，既可完成查询、导出；

![基础配置](https://gitee.com/uploads/images/2018/0424/165747_eb019228_907621.png "屏幕截图.png")

![输入图片说明](https://gitee.com/uploads/images/2018/0424/165802_e37b2dac_907621.png "屏幕截图.png")

-配置完成，选中点击预览
![输入图片说明](https://gitee.com/uploads/images/2018/0424/165909_736f2ffa_907621.png "屏幕截图.png")

* 文件上传：提供封装，可以快速实现文件上传

![输入图片说明](https://gitee.com/uploads/images/2018/0426/170840_ccffd1e7_907621.png "屏幕截图.png")

* 资源管理：管理工程目录及系统目录下任意文件，可以编辑文本文件
![输入图片说明](https://gitee.com/uploads/images/2018/0426/170911_5de54961_907621.png "屏幕截图.png")

![在线文件编辑](https://gitee.com/uploads/images/2018/0426/170934_a86c3b3f_907621.png "屏幕截图.png")

* 定时任务：自由配置定时任务
![输入图片说明](https://gitee.com/uploads/images/2018/0426/171146_0fe4f3fc_907621.png "屏幕截图.png")

* 对象管理：只要选择库表，系统就自动生成CRUD功能（有小惊喜，建议用测试库测试，新增一张用户表试试）
![输入图片说明](https://gitee.com/uploads/images/2018/0426/171231_f3fac905_907621.png "屏幕截图.png")

* xlauch 计划功能
 ![输入图片说明](https://gitee.com/uploads/images/2018/0426/171127_92b951bf_907621.png "屏幕截图.png")

### 2 其它说明
* 项目中使用lombok，没有使用过的可以参与一下博文或自行百度
[lombok插件安装](https://www.cnblogs.com/shindo/p/7550790.html)
[lombok使用说明](https://blog.csdn.net/u010695794/article/details/70441432)


请作者喝杯茶：
![![输入图片说明](https://gitee.com/uploads/images/2018/0424/180710_e5673511_907621.png "屏幕截图.png")](https://gitee.com/uploads/images/2018/0424/181135_4804d828_907621.png "屏幕截图.png")


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)