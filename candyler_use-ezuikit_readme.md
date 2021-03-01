# use-ezuikit
在vuejs中使用萤石的ezuikit的监控模式播放视频


### 几个关键步骤
- 使用vuecli创建vue项目
- 下载[萤石监控模式的api](https://open.ys7.com/doc/zh/uikit/uikit_javascript.html)，比如当前版本为： EZUIKit_js_v2.6.1build20191105.zip
- 将文件解压到index.html文件所在的public目录的static目录下
- 修改index.html文件，在其中引入 `ezuikit.js` 文件
- 参考萤石的直播示例文件 EZUIKit-JavaScript/demo/demo-monitor.html，开发自己的播放组件，具体代码见 Helloworld.vue文件，其中只有一点要注意，在官方示例文件中没有指定 decoderPath，Helloworld.vue中，我们把它指定为 `/static/ezui`，就是`ezuikit.js`相对于`index.html`的相对路径

### 使用方法
- git clone
- npm install
- npm run serve
- 然后填写自己的直播路径以及token就可以播放了。

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)