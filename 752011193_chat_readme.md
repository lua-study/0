# JwChat

#### 介绍
**一款基于Vue和ElementUI极简的聊天框组件**
本项目是一款极简的数据驱动为主的聊天框组件。
新增表情包可自动匹配微信表情。
新增聊天窗口配置组件，可以自由配置 顶部状态栏 和 右侧信息栏

![](./document/img/20200505.gif)

#### 安装

* 使用 `npm` 安装

  ``` bash
  npm install jwchat
  ```

* 使用 `yarn` 安装

  ``` bash
  yarn add jwchat
  ```

#### 使用

1. 因为本组件是基于 `element-ui` 开发。首先需要引入  `element-ui`。

   ```bash
   npm install element-ui
   ```

2. 在 `main.js` 中引入组件

   ``` js
   import ElementUI from 'element-ui';
   import 'element-ui/lib/theme-chalk/index.css';
   Vue.use(ElementUI);
   
   import Chat from 'jwchat';
   import 'jwchat/lib/JwChat.css';
   Vue.use(Chat)
   ```

3. 在 `*.vue` 中引入

   ``` vue
    
   ```
   
#### 文档
* [**官方文档**](https://codegi.gitee.io/jwchatdoc/)


#### 参与贡献

1.  Fork 本仓库
2.  新建 Feat_xxx 分支
3.  提交代码
4.  新建 Pull Request

#### 声明

* 本代码借鉴于[AVue](https://avuejs.com/)


#### 交流学习

* QQ群 ：235689934

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)