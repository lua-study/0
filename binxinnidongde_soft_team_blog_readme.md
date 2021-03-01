
**滴卡录**

------
**项目描述**

- “滴卡录”是一个打卡小程序，用户可以自己新建活动或加入他人活动，然后再进行打卡。


**功能特点介绍**

- 首页模块
显示所有用户已创建的活动，并可判断用户是否加入过此活动，若未加入，则可“立即加入”
在搜索栏中进行关键字检索可跳入搜索结果界面

- 新建活动模块
属性：活动名称（限12字以内）、活动内容、活动开始时间及结束时间（活动结束时间要大于开始时间），以上所有属性皆不能为空
组件："创建"按钮、输入框

- 打卡模块
 用户选择所要打卡的活动后，会先判断今天是否已打卡，若未打卡才可发表日记

 
- 我的模块
  - 我的活动：显示用户创建及加入的所有活动，点击相应活动，即进入相应的活动详情页面
  - 我的打卡记录：显示用户个人所发表的所有日记
  - 我的奖励（未实现）
  - 用户反馈：用户的个人建议及对我们小程序的看法均可反馈给管理员。
 

|页面目录|页面描述|页面链接|
|---|---|---|
|entrance|入口|[entrance](https://gitee.com/kezhiqing/soft_team_blog/tree/master/pages/index)|
|index|首页|[index](https://gitee.com/kezhiqing/soft_team_blog/tree/master/pages/index)|
|join|首页，搜索都指向的活动详情|[join](https://gitee.com/kezhiqing/soft_team_blog/commit/517732b66bfa641ccaf64f689e4274b896796435)|
|search|搜索结果|[search](https://gitee.com/kezhiqing/soft_team_blog/tree/master/pages/search)|
|newact|创建活动|[newact](https://gitee.com/kezhiqing/soft_team_blog/tree/master/pages/newact)|
|create|选择活动|[create](https://gitee.com/kezhiqing/soft_team_blog/tree/master/pages/newact)|
|release|发表日记|[release](https://gitee.com/kezhiqing/soft_team_blog/tree/master/pages/release)|
|mine|我的|[mine](https://gitee.com/kezhiqing/soft_team_blog/tree/master/pages/mine)|
|myActivity|我的活动|[myActivity](https://gitee.com/kezhiqing/soft_team_blog/tree/master/pages/myActivity)|
|record|我的打卡记录|[record](https://gitee.com/kezhiqing/soft_team_blog/tree/master/pages/record)|
|reward|我的奖励|[reward](https://gitee.com/kezhiqing/soft_team_blog/tree/master/pages/reward)|
|details|我的活动的活动详情|[details](https://gitee.com/kezhiqing/soft_team_blog/tree/master/pages/details)|
|fedback|用户反馈|[fedback](https://gitee.com/kezhiqing/soft_team_blog/tree/master/pages/fedback)|
|images|存放图片|[images](https://gitee.com/kezhiqing/soft_team_blog/tree/master/images)|
|utils|工具类|[utils](https://gitee.com/kezhiqing/soft_team_blog/tree/master/utils)|



**系统已知的问题和限制**

（1）用户创建活动时首页的图片显示是随机的，搜索结果的图片也是随机的，所以两个的显示可能不同。 
（2）用户创建活动时暂未实现上传图片的功能 
（3）我的奖励功能未实现 
（4）创建活动时对输入活动内容进行换行，显示出来的是空格 
（5）若用户更改微信用户昵称，我们的小程序无法获取新的昵称，显示出来的还是原来的昵称 
（6）活动结束未实现删除已结束的活动 
（7）无法退出自己加入的活动，无法删除自己创建的活动 
（8）无法删除及修改自己的打卡动态 

 
**开发环境搭建**

- 先下载微信开发者工具1.02版本，然后要申请微信小程序APPID
- 购买腾讯云服务器Windows server2012标准版
- 在服务器上安装wamp集成软件
- 开启域名解析
- 先申请CA证书，然后下载证书并放置服务器上，根据腾讯云的SSL证书配置指南进行相关配置后即可




-----


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)