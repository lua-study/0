## 最近打算写一些前端网页，为了方便查阅，突发奇想，将前端网页嵌套在APP内部，而APP可以安装在手机，岂不是可以随时查阅了么，比如自己写的博客，让它成为一个独立的APP安装在手机上，岂不是锦上添花？

### 1.[仓库地址](https://gitee.com/Chaoc/PeakWebApp.git)

### 2.克隆代码(建议直接从仓库fork)：

```
git clone https://gitee.com/Chaoc/PeakWebApp.git
```

### 3.修改个人配置：

```
#打开项目根目录下config.gradle文件
ext {
    //App安装到手机上的名字
    app_name = "淘宝"
    //是否从本地加载网页
    isLocal = "false"
    //应用包名
    application_id = "com.peakchao.webapp"
    //isLocal = "true"：说明从本地加载网页，你只需将你的网页源码放到项目app/src/main/assets目录下即可
    //isLocal = "false"：说明不从本地加载网页，而是从加载下面web_url
    web_url = "http://demo.wex5.com/taobao/index.html?device=m"
}
#App桌面图标替换路径：app/src/main/res/drawable-xxhdpi/ic_launcher.jpg

```

### 4.打包(打包前先push你的代码到仓库)：

![下载APK](https://upload-images.jianshu.io/upload_images/5174117-1e5d8a524cbd19fb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![新建构建](https://images.gitee.com/uploads/images/2019/0129/161711_14f35654_595073.png)

![构建信息](https://images.gitee.com/uploads/images/2019/0129/161711_0609a0ac_595073.png)

![apk下载](https://images.gitee.com/uploads/images/2019/0129/161711_59da405a_595073.png)

### 5.运行：

![应用](https://images.gitee.com/uploads/images/2019/0129/161710_111fab3c_595073.png)

![运行](https://images.gitee.com/uploads/images/2019/0129/161711_6ee171ce_595073.png)




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)