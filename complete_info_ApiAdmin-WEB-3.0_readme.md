 
     
         
     
 

# ApiAdmin-WEB
[![](https://img.shields.io/badge/build-passing-brightgreen.svg)]()
[![ApiAdmin](https://img.shields.io/hexpm/l/plug.svg)](http://www.apiadmin.org/)
[![ApiAdmin](https://img.shields.io/badge/ApiAdmin-v3.0.6-brightgreen.svg)](https://gitee.com/apiadmin/ApiAdmin)
[![vue](https://img.shields.io/badge/vue-2.5.13-brightgreen.svg?style=flat-square)](https://github.com/vuejs/vue)
[![iview ui](https://img.shields.io/badge/iview-2.8.0-brightgreen.svg?style=flat-square)](https://github.com/iview/iview)

# 特别提示
本项目依赖于[ApiAdmin](https://gitee.com/apiadmin/ApiAdmin)，请确保您同时具备PHP和Vue的技能，否则使用本项目存在技术性障碍！

## 线上体验
[https://admin.apiadmin.org](https://admin.apiadmin.org)。账号请加群获取！

## Install
```bush
// install dependencies
npm install
```

## Prepare
```bush
/build/webpack.prod.config.js中的publicPath参数需要变更为你自己的项目域名
/build/config.js中的baseUrl需要换成你自己搭建的后台接口域名
```

## Run
### Development
```bush
npm run dev
```
### Production(Build)
```bush
npm run build
```

## 愿景

> 希望有人用它，希望更多的人用它。
> 希望它能帮助到你，希望它能帮助到更多的你。

## 简介

 1. 接口文档自动生成
 2. 接口输入参数自动检查
 3. 接口输出参数数据类型自动规整
 4. 灵活的参数规则设定
 5. 支持三方Api无缝融合
 6. 本地二次开发友好
 7. ...
 
 ```
 ApiAdmin（PHP部分）
 ├─ 系统维护
 |  ├─ 菜单管理 - 编辑访客权限，处理菜单父子关系，被权限系统依赖（极为重要）
 |  ├─ 用户管理 - 添加新用户，封号，删号以及给账号分配权限组
 |  ├─ 权限管理 - 权限组管理，给权限组添加权限，将用户提出权限组
 |  └─ 操作日志 - 记录管理员的操作，用于追责，回溯和备案
 |  ...
 ```

## 鸣谢

- [iView-Admin](https://github.com/iview/iview-admin)
- [iView](https://github.com/iview/iview)
- [Vue](https://github.com/vuejs/vue)
- [Webpack](https://github.com/webpack/webpack)

## 效果展示

![输入图片说明](https://gitee.com/uploads/images/2018/0224/095358_19cb42d0_110856.png "api.png")

![输入图片说明](https://gitee.com/uploads/images/2018/0224/095410_55dc23e1_110856.png "app.png")

![输入图片说明](https://gitee.com/uploads/images/2018/0224/095420_bddff990_110856.png "auth1.png")

![输入图片说明](https://gitee.com/uploads/images/2018/0224/095427_fa86e42d_110856.png "auth2.png")

![输入图片说明](https://gitee.com/uploads/images/2018/0224/095436_3600de17_110856.png "lock.png")

![输入图片说明](https://gitee.com/uploads/images/2018/0224/095444_d2a88da0_110856.png "user.png")

## 联系我们
官方唯一QQ群：221522638

## License
[Apache-2.0](http://www.apache.org/licenses/LICENSE-2.0)

Copyright (c) 2017-present, ApiAdmin


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)