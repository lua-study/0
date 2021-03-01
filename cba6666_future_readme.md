# future
- 一个完整的saas外卖系统，包括手机端，后台管理,手机端可以打包成app
- 基于spring boot和vue的前后端分离的外卖系统
- 包含完整的手机端，后台管理功能

## 技术选型
- 核心框架：Spring Boot
- 数据库层：mybatis
- 数据库连接池：Druid
- 搜索: essearch
- 缓存：redis
- 消息队列: rabbitmq(订单15分钟失效)
- 前端：Vue.js
- 数据库：mysql5.5以上

## 模块
- flash-waimai-mobile 手机端
- ruoyi-ui 后台管理系统
- ruoyi java接口服务

## 快速开始
- 数据存储采用了mysql和mysql，其中基础管理配置功能数据使用mysql，业务数据使用redis存储。

- 下载项目测试数据的图片（商家和食品图片）：链接：https://pan.baidu.com/s/1rvZDspoapWa6rEq2D_5kzw 提取码：urzw ，将图片存放到t_sys_cfg表中system.file.upload.path配置的目录下

- 启动管理平台:
    - 进入ruoyi目录：
    - 运行 npm install --registry=https://registry.npm.taobao.org
    - 运行npm run dev
    - 启动成功后访问 http://localhost:8770 ,登录，用户名密码:admin/admin123
- 启动手机端:
    - 进入flash-waimai-mobile目录：    
    - 运行 npm install --registry=https://registry.npm.taobao.org
    - 运行npm run local
    - 启动成功后访问 http://localhost:8000
    - 用户名密码 admin/admin123

## 运行效果图
- 后台管理
![admin](doc/admin.gif)
- 手机端    
![mobile](doc/mobile.gif)
- 安卓app扫码    
![android](doc/ma.png)

## 在线演示
- 后台管理：[http://47.100.225.158:8770](http://47.100.225.158:8770)
- 手机端:[http://47.100.225.158:8769](http://47.100.225.158:8769)



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)