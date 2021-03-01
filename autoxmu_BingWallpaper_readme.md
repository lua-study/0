# 必应每日壁纸
自动下载每日壁纸，并设置为你的桌面壁纸，让你保持桌面的壁纸每日清新不同。

同时，这个脚本还会下载当日壁纸中包含的视频，可以随时进行查看。

# Start
需要下载Python（兼容2、3）和pywin32, 然后对脚本中的下载目录进行简单设置即可:
```
pic_folder = "set-to-your-location"
video_folder = "set-to-your-location"
```

# Quick install
* 在windows中，以管理员身份运行cmd
* 安装 Chocolatey 这款 windows 软件包管理工具，当然，你也可以自行安装上面提到的软件 [check out Chocolatey.org](https://chocolatey.org)
```
@powershell -NoProfile -ExecutionPolicy Bypass -Command "iex ((new-object net.webclient).DownloadString('https://chocolatey.org/install.ps1'))" && SET PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin
```
* 这里以python3为例，安装python 3:
```
choco install python3
```
* 安装 pywin-32:
```
choco install pywin32
```
* 现在，你可以选择运行本脚本了, and there you go, with a little cute ballon tip, your wallpaper is already the latest Bing.com

# Extra
Add this script to your startup, keep your desktop up-to-date.

你可以尝试将本脚本放到启动项里面，那么，你每天开机时，壁纸都会自动更新啦。
脚本使用*.pyw的原因是，可以不弹出windows的cmd窗口。

Linux (如ubuntu) 下无法自动设置为桌面壁纸，但是可以正常下载。

# Screenshots

**一年多时间，无差错执行。**

![壁纸](https://git.oschina.net/NigelYao/BingWallpaper/raw/master/screenshot_1.png?dir=0&filepath=screenshot_1.png&oid=7ec43baf334d60c58ca5fd517d75a59850a103cf&sha=879fffd992e51349785005b047e657d9626d1b46 "必应壁纸预览效果")
![视频](https://git.oschina.net/NigelYao/BingWallpaper/raw/master/screenshot_2.png?dir=0&filepath=screenshot_2.png&oid=e8418ec1c90c5ccb0ad2ce8f04df73a51ce2579b&sha=73ec7b0bcaa9ec948b8669ad087d440b0b5296e0 "必应视频预览效果")

# 必应视频示例
必应视频很棒的一点是，可以无缝无限循环，所以，用来做背景是再适合不过了

[点击这里打开视频播放页面，右键选择循环](https://git.oschina.net/NigelYao/BingWallpaper/raw/master/CoalTit_GettyRR_133494783_1080_HD_ZH-CN.mp4)

# Notice
Follow bing.com's wallpaper usage, all wallpaper copyright belongs to bing.com

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)