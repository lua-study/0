English | [简体中文](./README.zh-CN.md)

 Ant Design Pro Vue 

 
An out-of-box UI solution for enterprise applications as a Vue boilerplate. based on   Ant Design of Vue 
 

 

[![License](https://img.shields.io/npm/l/package.json.svg?style=flat)](https://github.com/sendya/ant-design-pro-vue/blob/master/LICENSE)
[![Release](https://img.shields.io/github/release/sendya/ant-design-pro-vue.svg?style=flat)](https://github.com/sendya/ant-design-pro-vue/releases/latest)
[![Travis branch](https://travis-ci.org/sendya/ant-design-pro-vue.svg?branch=master)](https://travis-ci.org/sendya/ant-design-pro-vue)
[![All Contributors](https://img.shields.io/badge/all_contributors-10-orange.svg?style=flat-square)](#contributors)

 

- Preview: https://preview.pro.loacg.com
- Home Page: https://pro.loacg.com
- Documentation: https://pro.loacg.com/docs/getting-started
- ChangeLog: https://pro.loacg.com/docs/changelog
- FAQ: https://pro.loacg.com/docs/faq

Overview
----

![dashboard + multi-tabs](https://static-2.loacg.com/open/static/github/20190224163345.jpg)

![dashboard + setting](https://static-2.loacg.com/open/static/github/20181126112124.png)

![user profile](https://static-2.loacg.com/open/static/github/20180916-134251.png)

![permission list](https://static-2.loacg.com/open/static/github/20180916-154937.png)


### Env and dependencies

- node
- yarn
- webpack
- eslint
- @vue/cli ~3
- [ant-design-vue](https://github.com/vueComponent/ant-design-vue) - Ant Design Of Vue 
- [vue-cropper](https://github.com/xyxiao001/vue-cropper) - Picture edit
- [@antv/g2](https://antv.alipay.com/zh-cn/index.html) - AntV G2
- [Viser-vue](https://viserjs.github.io/docs.html#/viser/guide/installation)  - Antv/G2 of Vue

> Note:  [Yarn](https://yarnpkg.com/) package management is recommended, the exact same version loaded with the demo site of this project (yarn.lock) . but you can also use npm


### Project setup

- Clone repo
```bash
git clone https://github.com/sendya/ant-design-pro-vue.git
cd ant-design-pro-vue
```

- Install dependencies
```
yarn install
```

- Compiles and hot-reloads for development
```
yarn run serve
```

- Compiles and minifies for production
```
yarn run build
```

- Lints and fixes files
```
yarn run lint
```


### Other

- **IMPORTANT : About Issue feedback !! Please describe your environment, the Pro version or branch used, what happened, etc. when opening Issue**

- [Vue-cli3](https://cli.vuejs.org/guide/) used by the project.
- Disable Eslint (not recommended): remove `eslintConfig`  field in `package.json` 

- Easy-Mock used by project，[easy-mock](https://www.easy-mock.com/)  Project API Data [DO NOT CHANGE THE INTERFACE](https://www.easy-mock.com/project/5b7bce071f130e5b7fe8cd7d)，If you want to modify, please fork [ANTD-PRO-Easy-Mock-API.zip](https://github.com/sendya/ant-design-pro-vue/files/2682711/ANTD-PRO-Easy-Mock-API.zip) and running to your server.

- Load on Demand: modify `/src/main.js` L7,  append `import './core/lazy_use'` code.

- Customize Theme:  `vue.config.js` 
eg: 
```ecmascript 6
  css: {
    loaderOptions: {
      less: {
        modifyVars: {
          /* Less variables, required modifyVars*/

          'primary-color': '#F5222D',
          'link-color': '#F5222D',
          'border-radius-base': '4px',
        },
        javascriptEnabled: true,
      }
    }
  }
```
- **polyfill**

- remove polyfill: 
  > [Vue CLI Polyfill](https://cli.vuejs.org/zh/guide/browser-compatibility.html#usebuiltins-usage)
  
  - remove `import '@babel/polyfill'`  field in  `src/main.js`
  - `babel.conflg.js` remove
    ```ecmascript 6
    [
      '@babel/preset-env',
      {
        'useBuiltIns': 'entry'
      }
    ]
    ```


Docs
----

- [Router and Menu](https://github.com/sendya/ant-design-pro-vue/blob/master/src/router/README.md)
- [Table](https://github.com/sendya/ant-design-pro-vue/blob/master/src/components/table/README.md) [@Saraka](https://github.com/saraka-tsukai)
- [ANTD DefaultConfig](https://github.com/sendya/ant-design-pro-vue/blob/master/src/defaultSettings.js)
- [Frist page loading animate](https://github.com/sendya/ant-design-pro-vue/blob/master/docs/add-page-loading-animate.md)
- [Multi-Tabs feature/multi-tabs](https://github.com/sendya/ant-design-pro-vue/tree/feature/multi-tabs) [How to remove](https://github.com/sendya/ant-design-pro-vue/blob/master/docs/multi-tabs.md)
- [LoadOnDemand Demo feature/demand_load](https://github.com/sendya/ant-design-pro-vue/tree/feature/demand_load)
- [LoadOnDemand Docs](https://github.com/sendya/ant-design-pro-vue/blob/master/docs/load-on-demand.md)  
- [i18n feature/lang](https://github.com/sendya/ant-design-pro-vue/tree/feature/lang)  Creator [@musnow](https://github.com/musnow)
- [Dependency analysis tool: analyzer](https://github.com/sendya/ant-design-pro-vue/blob/master/docs/webpack-bundle-analyzer.md)  
- ANTD PRO Components:
  - Trend [Trend.md](https://github.com/sendya/ant-design-pro-vue/blob/master/src/components/Trend/index.md)
  - AvatarList [AvatarList.md](https://github.com/sendya/ant-design-pro-vue/blob/master/src/components/AvatarList/index.md)
  - CountDown [CountDown.md](https://github.com/sendya/ant-design-pro-vue/blob/master/src/components/CountDown/index.md)
  - Ellipsis [Ellipsis.md](https://github.com/sendya/ant-design-pro-vue/blob/master/src/components/Ellipsis/index.md)
  - NumberInfo [NumberInfo.md](https://github.com/sendya/ant-design-pro-vue/blob/master/src/components/NumberInfo/index.md)
  - FooterToolbar [FooterToolbar.md](https://github.com/sendya/ant-design-pro-vue/blob/master/src/components/FooterToolbar/index.md)
  - IconSelector [IconSelector.md](https://github.com/sendya/ant-design-pro-vue/blob/master/src/components/IconSelector/README.md) Creator: [@Saraka](https://github.com/saraka-tsukai)
- doing...


## Contributors

Thanks goes to these wonderful people ([emoji key](https://github.com/all-contributors/all-contributors#emoji-key)):

 
 
| [    言肆  ](https://i.loacg.com) [💻](https://github.com/sendya/ant-design-pro-vue/commits?author=sendya "Code") [📖](https://github.com/sendya/ant-design-pro-vue/commits?author=sendya "Documentation") | [    晴心  ](https://github.com/kokoroli) [💻](https://github.com/sendya/ant-design-pro-vue/commits?author=kokoroli "Code") [📖](https://github.com/sendya/ant-design-pro-vue/commits?author=kokoroli "Documentation") | [    musnow  ](https://github.com/musnow) [💻](https://github.com/sendya/ant-design-pro-vue/commits?author=musnow "Code") | [    zkwolf  ](https://github.com/zkwolf) [💻](https://github.com/sendya/ant-design-pro-vue/commits?author=zkwolf "Code") | [    土拨鼠  ](https://github.com/mcmf) [💻](https://github.com/sendya/ant-design-pro-vue/commits?author=mcmf "Code") | [    阿凌  ](https://github.com/AClumsy) [💻](https://github.com/sendya/ant-design-pro-vue/commits?author=AClumsy "Code") | [    mynuolr  ](https://github.com/mynuolr) [💻](https://github.com/sendya/ant-design-pro-vue/commits?author=mynuolr "Code") |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: |
[    Saraka  ](https://github.com/saraka-tsukai) [💻](https://github.com/sendya/ant-design-pro-vue/commits?author=saraka-tsukai "Code") [🔧](https://github.com/sendya/ant-design-pro-vue) | [    since2006  ](https://github.com/since2006) [💻](https://github.com/sendya/ant-design-pro-vue/commits?author=since2006 "Code") | [    挥手的骑士  ](https://github.com/yihuishou) [💻](https://github.com/sendya/ant-design-pro-vue/commits?author=yihuishou "Code") |
 


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)