# create-react-app
这是个 React-Babel-Webpack 项目的脚手架。您可以将其用作构建自己的Web应用程序的基础。

# 特征
- 使用`Webpack 4`构建
- 配备了`React`，`ES6`和`Babel 7`
- 配置了`ESLint`，根据自己代码风格个性化配置
- 配置了`Service Worker`，生产环境直接生成PWA离线网页应用
- 打包配置好了图片压缩，字体打包，js,css代码目录分离
- 结合了`koa`生成mock假数据模拟
- 结合了`react-redux`，`react-router`一些使用代码
- 开发环境自动在`Webpack`加载时打开一个新的浏览器选项卡，并修改项目代码时不刷新页面更新
- `public`文件夹存放静态文件，不经过`Webpack`打包处理，一些特殊的代码文件可以存在在这里
- 可以在`Webpack`配置文件找到`APP_URL`，方便在「生产/开发」构建中使用不同的服务URL(Service URLs)
- 直接修改`src`目录下文件，编写自己的项目代码

# 如何使用

首先，克隆下载。
```
$ git clone https://gitee.com/xuhongling/create-react-app  
$ cd   
```
接着，安装依赖关系。（建议使用阿里源或者cnpm）
```
$ npm install
```
然后，启动假数据模拟接口。
```
$ npm run mock
```
最后，启动应用程序。
```
$ npm start
```
现在你应该在http://127.0.0.1:8088中看到一个新的浏览器窗口/标签打开的react项目样板了

# 如何打包
你开始在src目录中开发自己的代码。编码完成后，使用npm run buil构建静态文件，在新生成的build目录中可以看到打包好的项目。
```
$ npm run buil
```
可以启动本地服务。
```
$ npm run server
```
现在你应该在http://127.0.0.1:8081中看到一个新的浏览器窗口/标签打开的react项目打包好的项目了

# 执照
MIT


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)