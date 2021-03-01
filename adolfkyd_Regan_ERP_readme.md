# Regan_ERP

#### 项目介绍

ERP项目是基于微服务框架Jfinal搭建的，前端应用为react。页面更简洁，更美观，更清晰，目前项目正在开发阶段。

已完善权限登录，session失效验证，用户信息存储更新，头像截取与上传。后续会陆续更新模块代码，同时也期待更多的人加入此项目的开发中。

#### 欢迎加入 [regan_org组织【编程爱好者】](https://gitee.com/organizations/regan_org/invite?invite=dddf200261b5b5b3cc442eb5d661b872ad4de3598d087d4c00dff9da30dd446d17494c4c2357cf5d)

#### 部署与启动
- 启动：执行ErpConfig main方法。
- 访问：此处默认端口（8080）
    - erp 项目访问地址：[http://localhost:8080/](http://localhost:8080/)。
    - erp API访问地址：[http://localhost:8080/api](http://localhost:8080/api)。
    - erp 文档访问地址（待更新）：[http://localhost:8080/doc](http://localhost:8080/doc)。

> jfinal启动失败情况：ecplise与idea启动时有所区别，注意main方法启动方式注释。 
  这里是列表文本idea如果启动方式正确，任然启动失败可参考如下配置。 
    Project settings -> Modules
    参考：[截图](https://regan_jeff.gitee.io/regan_data_img/2018/09/WX20180907-105618@2x.png。) 
> 默认管理员账号：admin / 123456

#### 演示
- 演示地址（还在开发中）：[http://47.93.202.241/#/](http://47.93.202.241/#/)
> 账号密码：admin / 123456  
> 此处演示只限部分已完成的功能，后续还在不断迭代。

#### 页面功能开发
由于erp项目前端是用react开发的，所以项目架构整体来说在开发阶段属于前后端分离。由erp提供接口，react调用进行页面渲染。在部署的时候
react可打包为静态页面，放入erp项目webapp下即可直接展现。

所以需要进行页面开发的时候，首先安装node开发环境。并下载erp页面项目[Regan_ERP_Source](https://gitee.com/regan_org/Regan_ERP_Source),修改对应的erp服务代理接口即可开发。具体配置可参考Regan_ERP_Source。


#### _截图：_ 

- 登录模块：![登录](http://file.homeins.cn/Fpy_SvR5eUKVwENJSAAbfRuthZWh)
- 主页（待开发）：![主页](http://file.homeins.cn/FgpYZOf3hzsXCHt2mh0diZGmPm8F)
- 用户列表：![](http://file.homeins.cn/FpdpkkyzQV_vai7u2FtyNJiK_5Vy
)
- 个人设置：![个人设置](http://file.homeins.cn/FsF3wFOz6ser_vNBUxv9daMsaJxe)

#### 功能集成：[regan_api](https://gitee.com/regan_org/jfinal-api)
[文档](https://gitee.com/regan_org/jfinal-api)
- 统计功能集成：![](http://file.homeins.cn/FhFsTPxR06yqVWslnzIQnn8g6-7p)
- 接口文档自动化生成：![](http://file.homeins.cn/FnRp5x4JeVXt770BQvJazNuoBHT6)
- 集合postman在线调用：![](http://file.homeins.cn/FnIshvg5Om3QP49PBuX59mtbkW14)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)