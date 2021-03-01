
=======
# RTX2010 for Mac
***
## Delphi开发RTX2010 Mac OS x客户端
***
#### **这个东西就是我随便玩玩的！**
#### **暂时还在继续开发中，还有很多没有弄，反正有空就整下吧**
#### **[我的博客](http://blog.csdn.net/zyjying520)**
***
***
##### 原协议参考[solosky](http://git.oschina.net/solosky/rtx)分析的协议，不过他的不全完，而且跟rtx2010的有些协议有点不一样，于是自己着手写了工具分析
***
### 目录结构及祥细情况
1. RTX2010Mac  ***-----------客户端主工程 DelphiXE8***
2. RTXPacketHook  ***-----------RTX Hook库 DelphiXE6***
3. X ***-----------分析工具  DelphiXE6***

*** 

### 第三方库使用情况：
1. RTX2010中使用了RYYD编写的QQTEA.pas单元，由我增加支持Mac平台
2. RTXPacketHook 中使用了[wr960204武稀松](http://www.raysoftware.cn)的HookUtils.pas，用习惯这个了自己都忘了怎么做hook了，只能怪这个好用，嘿嘿
3. X中使用了来自[CnPack团队](http://www.cnpack.org)的Cnvcl控件CnHexEditor.pas及CnMD5.pas单元 


![登录窗口](http://git.oschina.net/ying32/RTX2010Mac/raw/master/%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A71.png?dir=0&filepath=%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A71.png&oid=2d77846082796e9cff9ff7819ce44e95ebbb81e7&sha=40876ae2b2a50dbf4803caf8a9adbc0d893b9fab)

![主窗口](http://git.oschina.net/ying32/RTX2010Mac/raw/master/%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A72.png?dir=0&filepath=%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A72.png&oid=aac47668e36ae1b7ee7cb67cfb68a4acac7f550e&sha=40876ae2b2a50dbf4803caf8a9adbc0d893b9fab)

![数据包分析工具](http://git.oschina.net/ying32/RTX2010Mac/raw/master/xxx.png?dir=0&filepath=xxx.png&oid=242e34eb105ca618696e83c1375f92168241ac9a&sha=40876ae2b2a50dbf4803caf8a9adbc0d893b9fab)
***
## 作者信息
***
ying32

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)