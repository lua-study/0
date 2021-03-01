# 权限管理系统

#### 项目介绍

  一个完全前后端分离的通用的权限管理系统，同时也是web项目的脚手架，可以很方便的基于此系统开发项目。各个application可独立启动，只要依赖pms-authorization后，
  做一些简单的配置，就可以接入权限系统的管理，方便分模块开发。
        独立启动的web项目，为了能统一控制权限，目前的做法使用redis来接管session的保存，前置一个nginx来把各个系统的接口接到一个域名下，
      来实现，后续打算换成jwt的方式来验证。
      项目参考了jeesite等开源项目。感谢各位开源作者的工作。

#### 用到的开源框架
 1. spring boot 2.0 不用介绍了  
 2. jooq orm框架  
 3. shiro 权限框架  
 4. redis 缓存  
 5. alibaba druib 数据库连接池  
 6. react；阿里的 ice  前端框架

演示地址：
 - http://47.98.182.45:8099/#/user/login
 账号密码：admin/123456  

前端项目地址：  
 - https://gitee.com/yueyakk/pms-front-new
#### 内置功能
 1. 菜单列表 get  
 2. 新增菜单 get  
 3. 删除菜单 get  
 4. 模块列表 get
 5. 新增模块 get
 6. 删除模块 get
 10. 区域列表 get
 11. 新增区域 get
 12. 删除区域 get
 18. 组织列表 get
 19. 新增组织 get
 20. 删除组织 get
 7. 用户列表 get
 8. 新增用户 get
 9. 删除用户 get
 13. 角色列表 get
 14. 新增角色 get
 15. 删除角色 get
 16. 角色授权 get
 17. 角色分配 get
 25. 日志列表 get
 22. 字典列表
 23. 新增字典
 24. 删除字典
 26. 在线用户查看 get
 27. 强制下线 get
 28. 主从数据源 get
 29. 通用分页 get
 
### 后续计划
 1. jwt支持
 2. 独立的文件管理模块
 3. 定时任务
 4. 即时推送
  
 ### 代码结构
1.  pms-authorization：权限管理模块
2.  pms-codegen： 代码生成模块
3.  pms-sysm：权限管理系统接口
4.  pms-common: 通用模块
5.  cms: 测试多项目单独启动用的，没啥用 


#### 使用说明

1. 导入数据库
2. 启动redis
3. 修改配置文件，启动Application

### 业务系统开发
1. 依赖pms-authorization模块
2. 配置applciation.yml
```
 auth:
     appId: xxx
     adminPath: /a
     frontPath: /f
     loginUrl: /login
     successUrl: http://127.0.0.1:8090
     type: client
```
3. 配置好reids连接和数据库连接
4. 在nginx中配置好该模块的接口匹配规则

#### 参与贡献

1. Fork 本项目
2. 新建 Feat_xxx 分支
3. 提交代码
4. 新建 Pull Request


#### 码云特技

1. 使用 Readme\_XXX.md 来支持不同的语言，例如 Readme\_en.md, Readme\_zh.md
2. 码云官方博客 [blog.gitee.com](https://blog.gitee.com)
3. 你可以 [https://gitee.com/explore](https://gitee.com/explore) 这个地址来了解码云上的优秀开源项目
4. [GVP](https://gitee.com/gvp) 全称是码云最有价值开源项目，是码云综合评定出的优秀开源项目
5. 码云官方提供的使用手册 [https://gitee.com/help](https://gitee.com/help)
6. 码云封面人物是一档用来展示码云会员风采的栏目 [https://gitee.com/gitee-stars/](https://gitee.com/gitee-stars/)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)