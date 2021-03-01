# 前言

高仿饿了么，以nuxt作为vue的服务端渲染，适合刚接触或者准备上vue ssr的同学参考和学习

如遇网络不佳，请移步[国内镜像加速节点](https://gitee.com/easytuan/nuxt-elm)

# 效果演示

[查看demo请戳这里](https://elm.caibowen.net/)（请用chrome手机模式预览）

### 移动端扫描下方二维码

 

# API接口文档

[接口文档地址](https://easytuan.gitee.io/node-elm-api/doc)（基于apidoc）

# 技术栈

vue2 + vuex + vue-router + mint-ui + nuxt

## 项目运行

```

git clone git@github.com:EasyTuan/nuxt-elm.git

# 国内镜像加速节点:git@gitee.com:easytuan/node-elm-api.git

cd nuxt-elm

npm install

npm run dev

#模版快速生成
npm run tep `文件名`

# pm2部署
npm run start

```

## 补充

此项目有配套的后台系统，如果想体验前后台同时开发，可以下载对应的后台系统：[后台项目传送地址](https://github.com/EasyTuan/node-elm-api)。

如果只做前端开发，请忽略这句话。


# 目标功能
- [x] 商家列表 -- 完成
- [x] 购物车功能 -- 完成
- [x] 餐馆食品列表页 -- 完成
- [x] 店铺评价页面 -- 完成
- [x] 商家详情页 -- 完成
- [x] 登录、注册 -- 完成
- [x] 修改密码 -- 完成
- [x] 个人中心 -- 完成
- [x] 红包 -- 完成
- [x] 收货地址 -- 完成

# 业务介绍

目录结构

    ├── assets               // 静态资源
    │   ├── images                // 图片资源
    │   ├── services              // api请求
    │   ├── styles                // 样式文件
    │   └── utils                 // 常用工具类
    ├── components           // 组件
    ├── config
    │   └── index.js              // 配置文件
    ├── layouts              // 布局
    ├── middleware           // 中间件
    ├── pages                // 页面
    ├── plugins              // 插件
    ├── static               // 静态资源
    └── store                //vuex状态树


## 部分截图展示

### 首页展示

   

### 个人资料

   

### 我的

   

### 订餐

   

### 商家评价

   

# 说明

>  如果对您有帮助，您可以点右上角 "Star" 支持一下 谢谢！ ^_^

>  或者您可以 "follow" 一下，我会不断开源更多的有趣的项目

>  如有问题请直接在 Issues 中提，或者您发现问题并有非常好的解决方案，欢迎 PR 👍

# 开发日常记录

### nuxt模版搭建

这里关于项目初始化，我是直接使用的 `Nuxt` 官网提供的 starter 模板

```shell

# 安装 vue-cli
npm install -g vue-cli

# 初始化项目
vue init nuxt-community/starter-template nuxt-ssr-demo

# 安装依赖
cd nuxt-ssr-demo
npm install

# 启动本地服务
npm run dev

```

访问 http://localhost:3000 ，现在我们来看下初始化好的项目目录

```shell

├── assets                      // 静态资源
├── components                  // 全局组件
├── layouts                     // 页面布局
├── middleware                  // 中间件
├── pages                       // 路由页面
├── static                      // 静态资源，打包文件名不会被hash
├── store                       // vuex
├── nuxt.config.js              // nuxt配置文件
├── package.json
├── README.md

```

注意：nuxt默认会读取pages里面的vue文件，自动生成路由，如需要自定义路由，可在nuxt.config.js中配置对应参数。

### request请求封装

数据和展示层的剥离是有必要的，这也是为什么前端都提倡MV*的设计模式，而对request请求封装是我们第一步要完成的。这里我选了axios作为HTTP请求客户端，axios兼容浏览器端和node端，同时提供了请求拦截、响应拦截等让我们开发更加愉快的功能。

在 `config/index.js` 中写入：

```

const json = require('../package.json');
const port = json.config.nuxt.port;

module.exports = {
  IS_RELEASE: true, // true线上，false测试

  BASE_URL: `http://localhost:${port}/api`, // 测试

  // BASE_URL: `https://elm.caibowen.net/api`, // 生产

  // IMG_URL: 'http://localhost:9000/', // 测试

  IMG_URL: 'https://easytuan.gitee.io/node-elm-api/public/', // 生产（使用码云Gitee Pages 服务）

  HEADERS: {
    'Content-Type': 'application/json;charset=UTF-8'
  },

  TIMEOUT: 12000, // api超时时间

};

```

在 `assets/utils/request.js` 中写入：

```

import axios from 'axios';
import config from '~/config';
import { Toast } from 'mint-ui';

axios.defaults.baseURL = config.BASE_URL;
axios.defaults.timeout = config.TIMEOUT;
axios.defaults.headers = config.HEADERS;

// 请求拦截器
axios.interceptors.request.use( request => {
  if (!config.IS_RELEASE) {
    console.log(
      `${new Date().toLocaleString()}【 M=${request.url} 】P=`,
      request.params || request.data,
    );
  }
  return request;
}, error => {
  return Promise.reject(error);
});

export default async (options = { method: 'GET' }) => {
  let isdata = true;
  if (
    options.method.toUpperCase() !== 'POST'
    && options.method.toUpperCase() !== 'PUT'
    && options.method.toUpperCase() !== 'PATCH'
  ) {
    isdata = false;
  }
  const res = await axios({
    method: options.method,
    url: options.url,
    data: isdata ? options.data : null,
    params: !isdata ? options.data : null,
  });
  if (res.status >= 200 && res.status    

# 友情链接

[项目后台地址](https://github.com/EasyTuan/node-elm-api)

# License

[GPL](LICENSE)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)