[Share.js](http://overtrue.me/share.js/)
===

一键分享到微博、QQ空间、QQ好友、微信、腾讯微博、豆瓣、Facebook、Twitter、Linkedin、Google+、点点等社交网站。

![qq20151127-1 2x](https://cloud.githubusercontent.com/assets/1472352/11433126/05f8b0e0-94f4-11e5-9fca-74dc9d1b633f.png)


[DEMO](http://overtrue.me/share.js/)

或者直接浏览我的博客 http://overtrue.me 或者 http://laravel.so 内容页查看效果。

# 安装

有3种安装方式：

1. 使用 [npm](https://npmjs.com)

    ```shell
    npm install social-share.js
    ```
2. 使用 [cdnjs](https://cdnjs.com/libraries/social-share.js)，引入 `share.min.css` 与 `share.min.js` 两个链接就好。 (感谢 [@mdluo](https://github.com/mdluo))

3. 手动下载或者 git clone 本项目。

# 使用


HTML:

```html
  

 
 
  

// 当你使用类名为 `social-share` 时不需要手动初始化
```

## 自定义配置

所有配置**可选**， 通常默认就满足需求：

可用的配置有：

```js

url                 : '', // 网址，默认使用 window.location.href
source              : '', // 来源（QQ空间会用到）, 默认读取head标签： 
title               : '', // 标题，默认读取 document.title 或者  
description         : '', // 描述, 默认读取head标签： 
image               : '', // 图片, 默认取网页中第一个img标签
sites               : ['qzone', 'qq', 'weibo','wechat', 'douban'], // 启用的站点
disabled            : ['google', 'facebook', 'twitter'], // 禁用的站点
wechatQrcodeTitle   : '微信扫一扫：分享', // 微信二维码提示文字
wechatQrcodeHelper  : ' 微信里点“发现”，扫一下  二维码便可将本文分享至朋友圈。 '
```

以上选项均可通过标签 `data-xxx` 来设置：

> 驼峰转为中横线，如`wechatQrcodeHelper` 的data标签为`data-wechat-qrcode-helper`

##### 禁用 google、twitter、facebook 并设置分享的描述

```html
  
```

##### 设置微信二维码标题

```html
  
```

##### 针对特定站点使用不同的属性（title, url, description,image...）

```html
  
```

### 你也可以自定义图标

使用: `data-initialized="true"` 标签或者 `initialized` 配置项来禁用自动生成icon功能。

```html
 
      
      
      
 
```
以上a标题会自动加上分享链接（`a` 标签必须带 `icon-NAME` 属性，不然分享链接不会自动加上）。

### 如果你想在分享icon列表中内置一些元素，比如放一个收藏按钮在分享按钮的后面：

```html
 
      
 
```
这样并没有实现，因为结果是所有的分享按钮都创建在了收藏按钮的后面了，这时候你就可以用 `data-mode="prepend"` 来确定分享按钮创建的方式。

```html
 
      
 
```

这样，所有的分享图标就会创建在容器的内容前面，反之可以用 `append` 创建在容器内容后面，当然这是默认的，也不需要这么做。

### 指定移动设备上显示的图标

```html
  
```
当在手机上打开该页面的时候就只会显示这4个图标了。

欢迎贡献代码及提建议！

# 引用

本项目中二维码生成部分用到了开源组件：[lrsjng/jquery-qrcode](https://github.com/lrsjng/jquery-qrcode) (MIT License)

# License

 MIT




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)