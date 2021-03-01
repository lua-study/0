**Ver 0.1** 2019-2-28

 声明 

请在认真阅读本声明之后继续：

1. 项目中的二进制文件来源于公开的渠道，未进行任何修改，对文件或者项目中的其他版权内容我没有任何权益，如果侵权请联系 wsgalaxy@qq.com ，我将删除侵权内容；
2. 本项目**完全为服务我本人的需求**而生，在开源精神的影响下共享出来，我没期望也不阻止任何人使用本项目的资源，但使用者要为他的行为、行为产生的风险以及造成的任何后果（包括但不限于账号失窃、文件损坏、信息泄漏、财产损失等）负完全责任；
3. 我对使用该项目的人不具有任何形式的强制的义务和责任，包括但不限于维护项目、解决问题、承担后果等；
4. 如果你在使用过程中遇到了任何问题，可以加QQ群 319066257 交流学习，同样的，群里的任何人都没有必须解决问题的强制性义务；
5. 如果你依然无法理解上述声明，为了你的信息安全，请你立即终止进一步的操作。


 目录 

- [声明](#声明)
- [介绍](#介绍)
- [已打包的应用](#已打包的应用)
- [安装](#安装)
- [运行](#运行)
- [卸载](#卸载)
- [常见问题](#常见问题)

 介绍 

在linux下使用QQ等流行的windows软件一直是国内很多linux用户的需求，之前要实现这个需求用户往往需要对wine进行很多繁琐的配置，但即使这样最后跑出来的软件也是功能残缺的，只能满足最基本的使用需求。深度操作系统的开发人员在这方面做出了很多卓越的工作，在深度操作系统上提供了一批几乎完美的使用wine来执行的windows软件，包括QQ，TIM，迅雷，百度云等。将这些软件从深度移植到其他发行版是可行的，但是依据发行版的不同要做很多繁琐的操作，容易出错，并且不易于进行管理。  
Flatpak是一个发行版无关的下一代linux软件打包格式，只需打包一次就可以在不同的发行版上方便的安装和执行，当然完全的发行版无关是很难实现的，发行版的不同也会导致flatpak软件的行为有所不同，但终究要强于传统打包方式。  
本项目提供了一种使用flatpak打包深度基于wine的windows应用的方式，可以实现一次打包，到处运行，并且管理方便，兼容性好。


 已打包的应用 

### 已使用flatpak打包的deepinwine应用:

- com.deepin.wine - deepinwine的运行时 2.18
  - 构建仓库：  
  - 二进制文件仓库： 
  - 预构建文件：[com.deepin.wine.Platform.2.18.1.flatpak](https://www.jianguoyun.com/p/Dfh1P9oQ7vD3BhjR2aIB)

- com.tencent.tim - 腾讯TIM 2.0
  - 构建仓库： 
  - 二进制文件仓库： 
  - 预构建文件：[com.tencent.tim.2.0.1.flatpak](https://www.jianguoyun.com/p/DRMP0TUQ7vD3Bhju2aIB)
  - 扩展：
    - com.tencent.tim.ext.fcitx - fcitx输入法支持
      - 构建仓库： 
      - 预构建文件：[com.tencent.tim.ext.fcitx.2.0.1.flatpak](https://www.jianguoyun.com/p/DQpJ6msQ7vD3Bhj92aIB)
    - com.tencent.tim.ext.xsettingsd - KDE桌面支持
      - 构建仓库： 
      - 预构建文件：[com.tencent.tim.ext.xsettingsd.2.0.1.flatpak](https://www.jianguoyun.com/p/Dbk6kigQ7vD3Bhi7nqMB)

- com.tencent.qqlight - 腾讯QQ轻聊版 7.9
  - 构建仓库： 
  - 二进制文件仓库： 
  - 预构建文件：[com.tencent.qqlight.7.9.1.flatpak](https://www.jianguoyun.com/p/DWP-YlAQ7vD3BhiP2qIB)
  - 扩展：
    - com.tencent.qqlight.ext.fcitx - fcitx输入法支持
      - 构建仓库： 
      - 预构建文件：[com.tencent.qqlight.ext.fcitx.7.9.1.flatpak](https://www.jianguoyun.com/p/Dcg3Km8Q7vD3BhiV2qIB)
    - com.tencent.qqlight.ext.xsettingsd - KDE桌面支持
      - 构建仓库： 
      - 预构建文件：[com.tencent.qqlight.ext.xsettingsd.7.9.1.flatpak](https://www.jianguoyun.com/p/Dfq7ZaAQ7vD3Bhib2qIB)

- com.tencent.wechat - 腾讯微信PC版 2.6
  - 构建仓库： 
  - 二进制文件仓库： 
  - 预构建文件：[com.tencent.wechat.2.6.1.flatpak](https://www.jianguoyun.com/p/DV9o3dYQ7vD3Bhii2qIB)
  - 扩展：
    - com.tencent.wechat.ext.fcitx - fcitx输入法支持
      - 构建仓库： 
      - 预构建文件：[com.tencent.wechat.ext.fcitx.2.6.1.flatpak](https://www.jianguoyun.com/p/DWPhyusQ7vD3Bhis2qIB)
    - com.tencent.wechat.ext.xsettingsd - KDE桌面支持
      - 构建仓库： 
      - 预构建文件：[com.tencent.wechat.ext.xsettingsd.2.6.1.flatpak](https://www.jianguoyun.com/p/DXKJFKMQ7vD3Bhiu2qIB)

- com.xunlei.thunderspeed - 迅雷极速版 7.10
  - 构建仓库： 
  - 二进制文件仓库： 
  - 预构建文件：[com.xunlei.thunderspeed.7.10.1.flatpak](https://www.jianguoyun.com/p/DaWu9RMQ7vD3Bhix2qIB)
  - 扩展：
    - com.xunlei.thunderspeed.ext.xsettingsd - KDE桌面支持
      - 构建仓库： 
      - 预构建文件：[com.xunlei.thunderspeed.ext.xsettingsd.7.10.1.flatpak](https://www.jianguoyun.com/p/DRY9yqgQ7vD3Bhi42qIB)


- com.baidu.pan - 百度网盘 5.7
  - 构建仓库： 
  - 二进制文件仓库： 
  - 预构建文件：[com.baidu.pan.5.7.1.flatpak](https://www.jianguoyun.com/p/DTrq53sQ7vD3Bhi_2qIB)
  - 扩展：
    - com.baidu.pan.ext.xsettingsd - KDE桌面支持
      - 构建仓库： 
      - 预构建文件：[com.baidu.pan.ext.xsettingsd.5.7.1.flatpak](https://www.jianguoyun.com/p/DVzjlIYQ7vD3BhiO2qIB)

 




 安装 

### 检查文件来源

将深度的deepinwine应用打包成flatpak格式使用了从深度软件仓库提取的二进制文件，为了防止文件的原始链接随着应用仓库的更新失效，我把所使用的二进制文件存放到了我的gitee仓库（即[已打包的应用](#已打包的应用)中的二进制文件仓库）。为了保证你的数据安全，请你在安装前始终检查仓库中的这些二进制文件是否与原始来源的文件相同。除了二进制文件之外其余文件均是字体文件（font.tar.xz）或者简单的文本文件，也请检查这些文件的内容是否有异常。在仓库中的urls文件中提供了这些二进制文件的原始链接，你可以通过如下步骤进行检查，以com.deepin.wine的[二进制仓库](https://gitee.com/wsgalaxy/com.deepin.wine.git)为例：

1. 下载仓库
```
$ git clone --depth=1 https://gitee.com/wsgalaxy/com.deepin.wine.git
$ cd com.deepin.wine
```
2. 下载原始来源文件
```
$ mkdir dl
$ cd dl
$ wget `cat ../urls`
```
3. 计算二进制文件的sha256sum
```
$ sha256sum ./* > sha256sum.ori
$ sha256sum ../* > sha256sum.repo
```
4. 请比较sha256sum.ori和sha256sum.repo中各个二进制文件的hash值是否相同。
   如果不相同或者因为原始链接失效导致文件无法下载比较，则之后是否进行下一步安装请慎重考虑。
   如果你执意继续安装，你可以尝试通过原始链接下载更新的文件版本，或者使用仓库中的过时版本，但**无论你怎样安装，你都需要为所有可能后果（包括但不限于账号失窃、文件丢失等）负全部责任，详情请认真阅读[声明](#声明)**。

### 使用构建文件自行构建安装（推荐）

对于有linux使用经验，且对安全十分看重的人，推荐在检查二进制文件来源之后，使用构建文件自行构建安装。

1. 配置环境
   1. 为你的发行版[安装flatpak并添加flathub仓库](https://flatpak.org/setup/)，以同样的方法安装flatpak-builder
   2. 安装基础的Platform和Sdk
```
$ flatpak install flathub org.freedesktop.Platform/i386/18.08
$ flatpak install flathub org.freedesktop.Sdk/i386/18.08
```

2. 构建并安装deepinwine的运行时 com.deepin.wine.Platform

取决于你的电脑性能，这一步可能很耗时。

```
$ git clone https://gitee.com/wsgalaxy/com.deepin.wine.json.git
$ cd com.deepin.wine.json
$ mkdir .build
$ cd .build
$ flatpak-builder --repo=repo --arch=i386 build ../com.deepin.wine.json
$ flatpak remote-add --user --no-gpg-verify repodeepinwine ./repo
$ flatpak install --user repodeepinwine com.deepin.wine.Platform
```

3. 构建并安装应用

构建应用的流程大同小异，这里以com.tencent.tim为例。

- 构建应用本身

```
$ git clone https://gitee.com/wsgalaxy/com.tencent.tim.json.git
$ cd com.tencent.tim.json
$ mkdir .build
$ cd .build
$ flatpak-builder --repo=repo --arch=i386 build ../com.tencent.tim.json
$ flatpak remote-add --user --no-gpg-verify repotim ./repo
$ flatpak install --user repotim com.tencent.tim
```

- 要获得fcitx支持，需要构建应用对应的fcitx扩展
   
与tim对应的fcitx扩展是 com.tencent.tim.ext.fcitx。

```
$ git clone https://gitee.com/wsgalaxy/com.tencent.tim.ext.fcitx.json.git
$ cd com.tencent.tim.ext.fcitx.json
$ mkdir .build
$ cd .build
$ flatpak-builder --repo=repo --arch=i386 build ../com.tencent.tim.ext.fcitx.json
$ flatpak remote-add --user --no-gpg-verify repotimextfcitx ./repo
$ flatpak install --user repotimextfcitx com.tencent.tim.ext.fcitx
```

- 要获得KDE支持，需要构建应用对应的xsettingsd扩展
   
与tim对应的KDE支持扩展是 com.tencent.tim.ext.xsettingsd。

```
$ git clone https://gitee.com/wsgalaxy/com.tencent.tim.ext.xsettingsd.json.git
$ cd com.tencent.tim.ext.xsettingsd.json
$ mkdir .build
$ cd .build
$ flatpak-builder --repo=repo --arch=i386 build ../com.tencent.tim.ext.xsettingsd.json
$ flatpak remote-add --user --no-gpg-verify repotimextxsettingsd ./repo
$ flatpak install --user repotimextxsettingsd com.tencent.tim.ext.xsettingsd
```

### 使用预构建文件安装

我为[已打包的应用](#已打包的应用)提供了已经构建好的安装包，如果你不想自己通过构建文件自行构建，可以使用已经构建好的安装包直接安装。你首先需要下载对应的安装包，以com.deepin.wine.Platform.2.18.1.flatpak为例：
```
在安装包的同一目录中打开终端
$ flatpak install --user ./com.deepin.wine.Platform.2.18.1.flatpak
```

### 安装顺序及注意事项

无论你已哪种方式安装，都要遵循一定的安装顺序：运行时 com.deepin.wine.Platform 必须第一个安装，之后安装对应的应用，如安装TIM的话就安装 com.tencent.tim，然后再根据需要安装应用对应的扩展，如TIM对应的 fcitx 支持扩展是 com.tencent.tim.ext.fcitx、对应的KDE支持扩展是 com.tencent.tim.ext.xsettingsd。  
只在你使用的是fcitx而无法输入中文的情况下安装fcitx扩展，如果你使用的是ibus输入法请不要安装该扩展；  
只在你使用的是KDE桌面而无法启动应用的情况下安装xsettingsd扩展，切记**不要在gnome环境下安装xsettingsd扩展**，否则可能导致桌面异常。


 运行 

应用可以使用应用菜单的图标直接启动，或者使用命令行 `flatpak run APPID` 运行，如运行 com.tencent.tim：
```
$ flatpak run com.tencent.tim
```

安装完之后的第一次执行建议使用命令行，**迅雷 com.xunlei.thunderspeed 和百度云 com.baidu.pan 第一次执行必须使用命令行**，并在命令的提示中输入 y 回车，之后才能通过应用菜单启动。

 卸载 

使用 `flatpak run APPID -h`可以查看帮助。  
卸载时，需要先删除wine容器，再卸载应用和扩展，当所有的deepinwine应用卸载完后，才可以卸载运行时：
```
卸载 com.tencent.tim 以及对应的fcitx和xsettingsd扩展
$ flatpak run com.tencent.tim -e
$ flatpak remove com.tencent.tim
$ flatpak remove com.tencent.tim.ext.fcitx
$ flatpak remove com.tencent.tim.ext.xsettingsd
```
所有deepinwine应用都卸载后，卸载运行时：
```
$ flatpak remove com.deepin.wine.Platform
```


 常见问题 

- 应用无法启动

尝试使用`flatpak run APPID -r`来重新解压运行时，当询问时回答y。

- fcitx安装扩展之后仍无法启用

安装扩展后使用 `flatpak kill APPID` 终结应用后重新启动，在输入前注意确保fcitx已是中文输入模式（通过点击fcitx图标切换）

- 即使没有安装fcitx扩展但无法使用ibus

如果你同时安装了fcitx和ibus，请卸载fcitx然后重新启动。

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)