# 【天天派奖】 微信小程序开发文档

## 目录结构
```
.
├── README.md
├── build
│   ├── build.js
│   ├── check-versions.js
│   ├── dev-client.js
│   ├── dev-server.js
│   ├── utils.js
│   ├── vue-loader.conf.js
│   ├── webpack.base.conf.js
│   ├── webpack.dev.conf.js
│   └── webpack.prod.conf.js
├── config
│   ├── dev.env.js
│   ├── index.js
│   └── prod.env.js
├── index.html
├── package.json
├── src
│   ├── App.vue                 # 入口根组件（APP组件）
│   ├── components              # 普通组件目录
│   ├── main.js                 # 入口js
│   ├── pages                   # 页面组件目录（Page组件）
│   └── store.js                # 全局store
└── static
    ├── images
    └── less
```

## 开发模式
运行下列指令：
```
npm start -- -m=st
```
即可指定`st`环境，此时在根目录下会生成`/dist`目录，在`微信开发者工具`里面选择该目录，填写位于`/config/index.js`里面的`appid`即可进行开发。

开发模式下自动支持热更新功能，每修改代码都会触发开发者工具的刷新，实时预览效果。

注意，此模式不可进行体验版代码上传，因为代码还未被优化处理，存在反编译为明文的风险。

## 预发布/生产模式
运行下列指令：
```
npm run build -- -m=st
```
指定`st`环境的**预发布模式**，该模式会重新生成一个`/dist`目录，这个目录可以用于体验版代码上传。

## 支持的环境
- st (默认)
- prod


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)