# 百灵快传（B0Pass）

LAN large file transfer tool。

基于Go语言的高性能 “手机电脑超大文件传输神器”、“局域网共享文件服务器”。

只需一个文件（exe）双击开启。

## 1. 主要功能

### 1.1 功能描述

- [x] 文件共享服务器
- [x] 简单的单个可执行文件
- [x] 共享文件界面（只要在同一局域网或WIFI下，可以传输超大文件）
- [x] 上传文件界面（支持点选和拖拽）
- [x] 二维码扫码界面（支持手机传输，支持其它电脑输入网址）
- [x] 共享文件在线管理界面（可删除）
- [x] 开发linux可部署版本
- [ ] 端口如果被使用，可以自行开启其它端口 
- [ ] 使用WebSocket实时通知文件变更
- [ ] 更简洁高效的操作界面
- [ ] 自动检查更新版本

### 1.2 功能截图

 
 
 
     
     主页（文件共享页） 
 
 
     
     手机扫码，或获取链接地址 
 
 
     
     上传（上传页面） 
 
 
 
 
     
     上传（上传过程页面） 
 
 
     
     可点击在线浏览或下载 
 
 
     
     主页（管理文件）可点击删除 
 
 
 

 
     上传超大文件 
    
![linux/amd64版本发行版](https://images.gitee.com/uploads/images/2019/1029/165512_c182287e_77462.png "b0pass_linux_cli.png")

linux/amd64版本发行版


## 2. 下载使用

-  为了流畅使用UI界面， 最好先安装了谷歌浏览器 
-  已编译版本支持Mac OS、Windows、Linux/amd64等平台

### 2.1 Mac OS
- [b0pass_mac.dmg v0.1.4 @ github](https://github.com/bitepeng/b0pass/releases/download/v0.1.4/b0pass_OSX.dmg)
- [b0pass_mac.dmg v0.1.4 @ gitee 国内链接](https://gitee.com/b0cloud/b0pass/releases)

### 2.2 Windows
- [b0pass_win.exe v0.1.4 @ github](https://github.com/bitepeng/b0pass/releases/download/v0.1.4/b0pass_win32.exe)
- [b0pass_win.exe v0.1.4 @ gitee 国内链接](https://gitee.com/b0cloud/b0pass/releases)

### 2.3 Linux Amd64
- [b0pass_linux_cli v0.1.4 @ github](https://github.com/bitepeng/b0pass/releases/download/v0.1.4/b0pass_linux_cli)
- [b0pass_linux_cli v0.1.4 @ gitee 国内链接](https://gitee.com/b0cloud/b0pass/releases)

### 更多版本下载地址

- https://gitee.com/b0cloud/b0pass/releases （国内用户建议访问）
- https://github.com/bitepeng/b0pass/releases


## 3. 代码库

- https://github.com/bitepeng/b0pass   欢迎到github star
- https://gitee.com/b0cloud/b0pass     欢迎到gitee  star


## 4. 使用场景
- ***手机电脑共享文件***

    电脑上双击执行 --> 手机扫码 --> 手机上的大文件传到电脑、或者电脑传文件到手机。

- ***电脑之间共享文件***

    电脑A上双击执行 --> 电脑B上浏览器输入A的地址 --> 电脑A上的大文件传到电脑B、或者电脑B传文件到电脑A。

- ***虚拟机和电脑之间共享文件***

    电脑上双击执行 --> 虚拟机上浏览器输入电脑的地址 --> 虚拟机上的大文件传到电脑、或者电脑传文件到虚拟机。

- ***更多使用场景***

    也可以用作“家庭影音中心”、“办公室文件共享”、“产品原型服务器”等。总之走局域网的HTTP协议，和是不是iPhone、iOS、安卓、虚拟机等都没有关系，跨平台共享文件。

## 5. 源码编译
```
# 下载代码，推荐使用go mod模式管理依赖
git clone https://github.com/bitepeng/b0pass.git

# 配置Goland支持go mod，更新依赖
cd docs/script && chomd +x ./do-vendor && ./do-vendor

# 编译运行开发版本
cd docs/script && chomd +x build-develop.sh && build-develop.sh
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)