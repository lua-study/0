# h-cloud

#### 项目介绍
h-cloud是一个基于Spring Cloud Greenwich.RELEASE,Spring Boot 2.1.3.RELEASE的最新的微服务开发平台，Spring Oauth统一认证中心，
支持微信，qq，gitee第三方登录，完善的权限控制（细化至按钮），独立的日志服务记录每一步操作。并使用layui进行前后端分离，
代码完全开源而且注释详尽，MIT协议允许你在任何地方使用代码，是学习spring cloud系列的不错选择！

#### 在线体验
  cloud.hepg.net  

    用户名：test 密码：123456 
    系统监控： 用户名hcloud，密码hcloud
    演示系统后台已屏蔽修改，删除功能
    
或者  点击此处  
直接使用gitee账号进行第三方登录

    

#### 当前架构
- 基于Spring Boot 2.1.3.RELEASE
- 基于Spring Cloud Greenwich.RELEASE
- 网关 Spring Cloud Gateway
- 注册中心 Eureka
- 认证方式 Spring Security oAuth 
- 持久层采用Spring Data JPA ，自动建表，实体类与数据库高度统一
    并封装基础curd的dao，service，controller以及权限控制
- 使用nginx进行前后端分离
- LayUI，使用q.js单页面路由，减少代码，增强体验

#### 当前功能
- 用户管理
- 权限管理（权限控制到按钮）
- 统一认证登录 jwt或redis
- 角色管理
- 统一日志记录（登录日志，操作日志。只需引入项目便可记录远程日志）
- Spring Boot Admin 服务监控
- 社交登录功能（微信，qq，gitee）

#### 项目结构
- hcloud-components  
- 权限管理（权限控制到按钮）
- 统一认证登录 jwt或redis
- 角色管理
- 统一日志记录（登录日志，操作日志。只需引入项目便可记录远程日志）
- Spring Boot Admin 服务监控
- 社交登录功能（微信，qq，gitee）
    

#### 安装教程
（详见doc文件夹下的文档）
1. 下载项目
2. 导入IDEA，准备好JDK8+
3. 安装gradle，build ,应群众要求，增加maven构建方式
4. 执行buildJar任务生成jar包 或使用maven
5. 准备数据库，redis等环境
5. 运行

#### 启动顺序
    eureka config gateway system auth 非必须：【audit monitor】
#### 项目截图
   ![图片](doc/img/user.png)
   ![图片](doc/img/auth.png)
   ![图片](doc/img/monitor.png)
   
#### 写在最后
    如果觉得我的项目帮到了您，麻烦您给点个star！ 
    有问题加qq群找我吧：829471660

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)