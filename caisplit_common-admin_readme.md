# common-admin

#### 项目介绍
tyqx-cms精简版，去除分布式部署（ zookeeper、dubbo），基于springboot、mybatisplus、shiro、log4j、layuicms2.0、mysql5.6、redis、jdk1.8开发而成，具备完整的权限管理功能，代码简洁，容易入门，方便您进行二次开发，节省开发时间，快速构建企业级的web应用系统。

系统预览地址：http://148.70.12.166:9999/
（注：管理员账号：admin 密码：123456，测试账号：test 密码：123456，
请朋友们不要恶意删除数据，想要测试删除功能可以先添加数据后再行测试，谢谢！）

common-admin项目配套代码生成器（分离版，只能生成后台代码）：https://gitee.com/xieke90/code-generator

common-admin分布式版（zookeeper、dubbo）：https://gitee.com/xieke90/tyqx-cms

#### 软件架构
- 核心框架：SpringBoot
- 安全框架：Shiro（细粒度控制：目录菜单按钮都按权限加载）
- 缓存框架：Redis
- 持久层框架：MyBatisPlus
- 数据库连接池：Druid
- 日志管理：Log4j
- 前端框架：Layui
- 后台模板：LayuiCMS2.0


#### 系统功能

- 系统登录

![系统登录](https://images.gitee.com/uploads/images/2018/1207/100305_c682872f_583593.jpeg "微信图片_20181207100212.jpg")
- 后台首页

![后台首页](https://images.gitee.com/uploads/images/2018/1207/100331_5c35ccc1_583593.jpeg "微信图片_20181207100220.jpg")

- 用户管理

![用户管理](https://images.gitee.com/uploads/images/2018/1207/100403_1e5b0a44_583593.jpeg "微信图片_20181207100239.jpg")

- 角色管理

![角色管理](https://images.gitee.com/uploads/images/2018/1207/100429_2882389e_583593.jpeg "微信图片_20181207100224.jpg")

- 权限管理

![权限管理](https://images.gitee.com/uploads/images/2018/1207/100522_cdbba516_583593.jpeg "微信图片_20181207100229.jpg")

- 登录日志

![登录日志](https://images.gitee.com/uploads/images/2018/1207/100541_20c3dfa7_583593.jpeg "微信图片_20181207100158.jpg")

- 系统日志

![系统日志](https://images.gitee.com/uploads/images/2018/1207/100600_24d16e3f_583593.jpeg "微信图片_20181207100232.jpg")

- 图标管理

![图标管理](https://images.gitee.com/uploads/images/2018/1207/100613_0f7a0591_583593.jpeg "微信图片_20181207100236.jpg")

#### 使用说明

1. 创建数据mysql数据库sys_admin，导入init.sql，修改数据库链接配置
2. 运行redis，再运行CommonAdminApplication
3. 访问http://127.0.0.1:9999/ （注：管理员账号：admin 密码：123456，测试账号：test 密码：123456）

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