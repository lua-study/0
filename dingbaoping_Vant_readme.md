 
      
     
 
 
     
 
 A Vue.js 2.0 Mobile UI at YouZan 

[![Build Status](https://travis-ci.org/youzan/vant.svg?branch=master)](https://travis-ci.org/youzan/vant) [![Coverage Status](https://img.shields.io/codecov/c/github/youzan/vant/dev.svg)](https://codecov.io/github/youzan/vant?branch=dev) [![npm version](https://img.shields.io/npm/v/vant.svg?style=flat)](https://www.npmjs.com/package/vant) [![downloads](https://img.shields.io/npm/dt/vant.svg)](https://www.npmjs.com/package/vant) 
 
[访问中文版](./README.zh-CN.md)

## Install

```shell
npm i -S vant
```
 
## Usage

### Use [babel-plugin-import](https://github.com/ant-design/babel-plugin-import) (Recommended)

   ```js
   // .babelrc or babel-loader option
   {
     "plugins": [
       ["import", { "libraryName": "vant", "style": true }]
     ]
   }
   ```

   Then you can import components from vant, equivalent to import manually below.

   ```js
   // import js and css modularly, parsed by babel-plugin-import
   import { Button } from 'vant';
   ```

### Manually import

   ```jsx
   import { Button } from 'vant';
   import 'vant/lib/vant-css/button.css';
   ```
 
 
### Import all components
 
```javascript
import Vue from 'vue';
import vant from 'vant';
import 'vant/lib/vant-css/index.css';

Vue.use(vant);
```
 
## Development

### Add a new component

```shell
make init componentName
```

### Start coding

Start development mode:

```shell
npm run dev
```

Visit [http://localhost:8080](http://localhost:8080) to see an example of all components.

## Preview

You can scan the following QR code to access the demo：

![zanui_vue_mobile_qrcode](https://img.yzcdn.cn/v2/image/youzanyun/zanui/pc/zanui_vue_mobile_preview_03.png)
 
## LICENSE

[MIT](https://zh.wikipedia.org/wiki/MIT%E8%A8%B1%E5%8F%AF%E8%AD%89)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)