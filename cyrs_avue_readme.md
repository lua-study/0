 
   
   
   
 


#### 简介

Avue是基于[Vue.js](https://github.com/vuejs/vue)和[element](https://github.com/ElemeFE/element)的快速开发框架 它的核心是数据驱动UI的思想，让我们从繁琐的crud开发中解脱出来，它的写法类似easyUI，但是写起来比easyui更容易，因为它是基础数据双向绑定以及其他vue的特性。同时不知局限于crud，它还有我们经常用的一些组件例如，表单，数据展示卡，人物展示卡等，更多的组件还在开发  

### avue2.x来了！！
avue2.x重磅来袭！与1.0.x版本截然不同！！  
[演示地址](https://cli2.avue.top)  
[源码获取](https://gitee.com/smallweigit/avue/wikis/vip )  

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

#### avue自定义第三方插件

[穿梭框](https://gitee.com/smallweigit/avue-plugin-transfer)  
[富文本编辑器](https://gitee.com/smallweigit/avue-plugin-ueditor)  

使用方式(以富文本编辑器为例)：  
* npm install avue-plugin-ueditor --save
* main.js导入import 'avue-plugin-ueditor/packages'
* 列的属性配置"component": "AvueUeditor" 你插件的全局名字即可


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

#### cli 1.x演示地址
- [演示地址](https://cli1.avue.top)

#### 技术文档
- [avue技术文档](https://www.kancloud.cn/smallwei/avue/)

#### 官方网站
- [avue官方网站](https://avue.top)

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
- 数据展示
- 登录/注销
 - 用户名登录
 - 验证码登录
 - 第三方登陆(QQ,微信)
- 权限验证
- 第三方网站嵌套
- CRUD(增删改查)
- FORM(动态生成)
- 阿里巴巴图标库(在线调用)
- tag标签操作
- 环境变量
- 表格树
- 引导页
- 数据持久化
- 剪切板
- 灰度化
- 系统管理
 - 用户管理
 - 角色管理
 - 菜单管理
- 高级路由
 - 动态路由
 - 参数路由
- 更多功能开在开发
```

### 部分页面展示

#### 登录页面
 


#### 首页页面
 

#### 炫彩主题
 


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
3.vue ui 运行管理工具，导入avue-cli项目  

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