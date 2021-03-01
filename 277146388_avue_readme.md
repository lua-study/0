 
   
   
   
 


#### 简介

Avue是基于[Vue.js](https://github.com/vuejs/vue)和[element](https://github.com/ElemeFE/element)的快速开发框架 它的核心是数据驱动UI的思想，让我们从繁琐的crud开发中解脱出来，它的写法类似easyUI，但是写起来比easyui更容易，因为它是基础数据双向绑定以及其他vue的特性。同时不知局限于crud，它还有我们经常用的一些组件例如，表单，数据展示卡，人物展示卡等，更多的组件还在开发  

### avue2.x来了！！
avue2.x重磅来袭！与1.0.x版本截然不同！！  
不只是后台模板解决方案，更像是页面开发神器，积木拼装的概念，简单的拼装快速实现业务场景复杂的需求  
  
核心:数据驱动视图  
  
亮点:  
1.只需要配置简单的json属性，即可实现复杂的页面  
2.配置不同的属性，实现不同的控件效果和业务逻辑（需要一个上传图片的功能，配置属性为upload,和图片上传后台接口即可)  
3.配置字典接口，全局字典自动加载无需操心label和value值的对应
4.简单配置即可实现分步骤表单提交，多选项卡表单提交，等其他复杂的表单  
5.不需要写大量html和css，只需要一个json即可完成你的页面  
6.解放手写大量重复crud和form表单功能，只要维护一个json就好  
7.让你轻松完成工作，有更多的时间去泡妹子  
  
演示地址:[http://122.4.247.156:8000/#/login](http://122.4.247.156:8000/#/login)  
重点在form表单和crud表格

适合人群:  
1.常年撸后端，对前端页面有恐惧心里  
2.刚入门vue，需要写一些复杂的业务场景  
3.干着大量重复的crud，机械式劳动，浪费时间  
4.前端小白，没用过很多框架，没有很多经验  

[点击查看详情](https://gitee.com/smallweigit/avue/wikis/vip )

#### 百度云课程
 
   
 

- [B站视频](https://www.bilibili.com/video/av24644922)
- [1.Avue修仙系列之基础环境的准备和课程介绍](https://pan.baidu.com/s/1ZBgYby4K8yQC3U4mevuk8A)
- [2.Avue修仙系列之avue-crud组件type属性介绍](https://pan.baidu.com/s/1jo1yx128sSJgnRnECtvEEw#list/path=%2F)
- [3.Avue修仙系列之avue-crud本地字典的使用方法](https://pan.baidu.com/s/1i193Ced5d65_i1wXdVSchQ)
- [4.Avue修仙系列之avue-crud后台接口字典的使用方法](https://pan.baidu.com/s/1TKZSu4K6mac4wio8qDdFJQ)
- 未完待续

#### avue综合实际实例
- [crud综合例子](http://sandbox.runjs.cn/show/xjjyj1cj)
- [crud流程例子](https://sandbox.runjs.cn/show/hnhjz9wn)
- [crud多级联动例子](https://sandbox.runjs.cn/show/vigm1mvl)
- [crud动态切换](https://sandbox.runjs.cn/show/e5kht8ed)
- 未完待续

#### avue相关地址
欢迎加入QQ交流群，互相学习   
前端avue交流群：606410437  
后台微服务群：23754102   
服务端解决方案：[https://gitee.com/log4j/pig](https://gitee.com/log4j/pig)   
刚入门的前端小师妹博客:[https://my.oschina.net/u/3883702/](https://my.oschina.net/u/3883702/)   
最近很多人反应不太会用crud快速开发组件，因此免费推出crud系列的讲解课程，详情请加QQ群

#### avue-cli 1.x演示地址
- [演示地址1:http://avue.2bugs.cn](http://avue.2bugs.cn)
- [演示地址2:http://122.4.247.156:7777](http://122.4.247.156:7777)

#### 技术文档
- [avue技术文档](https://www.kancloud.cn/smallwei/avue/)

#### 在线例子
- [avue在线例子](http://122.4.247.156:7000)

#### json管理平台
- [avue组件json管理平台](http://122.4.247.156:5555)

#### 源码地址
- [码云地址:https://gitee.com/smallweigit/avue](https://gitee.com/smallweigit/avue)
- [github地址：https://github.com/nmxiaowei/avue](https://github.com/nmxiaowei/avue)

#### 更新日志
本项目以更新到最新的vue-cli@3.0的脚手架，更多使用请去vue官方查看  
- [更新日志](./UPDATE.md)

### Avue
基于数据驱动视图的思想，根据json数据快速构建crud和form等组件  
依赖包:  
* axios：发送ajax数据用到的包
* element-ui：可视化UI组件
* 引入avue之前先引入上面这俩个包

#### CDN
```
 

  

#### npm
npm i @smallwei/avue --save

#### yarn
yarn add @samallwei/avue --save

```

#### 使用方式
```
import Element from 'element-ui'
import axios from 'axios'
import Avue from @smallwei/avue/lib/index.js
import @smallwei/avue/lib/theme-chalk/index.css

Vue.use(Element);
Vue.use(Avue,axios)

```

#### 功能结构
```
- 全局错误日志记录
- vuex持久化存储
- 主题色切换
- 锁屏
- SSR渲染页面
- 数据展示
- 登录/注销
 - 用户名登录
 - 验证码登录
- 权限验证
- 第三方网站嵌套
- CRUD(增删改查)
- FORM(动态生成)
- 阿里巴巴图标库(在线调用)
- 环境变量
- 表格树
- 引导页
- 数据持久化
- 剪切板
- 系统管理
 - 用户管理
 - 角色管理
 - 菜单管理
- 高级路由
 - 动态路由
 - 参数路由
- 更多功能开在开发
```

### 页面展示 （点击可大图预览）
 
     
         炫彩主题  
         主题色  
     
     
         数据持久化  
         环境变量  
     
     
         表格树  
         登录  
     
     
         权限测试  
         数据展示  
     
     
         错误页面  
         错误日志  
     
      
         CRUD  
         FORM  
     
     
         阿里巴巴图标库(在线调用)  
         主页  
     
 


#### 开发
```bash
# 克隆项目
git clone https://gitee.com/smallweigit/avue.git

# 进入项目
cd avue

# 安装依赖
npm install --registry=https://registry.npm.taobao.org

# 启动服务
npm run serve

```


#### vue-ui启动
```bash
1.npm install -g @vue/cli 全局安装vue脚手架最新版  
2.vue --version 查看版本是否为3.x版本  
3.vue-ui 运行管理工具，导入avue-cli项目  

```


#### 调试与发布
```bash
# 构建测试环境
npm run serve

# 构建生成环境
npm run build

```


#### 其它
```bash
# 代码检测
npm run lint

# 单元测试
npm run test:unit2
```

#### 友情链接
- [d2-admin](https://github.com/FairyEver/d2-admin)

#### License
[MIT](https://gitee.com/smallweigit/avue/blob/master/LICENSE)

Copyright (c) 2017-present Smallwei


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)