# tyqx-cms

#### 项目介绍
本系统完全开源免费，基于springboot、mybatisplus、shiro、dubbo、zookeeper、log4j、layuicms2.0、mysql5.6、redis、jdk1.8开发而成，内置代码生成器，能够快速生成controller层、service层、dao层、实体层简单完整的增删改查代码，节省开发时间，快速构建企业级的web应用系统。具备完整的权限管理功能，代码简洁，容易入门，方便您进行二次开发。

tyqx-cms精简版，去除分布式部署（zookeeper、dubbo）：https://gitee.com/xieke90/common-admin

#### 软件架构

- 核心框架：SpringBoot
- 安全框架：Shiro（细粒度控制：目录菜单按钮都按权限加载）
- 缓存框架：Redis
- 分布式框架：Dubbo（注册中心：Zookeeper）
- 持久层框架：MyBatisPlus
- 数据库连接池：Druid
- 日志管理：Log4j
- 前端框架：Layui
- 后台模板：LayuiCMS2.0

#### 系统功能

- 系统登录
![系统登录](https://images.gitee.com/uploads/images/2018/1011/085445_6e25f3e5_583593.png "登录.png")
- 后台首页
![后台首页](https://images.gitee.com/uploads/images/2018/1117/190342_193c79a8_583593.png "后台首页.png")
- 用户管理
![用户管理](https://images.gitee.com/uploads/images/2018/1011/085535_f29e112c_583593.png "用户管理.png")
- 角色管理
![角色管理](https://images.gitee.com/uploads/images/2018/1011/085601_935470aa_583593.png "角色管理.png")
![角色添加](https://images.gitee.com/uploads/images/2018/1011/085624_1cfecc20_583593.png "角色添加.png")
![角色编辑](https://images.gitee.com/uploads/images/2018/1011/085643_1e47e2e8_583593.png "角色编辑.png")
- 权限管理
![权限管理](https://images.gitee.com/uploads/images/2018/1011/085704_272939a3_583593.png "权限管理.png")
![权限编辑](https://images.gitee.com/uploads/images/2018/1011/085750_41109161_583593.png "权限编辑.png")
- 登录日志
![登录日志](https://images.gitee.com/uploads/images/2018/1011/085817_40092e73_583593.png "登录日志.png")
- 系统日志
![系统日志](https://images.gitee.com/uploads/images/2018/1117/190424_dab9b4dc_583593.png "系统日志.png")
- 图标管理
![图标管理](https://images.gitee.com/uploads/images/2018/1011/085838_f1bca5d2_583593.png "图标管理.png")


#### 使用说明

1. 导入import.sql到mysql数据库
2. 运行redis、zookeeper
3. 运行服务提供方ServiceApplication，再运行服务消费方Application
4. 访问http://127.0.0.1:5555/ （注：管理员账号：admin 密码：123456，测试账号：test 密码：123456）

#### 作者说明
QQ：949118693（邪客）

JAVA技术社区：780509097

![JAVA技术社区](https://images.gitee.com/uploads/images/2018/0906/181739_496c27c1_583593.png "Java技术社区群聊二维码.png")

博客：http://xieke90.iteye.com/

公众号：xkjszt（随时更新技术文章）

![邪客杂谈](https://images.gitee.com/uploads/images/2018/0902/104634_2a5baaa1_583593.jpeg "qrcode_for_gh_1b3c05e1fe5e_258.jpg")

诚邀志同道合的朋友加入一道为开源做贡献！

专注开源开发群：877894892

![专注开源开发](https://images.gitee.com/uploads/images/2018/1010/114348_9fa0b4f2_583593.png "专注开源开发群聊二维码.png")

 **闲暇之余请作者喝杯咖啡吧！** 

![喝杯咖啡](https://images.gitee.com/uploads/images/2018/1117/191310_26ac9c2b_583593.png "喝杯咖啡.png")



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)