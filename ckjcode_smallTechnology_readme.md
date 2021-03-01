# 小技术君-小程序

[![Fork me on Gitee](https://gitee.com/ckjcode/smallTechnology/widgets/widget_6.svg?color=c71d23)](https://gitee.com/ckjcode/smallTechnology)

#### Description
技术社区类小程序，采用云开发 ，不需要单独开发后端接口
小技术君是一款基于云开发的技术社区类小程序，该小程序完全不依赖任何后端服务，无需自己的网站、服务器、域名等资源，只需要自行注册小程序账号即可。

Technology community applet, using cloud development, does not require separate development of backend interfaces
small Technology Jun is a technology community-based applet based on cloud development. The applet does not depend on any back-end services at all. It does not need its own website, server, domain name and other resources. You only need to register your own small program account.
#### Software Architecture
Software architecture description

#### Installation

1.准备安装最新版本的微信开发者工具“下载至微信小程序官方网站”nodejs环境“云开发和调试需要使用nodejs环境”，如果是首次安装，则可以自己安装教程。下载源代码：https://gitee.com/ckjcode/smallTechnology.git

2.项目初始化首先打开WeChat Developer工具，导入小型技术项目，名称可以自定义，然后AppID填写个人小程序帐户。如果是新注册的小程序帐户，则需要手动打开云开发功能，单击左上角的云开发按钮，然后根据提示打开云开发功能。完成后，您将跳至相应的云开发控制台。

3.云数据库配置small-Technology的数据源全部来自云数据库，因此您需要在运行之前初始化云数据库，并将以下集合添加到云数据库：

smallTechnology_comments 

smallTechnology_posts 

smallTechnology_logs

smallTechnology_posts_related

smallTechnology_formids

smallTechnology_config

access_token

4.云功能部署首先，您需要上传您的云功能，右键单击相应的云功能名称-上传并部署。有两个上载和部署，并且有相关的说明。如果已经下载并调试了相应的node_modules，则建议上传所有文件。同时，我们需要注意云开发的环境。微信小程序允许用户创建两个环境（通常是测试环境的正式环境），以及云功能需要上传到哪个环境才能切换到哪个环境。此时，它应该能够在WeChat Developer工具中正常运行。“但是没有与文章相关的数据。”####项目截图



 
 


 
&nbsp;
 
&nbsp;
 
&nbsp;
 
&nbsp;
 
&nbsp;
 

#### Instructions

1.  xxxx
2.  xxxx
3.  xxxx

#### Contribution

1.  Fork the repository
2.  Create Feat_xxx branch
3.  Commit your code
4.  Create Pull Request

#### 更新日志:
1. 新增blog-hunter 用来收集第三方平台的优秀文章 丰富小技术君
2. 初始化 blog-hunter-front Vue用户移动端
3. 初始化 blog-hunter-front-admin Vue管理员前端

#### Gitee Feature

1.  You can use Readme_XXX.md to support different languages, such as Readme\_en.md, Readme\_zh.md
2.  Gitee blog [blog.gitee.com](https://blog.gitee.com)
3.  Explore open source project [https://gitee.com/explore](https://gitee.com/explore)
4.  The most valuable open source project [GVP](https://gitee.com/gvp)
5.  The manual of Gitee [https://gitee.com/help](https://gitee.com/help)
6.  The most popular members  [https://gitee.com/gitee-stars/](https://gitee.com/gitee-stars/)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)