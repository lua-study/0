# vue-single-spa 

**基于vuejs为底座，single-spa 为框架的微前端示例工程**

## 更新日志

- 2019.12.20: 支持使用子项目的manifest.json 自动加载所需要的js文件（请重新install vue子项目 和 父项目）
- 2019.12.18: vue，react子项目支持任何环境下独立运行（请重新build dist文件）
- 2019.12.17: 解决不同语言服务切换时造成的服务无法挂载问题
- 2019.12.12: 样式隔离，父项目控制子项目路由跳转 （需要切换到子vue项目，重新npm install 一下）
- 2019.10.27: 父子项目分离，远程加载

## 说明

**子项目均在 subprojects内, 三个项目互不关联，相互隔离。**
> * 本示例主要说明，微前端的简单示例，和如何远程加载微前端模块，所以需要启动三个项目工程
> * single-spa 配置文件在src/single-spa-config.js。vue & react 项目的入口文件均有注释
> * 如果还不了解，请前往single-spa.js 官网查阅文档
> * https://single-spa.js.org

## 安装步骤：

### 1. Vuejs：
    - cd sub-projects/sub-app-vuejs
    - yarn install / npm install / cnpm install
    - npm run serve-vue
### 2. React：
    - cd sub-projects/sub-app-react16
    - yarn install / npm install / cnpm install
    - npm run build
    - npm run serve-react
### 3. Angular：
    - cd sub-projects/sub-app-angular
    - yarn install / npm install / cnpm install
    - npm run build
    - npm run serve-angular
### 4. vue-single-spa-back:
    - yarn install / npm install / cnpm install
    - npm run serve-spa
    
## 端口：

- vuejs: 3000
- react: 3001
- angular: 3002

## 个人微信

![欢迎添加微信探讨](https://images.gitee.com/uploads/images/2019/1212/225746_010d72cb_1957979.jpeg "WechatIMG91.jpeg")


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)