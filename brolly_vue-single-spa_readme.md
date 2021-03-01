# vue-single-spa 

**基于vuejs为底座，single-spa 为框架的微前端示例工程**

## 说明

**子项目均在 subprojects内, 三个项目互不关联，相互隔离。**
> * 本示例主要说明，微前端的简单示例，和如何远程加载微前端模块，所以需要启动三个项目工程
> * single-spa 配置文件在src/single-spa-config.js。vue & react 项目的入口文件均有注释
> * 如果还不了解，请前往single-spa.js 官网查阅文档
> * https://single-spa.js.org

## 安装步骤：

1. Vuejs：
    - cd sub-projects/sub-app-vuejs
    - yarn install / npm install / cnpm install
    - npm run serve-vue
2. React：
    - cd sub-projects/sub-app-react16
    - yarn install / npm install / cnpm install
    - npm run build
    - npm run serve-react
3. Angular：
    - cd sub-projects/sub-app-angular
    - yarn install / npm install / cnpm install
    - npm run build
    - npm run serve-angular
4. vue-single-spa-back:
    - yarn install / npm install / cnpm install
    - npm run serve-spa
    
## 端口示例：

- vuejs: 3000
- react: 3001
- angular: 3002


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)