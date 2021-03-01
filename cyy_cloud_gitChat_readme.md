## 社交聊天系统（vue + node + mongodb）- Vchat

## 一.项目需求说明

## 1. 登陆注册

### 	目前只支持验证码登录注册

## 2.加好友，通过ID或者昵称添加好友

## 3.生日提醒 好友相识天数 to-do list

## 4.在线聊天 点亮爱心 许愿墙

## 5.礼物商城 电影商城 音乐商城 

## 6.日记 相册

## 二.项目架构

- 技术栈 

> 前端主要采用了vue全家桶，没什么多说的，脚手架构建项目，vuex状态管理，vue-router控制路由，axios进行前后端交互。后端是基于node搭的服务，用的是express。聊天最重要的当然是通信，项目用[socket.io](https://www.w3cschool.cn/socket/socket-1olq2egc.html)来进行前后端通信。

> 数据库是mongoDB，主要有用户、好友、群聊、消息、表情、号码池等。

- 功能概览
- 目录结构

```
    // 前端
    ├─build
    ├─config
    ├─src
    │  ├─api                                  // 接口api
    │  ├─assets                               // 静态资源
    │  │  └─img
    │  ├─directives                           // 全局指令
    │  ├─libs                                 // 全局组件
    │  │  ├─bscroll
    │  │  ├─dropdown
    │  │  ├─icon
    │  │  ├─nodata
    │  │  ├─PhotoSwipe
    │  │  ├─uploadPopover
    │  │  └─vScroll
    │  ├─router                                // 路由
    │  ├─store                                 // 状态管理
    │  ├─utils                                 // 方法
    │  └─views
    │      ├─applicationModel
    │      │  ├─games                          // 游戏
    │      │  │
    │      │  └─sub                            // 应用
    │      ├─components                        // 组件
    │      │  ├─APlayer
    │      │  ├─chat
    │      │  ├─cropper
    │      │  ├─DPlayer
    │      │  └─header
    │      ├─personalModel                     // 主页
    │      │  ├─appModel                       // 天气等
    │      │  ├─friendModel                    // 好友
    │      │  └─groupModel                     // 群聊
    │      └─settingModel                      // 设置
    └─static
        ├─css                                  // 样式文件
        ├─font                                 // 字体文件
        └─theme                                // 主题
            └─vchat
```

## 三.项目启动

> ​	 注意必须要有node、npm以及mongodb，项目默认mongodb IP地址为localhost:27017，可以在配置文件中修改。（chatServer\utils\database.js） 

```
    git clone https://github.com/wuyawei/Vchat.git 
    cd chatRoom
    npm install 安装前端依赖
    npm run build 编译前端代码
    cd ..
    cd chatServer
    npm install 安装后端依赖
    npm run create 初始化数据库（号码池、表情包）
    npm start 启动服务
    在浏览器中打开 localhost:9988 即可
```



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)