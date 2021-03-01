# Pro-Cloud


**以下是cloud平台简介**
#### 介绍
系统采用前后端分离模式，前台采用 vue.js 为核心框架，后台基于 Spring Cloud alibaba、Spring Security Oauth 2.0 开发企业级认证与授权，提供常见服务监控、链路追踪、日志分析、缓存管理、任务调度等实现。基于在线教育平台开发和运营经验打造出来的产品，致力于打造一个全行业都适用的分布式在线教育系统。  

#### 前台主要功能介绍

1. 生成代码模块，节省开发时间，提高开发效率。
2. 统一授权中心，打造平台中心。
3. 后台权限，用户，字段等基础统一管理。
4. sms 短信，邮件，oss 文件统一模块管理。
5. 在线课程以及在线考试模块，题库管理等。
6. 各种组件注解开发，让代码简洁，通俗易通，以提高效率

#### 相关工程
后台管理前端工程vue-element-admin（pro-ui）：[码云地址](https://gitee.com/gitsc/pro-ui)  
后台管理前端工程layui（pro-layui）：[码云地址](https://gitee.com/gitsc/pro-layui) 

#### 文档
详细请参考: [pro-cloud技术文档](http://doc.eduvipx.cn)

#### 软件架构
nacos + Spring Cloud Oauth2 + Spring Cloud gateway +  Feign + mybatisplus等
```
Pro-Cloud
├── cloud-admin -- 系统基础模块
│   ├── cloud-admin-common  -- auth客户端
│   ├── cloud-admin-api   -- admin暴露的feign接口
│   └── cloud-admin-service -- admin模块的实现
├── cloud-auth  -- auth服务端
├── cloud-common    -- 系统公共模块
│   ├── cloud-common-util   -- 实体的公共类
│   ├── cloud-common-data   -- 对数据库操作和缓存
│   └── cloud-common-pom    -- 管理common版本
├── cloud-gateway   -- springcloud gateway 网关 
├── cloud-generator -- 代码生成
├── cloud-nacos -- nacos 集成
├── cloud-security  -- auth客户端
└── docs    -- pro-cloud文档
```
   
| 版本规划| 解决问题|
|----: |:--------:|
| v0.5 | 微服务架构的搭建，基础数据，用户，角色，部门，多租户，微服务文件上传支持，在线监控等 |
| v0.6 | 前端vue的集成，定时任务处理xxl-job，分布式事物的解决，代码在线生成器 |
| v0.7 | 保利威视的集成、在线课程以及在线考试的模块完成 |
| v0.8 | vue-element-admin的集成和文档的完善 |
| v0.9 | 课程的评论收藏，以及题目的收藏完成 |
| v1.0 | 在线论坛的完成 |
#### 安装教程

1. 安装mysql redis idea工具
2. 导入代码
3. 使用skywalking 链路追踪

#### 使用说明

1. /auth/oauth/token 获取token 
2. 先启动auth 统一登录中心，然后启动admin模块，统一管理后台
3. /code 获取验证码      
4. 生成代码接口示例：
generator/code?tableName=sys_user&moduleName=admin&comments=用户表     
5. 继承授权中心模块需要实现ProUserDetailsService接口（不实现只会走默认方法），如果定制发邮件需要重构SmsCodeSender接口
6. 继承data模块需要实现SystemService。获取当前用户id（不实现只会走默认方法）
7. 设置是否开启mybatisplus日志拦截性能分析mybatis-plus.performanceInterceptor.enabled:true



#### 参与贡献

1. [Mybatis-Plus](https://mp.baomidou.com/)
2. [Spring Cloud Oauth2](https://spring.io/projects/spring-security-oauth)
3. [Nacos](https://nacos.io/zh-cn/docs/quick-start.html)
4. [hutool](https://www.hutool.cn/docs/#/)


#### Pro-Cloud建设

1. 官方地址 [www.eduvipx.cn](http://www.eduvipx.cn) 文档地址http://www.eduvipx.cn:8000/ 官方网站正在建设中…… 可以先查看文档


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)