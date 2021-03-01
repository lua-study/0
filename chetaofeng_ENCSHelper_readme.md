[toc]
---

# 简介
本软件为甘肃紫光联网收费维护辅助移动端。

# 项目搭建
## 安装依赖环境
* sudo cnpm install cordova -g
* sudo cnpm install ionic -g

## 命令行创建项目
> 这里记录的是创建项目的相关命令，如果是远程下载项目，则跳过

* ionic start eHelper
* ionic login  //输入用户名、密码，非必须,https://apps.ionic.io/apps
* ionic link   //非必需

## 远程下载目录
* 通过webstorm图形界面下载项目
* sudo cnpm install

## 添加脚本执行权限
* sudo chmod -R 777 node_modules/

## 调试项目
* ionic serve //启动网页调试
* ionic cordova run ios/android //运行项目，第一次会自动安装平台依赖
* ionic cordova platform add ios --save //添加ios平台支持
* ionic cordova platform add android --save
~~~
// If you get the below error, just ignore. And try again.
Error: Failed to fetch platform cordova-ios@~4.4.0
Probably this is either a connection problem, or platform spec is incorrect.
Check your connection and platform name/version/URL.
Failed to get absolute path to installed module

 rm -rf ~/.cordova
~~~
* ionic cordova run ios --emulator --target="iPhone-6s"
 
## 平台无法添加的处理
* 原因分析：个人觉得应该是权限问题
* 处理方案：
~~~
1. 在本地重新创建一个本地项目，添加平台
2. 在下载项目中执行添加平台方法（为了通过命令添加记录到config文件中）
3. 拷贝platforms、plugins文件夹到下载目录
4. 拷贝1中添加平台是添加的package.json的内容到下载项目中
5. sudo cnpm install
6. 测试项目
~~~

# 联系我
QQ：183822908 天行贱


```bash
$ sudo npm install -g ionic cordova
$ ionic start myBlank blank 

$ ionic cordova platform add ios
$ ionic cordova run ios
```



sudo chown -R $(whoami) ~/.npm


https://my.oschina.net/u/1440971/blog/824435


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)