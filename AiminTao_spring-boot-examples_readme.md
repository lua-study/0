### spring-boot-examples


### 技术选型
- 核心框架：SpringBoot 2.0.3.RELEASE,SpringCloud Finchley.RELEASE
- 持久层框架：Mybatis-plus 2.1.6
- 数据库连接池：druid 1.1.6
- 缓存框架：Redis 
- 日志管理：logback
- 接口文档：swagger2
- 前端框架：Layui+Jquery+Freemarker模板

### 环境搭建
#### 开发工具
- Mysql:数据库
- IntelliJ IDEA:开发IDE
- Git:版本管理
- Navicat for MySQL: 数据库客户端
#### 开发环境
- JDK8+
- Mysql
- Redis
- Eureka
#### 开发指南
1. 本机安装jdk1.8、Mysql、Redis并启用相关服务，默认端口默认配置即可
2. 克隆源代码到本地并打开，推荐使用IntelliJ IDEA，本地编译并安装到本地maven仓库
3. 将项目根目录下的spring-boot-example.sql脚本导入到自己的数据库
4. 启动顺序
- 先启动Eureka注册中心，打开Maven Projects工具栏，打开路径：spring-cloud-eureka->Plugins->spring-boot,右击spring-boot:run,
点击'Debug Spring-Cloud-Eureka...’,如下图：
![输入图片说明](https://images.gitee.com/uploads/images/2019/0615/180340_24ca8062_1476348.png "屏幕截图.png")
看到端口号2222，说明启动成功。如下图：
![输入图片说明](https://images.gitee.com/uploads/images/2019/0615/180649_8183eff0_1476348.png "屏幕截图.png")
打开浏览器，访问http://localhost:2222
![输入图片说明](https://images.gitee.com/uploads/images/2019/0615/180906_c91d40e5_1476348.png "屏幕截图.png")
图中没有发现微服务，因为没有注册服务当然不可能有服务被发现了。
- 在启动config配置中心，同理如上。看到端口8888，说明启动成功。注册中心界面多了CONFIGSERVER,如下图：
![输入图片说明](https://images.gitee.com/uploads/images/2019/0615/181536_287ab56d_1476348.png "屏幕截图.png")
配置中心配置仓库地址：https://gitee.com/XiaoMuBiaoZaoFanQian/spring-cloud-config
- 启动file文件服务，更改数据库连接为自己的，如下图:
![输入图片说明](https://images.gitee.com/uploads/images/2019/0615/181832_f8ef2762_1476348.png "屏幕截图.png")
Redis端口默认是6379，如果要更改，改配置中心git仓库里的配置,如下图:
![输入图片说明](https://images.gitee.com/uploads/images/2019/0615/182105_fd421253_1476348.png "屏幕截图.png")
文件存储用的是阿里的OSS,将配置改成自己的，如下图：
![输入图片说明](https://images.gitee.com/uploads/images/2019/0615/182508_f659a630_1476348.png "屏幕截图.png")
启动服务，看到端口号8666,说明启动成功。
- 启动web服务，更改数据库连接配置为自己的，如下图：
![输入图片说明](https://images.gitee.com/uploads/images/2019/0615/183020_daf6f3f5_1476348.png "屏幕截图.png")
看到端口号8520，说明启动成功。打开浏览器，访问：http://localhost:8520/index
![输入图片说明](https://gitee.com/uploads/images/2017/1231/150939_9961dbda_1476348.png "登陆页面.png")

### 页面截图
用户管理页面
![输入图片说明](https://gitee.com/uploads/images/2017/1231/151035_9105f78e_1476348.png "用户管理页面.png")

用户编辑页
![输入图片说明](https://gitee.com/uploads/images/2017/1231/151129_764fb901_1476348.png "用户编辑页.png")

菜单管理页面
![输入图片说明](https://gitee.com/uploads/images/2017/1231/151153_94f1f82e_1476348.png "菜单管理页.png")

上传头像页面
![输入图片说明](https://gitee.com/uploads/images/2017/1231/151231_49b2a85b_1476348.png "修改头像页面.png")



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)