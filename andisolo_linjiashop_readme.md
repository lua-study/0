 # 前言
[![Spring Boot](https://img.shields.io/badge/spring--boot-2.1.1.1.RELEASE-brightgreen)](https://github.com/spring-projects/spring-boot)
[![vue](https://img.shields.io/badge/vue-2.6.10-brightgreen.svg)](https://github.com/vuejs/vue)
[![element-ui](https://img.shields.io/badge/element--ui-2.11.0-brightgreen.svg)](https://github.com/ElemeFE/element)
[![Vant](https://img.shields.io/badge/vant-2.2.0-brightgreen.svg)](https://youzan.github.io/vant/#/zh-CN/intro)
[![Vant-weapp](https://img.shields.io/badge/vant--weapp-1.0.1-brightgreen)](https://youzan.github.io/vant-weapp/#/intro)
[![Flutter](https://img.shields.io/badge/Flutter-1.9.6-brightgreen)](https://flutter.dev/)
[![license](https://img.shields.io/github/license/mashape/apistatus.svg)](https://github.com/enilu/linjiashop/blob/master/LICENSE)
[![Gitee stars](https://gitee.com/microapp/linjiashop/badge/star.svg?theme=social)](https://gitee.com/microapp/linjiashop)
[![GitHub stars](https://img.shields.io/github/stars/microapp-store/linjiashop.svg?style=social&label=Stars)](https://github.com/microapp-store/linjiashop)
 


- linjiashop 是一个基于[Spring Boot](https://spring.io/projects/spring-boot/)和[Vue.js](https://cn.vuejs.org)的web商城系统
- linjiashop 包含了商城的后台管理系统,手机h5，小程序版本
- linjiashop 包含了app版本（基于flutter) 仓库地址[gitee](https://gitee.com/microapp/linjiashop-flutter),[github](https://github.com/microapp-store/linjiashop-flutter) 
 

## 功能模块
linjiashop包含了后台管理功能和手机端商城业务功能
- 基础模块
    - 部门管理
    - 用户管理
    - 角色管理
    - 菜单管理
    - 权限分配
    - 参数管理
    - 数据字典管理
    - 定时任务管理
    - 操作日志
    - 登录日志
    - cms内容管理
    - 消息管理：配置消息模板，发送短信，邮件消息
    - 基于idea插件的代码生成
- 商城功能
    - 店铺管理
    - 类别管理
    - 商品管理    
    - 订单管理
    - 购物车列表
- 手机端
    -完整的商城购物功能        

## 运行效果图
### 手机端H5
![手机端](doc/img/mobile.gif)

### IOS
 
 
 
  
 
  
 
 
 
  
 
  
 
 
 
  
 
  
 
 

### Android
![效果](doc/img/app/mobile.gif)

### 后台管理
![后台管理](doc/img/admin.gif)
## 演示
- 手机版本：[http://linjiashop.microapp.store](http://linjiashop.microapp.store)
- 后台管理：[http://linjiashop-admin.microapp.store](http://linjiashop-admin.microapp.store) 请不要随意删除测试数据，谢谢

## 技术选型
- 核心框架：Spring Boot
- 数据库层：Spring data jpa
- 数据库连接池：Druid
- 缓存：Ehcache
- 前端：后台管理基于[element](http://element-cn.eleme.io)，手机端界面基于[vant](https://youzan.github.io/vant/#/zh-CN/intro)


## 目录说明
- linjiashop-admin PC端后台管理的前端网页
- linjiashop-admin-api PC端后台管理的api服务
- linjiashop-mobile 手机商城的前端网页
- linjiashop-mobile-api 移动端商城的api服务（h5,小程序，app都用改api服务作为后台接口）
- linjiasho-wxapp 微信小程序商城
- linjiashop-core 基础模块，包括工具类，dao，service，bean等内容
- linjiashop-generator 代码生成模块,根据实体生成dao,service,后台管理的controller和页面,配合IDEA 代码生成插件[webflash-generator](https://plugins.jetbrains.com/plugin/12648-webflash-generator)使用效果更好


## 快速开始
- 克隆本项目
- 导入idea或者eclipse
- 确保开发工具下载并安装了lombok插件
- 创建数据库：linjiashop
     ```sql
    CREATE DATABASE IF NOT EXISTS linjiashop DEFAULT CHARSET utf8 COLLATE utf8_general_ci; 
    CREATE USER 'linjiashop'@'%' IDENTIFIED BY 'linjiashop191028';
    GRANT ALL privileges ON linjiashop.* TO 'linjiashop'@'%';
    flush privileges;
    ```     
- 下载项目测试数据的图片：链接：链接：[https://pan.baidu.com/s/1Ppfgy2wR1nW0l-QMYHFGKw](https://pan.baidu.com/s/1Ppfgy2wR1nW0l-QMYHFGKw) 提取码：wo8q ，将图片存放到t_sys_cfg表中system.file.upload.path配置的目录下
- 启动后台管理
    - 启动后台管理api服务:linjiashop-admin-api
        - 修改linjiashop-admin-api中数据库连接配置
            ```properties
            ## 首次启动需要设置下列配置项设置为create，以便系统可以自动创建表并导入./import.sql测试数据文件
            ## 如果下面配置无法自动建表并导入测试数据文件；则可以手动初始化数据库，手动使用的初始化文件文件位于：doc/database.sql
            spring.jpa.hibernate.ddl-auto=create
            ```                    
        - 启动linjiashop-admin-api主类：cn.enilu.flash.api.AdminApiApplication，访问http://localhost:8082/swagger-ui.html ， 保证api服务启动成功
    - 启动后台管理的前端界面:linjiashop-admin
        - 运行 npm install --registry=https://registry.npm.taobao.org
        - 运行npm run dev
        - 启动成功后访问 http://localhost:9528 ,登录，用户名密码:admin/admin 
- 启动手机端商城
    - 启动手商城的api服务:linjiashop-mobile-api   
        - 修改linjiashop-mobile-api中数据库连接欸配置
        - 启动linjiashop-mobile-api主类：cn.enilu.flash.MobileApiApplication,访问http://localhost:8081/swagger-ui.html ， 保证api服务启动成功
    - 启动手机商城的前端:linjiashop-mobile
        - 运行 npm install --registry=https://registry.npm.taobao.org
        - 运行npm run dev
        - 启动成功后访问 http://localhost:8080/#/index
- 微信小程序开发
    - 首先启动后台api服务，和h5公用一个后台服务，即：linjiashop-mobile-api
    - 进入linjiashop-wxapp目录
        - 运行  npm install --registry=https://registry.npm.taobao.org
        - 运行npm run dev
        - 启动微信开发工具打开linjiashop-wxapp/dist/wx 目录即可预览小程序
 
## 技术交流
- QQ群：254059156
- 微信：myenilu,添加请备注：邻家小铺
## 在线文档
- 项目文档：[http://microapp.gitee.io/linjiashop](http://microapp.gitee.io/linjiashop/)
- 该项目克隆并扩展自[web-flash](https://github.com/enilu/web-flash),所以开发的时候多看看web-flash的[在线文档](http://enilu.gitee.io/web-flash)
- 该项目手机端linjiashop-mobile使用有赞Vant组件库，开发过程可以参考Vant的[在线文档](https://youzan.github.io/vant/#/zh-CN/intro)
- 该项目微信小程序使用mpvue+vant-weapp，开发过程请参考相关文档：[mpvue文档](http://mpvue.com/),[vant-weapp文档](https://youzan.github.io/vant-weapp/#/intro)
- 该项目的业务功能参考[litemall](https://github.com/linlinjava/litemall)，感谢[linlinjava](https://github.com/linlinjava)
 


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)