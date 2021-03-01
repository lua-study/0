Musical
==========


程序介绍
---------
  Musical是一套通用的音乐分享软件系统，用户可以在不需要任何编程的基础上，通过简单的设置和安装，在互联网上搭建起具备完善功能可高度定制的音乐分享服务。Musical 的基础架构采用世界上最流行的web编程组合PHP+MySQL实现，是一个经过完善设计，适用于各种服务器环境的高效音乐分享系统解决方案。


如何下载
---------
  Musical的源代码现在托管在git@OSC，如果你没有PHP开发经验，最好不要自行clone最新的源代码，因为可能只是我临时备份代码，还不完整，请直接进入官方网站(www.imusical.tk)下载已经发布的正式版。


上传系统工作流程[Doris版开始]
---------
```
  1.用户上传歌曲，服务器自动分析歌曲信息(存在失败的可能性)
  2.用户核对歌曲信息，提交审核
  3.审核员在后台找到待审歌曲，下载到本机
  4.审核员试听歌曲，决定通过还是驳回
  5.通过的歌曲审核员将其转换为192k的MP3文件(320k高峰期有点卡)，便于在线试听
  6.审核员将转码前后的音乐文件上传到百度网盘(暂时)
  7.审核员继续完善歌曲信息，并通过歌曲
```


环境要求
---------
```
  Apache 服务器[其他服务器请自行重写伪静态规则]
  PHP >= 5.2.10
  空间大小 >= 100MB[分析歌曲信息需要临时占用空间]
  空间流量尽量大
```


推荐配置
---------
```
  Apache 服务器
  PHP >= 5.4
  空间大小 >= 1GB
  空间流量 >= 20GB
```


安装教程
---------
```
  1.解压安装包
  2.修改配置文件(system/config.cfg.php)中的基本配置信息
  3.上传到空间
  4.打开网站，系统会自动进行安装
```


注意事项
---------
  1.安装好的系统中默认没有用户，请自行注册，默认第一个用户为管理员[配置文件中可以更改]。


升级教程
---------
```
  All:
    1.解压安装包
    2.修改配置文件(system/config.cfg.php)中的基本配置信息
    3.删除空间上原有的所有文件
    4.上传新代码
    5.打开网站，系统会自动进行数据库更新
```


更新记录(所有跟新纪录均基于上一版本)
---------
```
  Doris[Developing]:
    1.[ADD][功能]增加Clicki使用统计(方便程序开发者了解情况)
    2.[ADD][系统]全新的内核(Developing-需要较长开发时间)
  Chihiro[20130918]:
    1.[FIX][程序]修复PHP5.4兼容性
    2.[FIX][程序]规范DB和DEBUG类库
    3.[ADD][功能]增加系统公告
    4.[FIX][功能]修复邀请码机制无效的问题
    5.[ADD][功能]增加自主填写歌曲信息功能
    6.[FIX][功能]修复云存储服务商临时限流导致获取文件信息失败无法添加歌曲
    7.[DEL][功能]删除七牛接口入口(接口不合适)
    8.[ADD][功能]全新的HTML5播放器
    9.[FIX][界面]搜索结果页简化
  Blois[20130828]:
    1.[ADD][界面]搜索结果页手机版增加UP主显示
    2.[ADD][后台]增加系统设置页
    3.[ADD][功能]增加邀请码机制
    4.[ADD][功能]增加用户注册开关
    5.[ADD][功能]增加音质显示文字自定义功能
    6.[ADD][功能]增加歌曲上传下载开关
    7.[ADD][功能]增加上传接口开关
  Aria[20130827]:初始版本
```


还有一件事
---------
```
前台UI采用BootStrap构建。
分析歌曲信息使用getID3类库，分页类修改自ThinkPHP的分页类。
vDisk接口，BaiduPCS接口均为原创。
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)