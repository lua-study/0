# [Ystatic](http://www.yonglibao.com)
![Bower version](https://img.shields.io/bower/v/bootstrap.svg?style=flat)
[![npm version](https://img.shields.io/npm/v/bootstrap.svg?style=flat)](https://www.npmjs.com/package/bootstrap)
[![Build Status](https://img.shields.io/travis/twbs/bootstrap/master.svg?style=flat)](https://travis-ci.org/twbs/bootstrap)
[![devDependency Status](https://img.shields.io/david/dev/twbs/bootstrap.svg?style=flat)](https://david-dm.org/twbs/bootstrap#info=devDependencies)

[![Selenium Test Status](https://saucelabs.com/browser-matrix/bootstrap.svg)](https://saucelabs.com/u/bootstrap)

Ystatic简单文字介绍.

Get started  !

## 一、准备知识

- [nodejs](http://nodejs.org)
- [npm](https://www.npmjs.com/)
- [bower](http://bower.io/)
- [less](http://www.lesscss.net/)
- [grunt](http://www.gruntjs.net/)/[gulp](http://gulpjs.com/)
- [git](http://git-scm.com/)
- [more](docs/directory.md)

### 二、目的
- 让网站打开速度更快，用户体验更好；
- 让我们的网站的前端技术影响力更大；
- 让自身的开发效率更高。

### 三、途径
- 请求数更少；
- 静态资源更新自动化；
- css通过less管理；
- js和模板通过grunt/gulp管理；
- 连接数合并，nginx插件[http_concat](http://tengine.taobao.org/document_cn/http_concat_cn.html)。

### 四、网站目录结构

为了... You'll see something like this:

```
www.yonglibao.com/root
├── Aplication/
├── Core/
├── dist/
│   ├── static/
│   │   ├── lib/
│   │   │   ├── jquery/
│   │   │   ├── bxSlider/
│   │   │   ├── zepto/
│   │   │   └── ...
│   │   ├── fonts/
│   │   │   ├── yicon.eot
│   │   │   ├── yicon.svg
│   │   │   ├── yicon.ttf
│   │   │   └── yicon.woff
│   │   ├── images/
│   │   │   ├── public_img.jpg
│   │   │   ├── web/
│   │   │   ├── h5/
│   │   │   └── ...
│   │   ├── style/
│   │   │   ├──ylb.css
│   │   │   ├──ylb-touch.css
│   │   │   └──...
│   │   └── js/
│   │       ├── global.min.js
│   │       ├── home.min.js
│   │       └── ...
│   ├── tmpl
│   │   ├── web/
│   │   ├── h5/
│   │   ├── app/
│   │   ├── xieyi/
│   │   └── event/
│   │       ├── duanwu
│   │       │   ├── images/
│   │       │   ├── style/
│   │       │   ├── js/
│   │       │   ├── index.html
│   │       │   └── index_m.html
│   │       └── ...
├── src/
│   └── ...
└── test/
```

```
www.yonglibao.com/root
├── Admin/
├── Aplication/
├── Doc/
├── ThinkPHP/
├── event/
│   ├── 2014/
│   │   ├── zunxuan/
│   │   └── coffe/
│   │       ├──images/
│   │       ├──style/
│   │       ├──js/
│   │       └──index.html
│   └── 2015
├── template/
│   ├── pc
│   │   ├── html/纯静态，需配置nginx
│   │   │   ├──xieyi/
│   │   │   ├──aboutus/
│   │   │   ├──help/
│   │   │   └──index.html
│   │   └── other/
│   ├── touch/
│   └── app/
├── static/
│   ├── lib
│   │   ├── jquery/
│   │   ├── artTemplate/
│   │   └── bxSlider/
│   ├── js/
│   ├── fonts
│   │   ├── yicon.eot
│   │   ├── yicon.svg
│   │   ├── yicon.ttf
│   │   └── yicon.woff
│   ├── images
│   ├── less
│   │   ├── core/
│   │   │   └──不涉及展现的核心less方法
│   │   ├── config.less//预定颜色，文字大小
│   │   ├── pager.less
│   │   ├── ucenter.less
│   │   └── 各功能模块.less
│   ├── style
│   │    ├── ylb.css
│   │    ├── ylb-touch.css
│   │    └── ylb-app.css
│   └── demo/
└── test/
```

### 五、分享

- bower里边有的，统一用bower.json管理
- bower里没有的，上传到永利宝前端库（http://git.oschina.net/artcss/Sailfish）

### 六、编码规范

[详情](docs/coderules.md)

###七、工作方式
[详情](docs/workrules.md)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)