   

electron 开发的一个可以播放,下载国内主流视频的播放器。A player developed by electron that can play and download domestic mainstream video.

> 项目想法来源于[ivideo](https://github.com/phobal/ivideo)，另外增加了视频下载功能。

## 下载

- [mac 下载体验](https://gitee.com/meetqy/hapv/releases)

> windows 可拉取代码自行打包.

## 界面

|              -               |              -               |
| :--------------------------: | :--------------------------: |
|   |   |
|   |   |

## 技术栈&插件

- Electron
- Vue
- Vuex
- vue-cli-plugin-electron-builder
- Element

下载功能需安装 [annie](https://github.com/iawia002/annie)

## 如何运行

```
git clone git@github.com:meetqy/hapv.git
```

```
cd hapv
```

```
npm install
```

> 如果安装失败或者慢，建议使用 `cnpm install`.

```
npm start
```

## 项目结构

```tree
src
├─App.vue
├─background.js // electron后台文件
├─element-variables.scss
├─main.js
├─views
├─store
├─router
├─plugins
├─config
|   ├─analysis.js // 解释视频的配置文件
|   ├─index.js
|   └platform.js  // 各大视频平台url，视频解析规则的配置文件
├─components
├─assets
```

## 播放视频原理

1. 利用`electron`框架，返回 web 页面
2. 页面中嵌入 webview，url 为各平台官网
3. 利用`electron`提供的 api，监听页面跳转，劫持链接，返回解析之后的视频链接。

## 快捷小技巧

-  ESC 取消全屏

## 开发规范

- [开发规范](./开发规范.md)

## 版本记录

最近更新：

- 0.4.1-alpha

- [x] 取消双击导航栏全屏功能
- [x] mac 系统自带全屏功能，header 显示隐藏功能失效

* [版本记录](./版本记录.md)

## 参与贡献

   


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)