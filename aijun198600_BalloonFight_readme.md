# BalloonFight

### 特别声明

本项目自起始至结束所有源码全部开放，但必须保留署名权，所有素材资源一律网上收集，如果版权纠纷请您联系我，我会将项目中对应资源移除。

邮箱: Keyle_xiao@hotmail.com  QQ:351372404

StrangeIOC交流群: 137728654

开源项目地址: https://git.oschina.net/keyle/BalloonFight

OSChina Git手机端下载随时跟进项目状态 https://git.oschina.net/appclient 

很高兴与诸位StrangeIOC的学习者们分享此Demo的源码，如果你有什么不懂的可以加到群里聊聊或者邮件联系我。游戏的核心是仿照fc上的的气球大战来的，前面是关卡跑酷，关底是Boss战。数据层使用json作为关卡配置，战斗部分使用native sprite实现，ui部分使用ugui，此demo代码略粗糙没有细致整理，但对于想要学习strangeioc框架的同学来说是足够入门了。
 
 

# 开发流程

1.加入QQ群，注册OSChina账号

2.如果想成为master开发者请告知我注册邮箱，方便发放开发者权限

3.成为开发者后在team中确认模块分工 https://team.oschina.net/ 

4.所有人均有权重构重写它人代码，但请留下中文注释

5.所有测试代码请存于test分支中，请勿在master中上传

6.为了有一个自由的协作开发模式，管理员不审核代码提交，Push代码之后请在team中告知

7.请勿轻易删除非本人创建代码片段，有有必要 可全文注释


### 开发规范细则
命名规则：[Camel-Case(骆驼命名法)](http://baike.baidu.com/link?url=y3Syq4B7nXdn5QTN3sanj19fhC9JuQ5RhGSOmE8K_Kn25tHrXvuNotLr_9atUmRuVpfHVsPFOv41CzV1Dp8jga) 

枚举规范：使用StrangeIOC非全局事件枚举请尽量使用类内部枚举，即 在类内部定义枚举类

目录结构：如 

```
Main上下文为例
		   ------------common
		   --
           ------------controller	 
		   --
		   ------------model
		   --
		   ------------util
		   --
		   ------------view
```


# 非盈利声明

1.本项目内除代码外任何资源禁止商用

2.代码片段作者本人对该代码有最终解释权

3.禁止任何盈利性传播，如收费倒卖源码

 

# 最终语

由于现在国内使用此框架的开源项目几乎为零，主要是因为学习曲线陡难度大，所以导致团队协作起来不是那么容易，在您的团队的不可能每个人都具有十分的框架概念。希望通过此demo能带你入坑 ~ 

Demo已完成。完整项目开发周期不定，有空便可以上去倒腾两下，欢迎过来Fork代码。


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)