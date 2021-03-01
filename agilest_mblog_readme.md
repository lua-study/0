### Mblog 开源Java多人博客系统

### 技术选型：

* JDK8
* MySQL
* Spring-boot
* Spring-data-jpa
* Shiro
* Hibernate-search
* Ehcache
* Freemarker
* Bootstrap
* SeaJs

### 启动：
 - 项目默认配置是在容器中启动(个人习惯), 如果想要main方法运行, 请自行修改
 ```xml
 配置：web/src/main/resources/application.yml (数据库账号密码)、向数据库导入初始数据 sql/db_mblog.sql
 运行：web/src/main/java/mblog/BootApplication
 访问：http://localhost:8080/
 后台：http://localhost:8080/admin
 账号：默认管理员账号为 admin/12345
```

- 更多文档及教程见 [http://mtons.com/dock/mblog](http://mtons.com/dock/mblog)
- QQ交流群：378433412

### 最新版本(2.6)更新内容：
    1. 去除webapp目录,因为很多人反映启动访问404
    2. 优化注册、找回密码逻辑,发邮件改成异步发送
    3. 发文章支持图片黏贴上传(来自@杭州-锋)
    4. 项目目录调整
    5. 去除mblog-api.jar 合并到base模块中
    6. ueditor改为tinymce
    7. 修改footer样式
    8. 优化文章统计
    9. 优化用户统计
    10.优化文章详情页code显示
    11.fixed角色修改不能保存
    12.fixed评论框按钮变形
    13.fixed后台添加菜单项bug
    
### 版本(2.5)更新内容：
    1. 前端页面结构、链接地址、接口目录调整
    2. Group修改为Channel, 对应的文章表和链接指向做相应的调整
    3. 全新的前端界面
    4. 修复上个版本留下的若干bug
    
### 版本(2.4)更新内容：
    1. 框架更新为 spring-boot
    2. 持久层更新为 spring-data-jpa, 去除原有的一些包依赖
    3. 前端页面模板语音更新为 freemarker
    4. 简化系统逻辑, 删除了Tag
    5. 重新定义了Group概念, 即内容分组, 不再有原来复杂的模板定制等, 去除了原有的视频和问答定制, 可以在Group里面自行扩展
    6. 全新的后台界面


[官网地址](http://www.mtons.com)
    
### 图片演示 
*首页
![首页](https://gitee.com/uploads/images/2018/0129/114306_9b9a3172_330414.jpeg "2018-01-29_112236.jpg")
*详细页
![详细页面](https://gitee.com/uploads/images/2018/0129/114350_1fce3677_330414.jpeg "2018-01-29_112548.jpg")
*登录/注册
![登录/注册](https://gitee.com/uploads/images/2018/0129/115058_15483796_330414.jpeg "2018-01-29_112236.jpg")
*我的主页
![我的主页](https://gitee.com/uploads/images/2018/0129/115331_1330f189_330414.jpeg "2018-01-29_112842.jpg")
![我的主页](https://gitee.com/uploads/images/2018/0129/115357_581d0a7c_330414.jpeg "2018-01-29_113226.jpg")


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)