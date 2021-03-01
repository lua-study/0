 
      
     
 
 
     
 

 Lightweight Mobile UI Components built on Vue 

 
     
     
     
     
     
     
     
 

 
  🇨🇳  访问中文版 
  &nbsp;
  🚀  Vant Weapp - 小程序版 
 

---

## Features

* 50+ Reusable components
* 80%+ Unit test coverage
* Extensive documentation and demos
* Support [babel-plugin-import](https://github.com/ant-design/babel-plugin-import)
* Support TypeScript
* Support SSR

## Install

#### NPM

```shell
npm i vant -S
```

#### YARN

```shell
yarn add vant
```

#### CDN

```html
 
 

 
  
  
```

## Quickstart

#### 1. Use [babel-plugin-import](https://github.com/ant-design/babel-plugin-import) (Recommended)

```bash
# Install babel-plugin-import
npm i babel-plugin-import -D
```

```js
// set babel config in .babelrc or babel-loader
// Note: Don't set libraryDirectory if you are using webpack 1.
{
  "plugins": [
    ["import", {
      "libraryName": "vant",
      "libraryDirectory": "es",
      "style": true
    }]
  ]
}
```

Then you can import components from vant, equivalent to import manually below.

```js
import { Button } from 'vant';
```

> If you are using TypeScript，please use [ts-import-plugin](https://github.com/Brooooooklyn/ts-import-plugin) instead

#### 2. Manually import

```js
import Button from 'vant/lib/button';
import 'vant/lib/vant-css/base.css';
import 'vant/lib/vant-css/button.css';
```

#### 3. Import all components

```js
import Vue from 'vue';
import Vant from 'vant';
import 'vant/lib/vant-css/index.css';

Vue.use(Vant);
```

> If you configured babel-plugin-import, you won't be allowed to import all components.

See more in [Quickstart](https://youzan.github.io/vant#/en-US/quickstart).

## Contribution

Please make sure to read the [Contributing Guide](./.github/CONTRIBUTING.md) before making a pull request.

## Browser Support

Modern browsers and Android 4.0+, iOS 6+.

## Links

* [Documentation](https://youzan.github.io/vant)
* [Changelog](https://youzan.github.io/vant#/en-US/changelog)
* [Vant Demo](https://github.com/youzan/vant-demo)
* [Vant Weapp: Weapp UI](https://github.com/youzan/vant-weapp)
* [Zent: PC UI base on React](https://www.youzanyun.com/zanui/zent)


## Preview

You can scan the following QR code to access the demo：

 

## Wechat Group

Scan the qrcode to join our wechat discussion group, please note that you want to join Vant discussion group.

 

## LICENSE

[MIT](https://zh.wikipedia.org/wiki/MIT%E8%A8%B1%E5%8F%AF%E8%AD%89)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)