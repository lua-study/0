# vue-admin

## 环境依赖

- node v6.9.5
- webpack v2.3.1
- vue-cli v2.8.2

## 项目简介

1、webpack配置项

- Vue利用proxyTable实现跨域请求（反向代理）；
- webpack利用HtmlWebpackPlugin实现多页面应用；
- webpack使用build打包项目生成静态资源到nginx服务上运行；


2、前端页面配置项

- 使用less构建前端样式
- 使用vue组件式开发，各个vue文件都可以成为独立的一个模块，供全局使用
- 使用iview作为前端UI框架库
- 模块插件库
  - marked作为渲染markdown文件为html页面；
  - 使用highlight高亮代码块；
  - 弹窗、tips、进度条均为iview框架提供的UI组件；
- 使用lib-flexible + rem 实现移动端屏幕适配  

## 项目运行

```bash
$ npm install  

$ npm run dev

$ npm run build
```

## 项目运行地址

项目开发环境：[http://localhost:8091/#/login](http://localhost:8091/#/login) 或者 [http://localhost:8091/index.html#/login](http://localhost:8091/index.html#/login)

## 目录结构描述

```
├── Readme.md                       帮助文档
├── build                           项目构建(webpack)相关代码
│   ├── build.js                    生产环境构建代码
│   ├── check-versions.js           检查node&npm等版本
│   ├── dev-client.js               热加载相关
│   ├── dev-server.js               构建本地服务器
│   ├── utils.js                    构建配置公用工具
│   ├── vue-loader.conf.js          vue加载器
│   ├── webpack.base.conf.js        webpack基础环境配置
│   ├── webpack.dev.conf.js         webpack开发环境配置
│   └── webpack.prod.conf.js        webpack生产环境配置
├── config                          项目开发环境配置相关代码 
│   ├── dev.env.js                  开发环境变量
│   ├── index.js                    项目一些配置变量
│   └── prod.env.js                 生产环境变量
├── dist                            打包后文件
├── src                             源码目录
│   ├── assets                      系统静态源文件
│   ├── components                  多系统公用的组件（树形、弹窗、tips、进度条、文件上传等组件）
│   └── entry                       多页应用入口
│       └── admin                   vue-admin后台
│            │── components          vue-admin公共组件
│            │── router              vue-admin公路由文件
│            │── store               vue-adminvuex文件夹
│            │── index.html          vue-adminhtml文件
│            │── admin.js            vue-admin程序入口文件（入口js文件）
│            └── admin.vue           vue-admin页面入口文件（根组件）
├── static                          静态文件，比如一些图片，json数据等
├── .babelrc                        ES6语法编译配置
├── .editorconfig                   定义代码格式
├── .gitignore                      git上传需要忽略的文件格式
├── .postcssrc.js                   css3样式补充
└── package.json                    项目基本信息
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)