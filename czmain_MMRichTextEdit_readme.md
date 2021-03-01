### MMRichTextEdit
实现的功能包含了：
- 编辑器文字编辑
- 编辑器图片编辑
- 编辑器图文混排编辑
- 编辑器图片上传，带有进度和失败提示，可以重新上传操作
- 编辑器模型转换为HTML格式内容
- 简单的本地数据存储和恢复编辑实现（草稿箱功能）
- 配套的Java实现的服务器

对应的java实现的文件服务器代码开源托管地址：[javawebserverdemo](http://git.oschina.net/dhar/javawebdemo)  

具体的实现过程以及详细解析可以看我的这篇博客：[iOS使用UITableView实现的富文本编辑器](https://my.oschina.net/u/1242477/blog/1486577)  
关于编辑器的性能优化可以看我的这篇博客：[iOS使用Instrument-Time Profiler工具分析和优化性能问题](https://my.oschina.net/u/1242477/blog/1506747)  


下面是实现的效果图  
![Demo1](https://static.oschina.net/uploads/img/201707/24205815_bVa4.png "Demo1")
![Demo4](https://static.oschina.net/uploads/img/201707/27230228_sDyH.png "Demo4")
![Demo3](https://static.oschina.net/uploads/img/201707/24205938_syUr.png "Demo3")

#### 使用方法
项目使用 cocoapods 管理依赖库，如果没有安装cocoapods，可以参考 [Cocoapods安装和升级备忘录](https://my.oschina.net/u/1242477/blog/1480211) 这篇文章。  
已经安装好cocoapods，进入到 `RichTextEditDemo` 目录（Podfile文件所在的目录），执行命令 `pod update --no-repo-update` 下载依赖库，打开 `RichTextEditDemo.xcworkspace` 即可。

#### 已知问题
- 单段文字输入的内容很长，大于10000个英文字符会出现卡顿的情况，目前没有完美的解决方法，项目是使用简单的限制单段文字的长度为5000

因为时间原因，有很多地方优化的不到位，如果看官有建议意见希望给我留言，我会继续完善，或者你有时间欢迎加入这个项目，可以一起做得更好。

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)