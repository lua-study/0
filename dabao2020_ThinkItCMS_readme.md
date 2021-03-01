# ThinkItCMS

#### 介绍
又一个 JEE CMS,ThinkItCMS 是一款面向模板开发，支持静态生成的CMS 系统,其支持前后端分离部署,是一款好用的 cms 系统

#### 软件架构
ThinkItCMS 架构介绍：
ThinkItCMS 采用 SpringBoot + Mybatis Plus + Redis+
Spring Security + OAuth2 + Freemark
搭建的一套cms 系统，数据库采用 mysql 数据库，文件服务器采用 Fastdfs 
全文检索采用 Solr 。
前端架构采用ant design vue 前后端分离的系统架构。
门户系统采用的 静态模板生成技术，直接生成的静态 html 模板，js + jQuery 作相应的辅助。
部署服务 采用 nginx 门户系统和 后台 管理系统 采用正向代理正常部署，服务端采用反向代理暴露接口。ThinkItCMS 的服务端在接口限制方面都可以灵活配置分配权限，保证系统的最大安全。无特殊要求亦可以内网部署服务端

ThinkItCMS 采用目前最流行的 JEE 架构 SpringBoot 开发的一个CMS 系统其中涉及到不少开源的技术本次说明一下其中的技术框架有如下：
数据库：mysql + druid 连接池
ORM技术:Mybatis + MybatisPlus
权限技术：Spring Security + OAuth2
模板技术：Freemark 
定时任务技术：Quartz
缓存技术：Redis
日志技术：Slf4j
检索技术：Solr
文件服务器：Fastdfs
消息通知：WebSocket
项目部署容器：nginx （nginx 用于部署静态页和管理端页面）可通过反向代理访问server 以上就 ThinkItCMS用到的一些技术框架


#### 安装教程

### 特别说明
系统支持 默认的fastdfs（支持断点续传） 、七牛云OSS（不支持断点续传）阿里云OSS（支持断点续传） 等第三方云存储可自由切换，后期将会集成更多的第三方oss 以供满足不同用户需求
请务必按照本文档部署运行章节 进行操作，减少踩坑弯路！！
#### 注意：如果缺少jar 包请 替换您的 maven setting.xml 下载链接如下：
链接：https://pan.baidu.com/s/1xa131wbtplBp2Vbo1oucSw 
提取码：u4i2

如果您对本 ThinkItCMS 感兴趣可以加入QQ群关注最新动态 QQ群:313095864
[加群连接](https://jq.qq.com/?_wv=1027&k=5QtXTll)
### 环境说明

| 中间件 | 版本 | 备注 |
| --- | --- | --- |
| JDK | 1.8 | 强制要求 |
| MySQL | 5.7 + | 强制要求 |
| Redis | 3.2 + | 没测试以下版本 |
| node | 8.0 + |  |
| npm | 6.0 + |
本人采用 idea 开发其中用到了  Lombok 插件，如果不安装 插件会导致代码异常无法编译

[Lombok  IDEA安装方法](https://blog.csdn.net/zhglance/article/details/54931430)

[Lombok  ECLIPSE安装方法](https://blog.csdn.net/arkblue/article/details/52608213)

[文件服务器安装教程](https://blog.csdn.net/qq_34301871/article/details/80060235)

[文件服务器安装教程所需要资源](http://note.youdao.com/noteshare?id=9a139484bbedadf2ac2376a8fcf33dbb&sub=wcp1565775354933664)

[Linux Jdk 安装教程](https://www.cnblogs.com/116970u/p/10400436.html)

[Redis 安装教程](https://blog.csdn.net/zh15732621679/article/details/78507579)

solr: 下载地址：
下载 solr 文件开始部署
链接：https://pan.baidu.com/s/1VOGREGugl9snE-sH2BYIXg 
提取码：i2lk 

 solr 安装 solr 是一款Solr是一个高性能，采用[Java](https://baike.baidu.com/item/Java/85979)开发，

[![Solr](https://images.gitee.com/uploads/images/2020/0303/160826_cc1a5919_608975.jpeg)](https://baike.baidu.com/pic/Solr/4101582/0/7ac88051c1b20c6742a75be1?fr=lemma&ct=single "Solr")Solr

基于Lucene的全文搜索服务器。同时对其进行了扩展，提供了比Lucene更为丰富的查询语言，同时实现了可配置、可扩展并对查询性能进行了优化，并且提供了一个完善的功能管理界面，是一款非常优秀的[全文搜索引擎](https://baike.baidu.com/item/%E5%85%A8%E6%96%87%E6%90%9C%E7%B4%A2%E5%BC%95%E6%93%8E)。

ThinkItCMS采用 solr 作为 全文检索服务器 其中一些字段已经配置过了，如果你需要扩展字段可以自行设置。因为 solr 提供了 内置的 jetty 我们 可以直接 以 jetty 容器运行 。下载 ThinkItCMS提供的 ThinkItCMS进入 bin 目录 后 执行linux 使用   solr start 启动 linux  下使用 solr start -force 启动solr 当看到 以下 界面说明 solr 启动成功

接下来 我们可以通过 访问 [http://127.0.0.1:8983/solr/#/](http://127.0.0.1:8983/solr/#/)
后 会看到  search happy 字样

说明成功部署。后就可以直使用了。

### 启动说明
上述环境安装和配置完成后开始启动后端项目中的 think-web 的 ThinkItCMSApplication.java 的main 方法后启动 serve 服务，
server 启动后 在启动我们的 vue 管理端  前端项目[下载地址 ](https://gitee.com/slfj/ThinkItCMS-VUE)
git clone vue 项目到本地后 先执行 npm install 后在执行 npm run serve 就可以启动 vue 管理端的项目了，启动成功后，我们需要修改 util 文件夹 下的 request.js 修改 api 接口请求地址为你自己的serve 就可以登录系统，登录成功我们就完成了，管理端的登录，那门户项目如何访问呢？
在访问门户之前我们需要先了解一下 门户文件是怎么生成的，
首先门户文件不和 咱们的springmvc 或者其他的springboot 的项目 采用 jsp 或者 themleaf 模板直接访问后台服务地址就能访问的。
门户是静态的，是通过系统生成的静态html 文件，你可以把这些文件放到 tomcat 或者 nginx 等容器下就可以访问，每次更改数据都会重新生成 html,那么总不能手动去复制到 tomcat 容器或者 nginx 容器吧？是的，所以我们需要配置 ，本系统默认采用 nginx 作为容器来进行访问，也就是说我们把静态文件生成到指定位置就可以访问了。具体文章时如何生成的以及模板生成原理 可以购买文章查看  文档地址： https://www.kancloud.cn/lbcms/lbcms 不定期更新

#### 使用说明

由于 ThinkItCMS 是一款开源软件，您可以在此基础上做修改变更，单务必保留版权标识，针对个人非商用用户可联系作者获取 免费授权，企业、事业单位需获得授权后方可使用(商用授权获取方式:扫描下方微信二维码添加微信好友后详聊)，如在使用过程中由于开发过程中代码存在的 bug 导致您的利益受损 ThinkItCMS 不对此负责，但 ThinkItCMS 将会完善代码更新BUG。如果您对本 ThinkItCMS 感兴趣可以加入QQ群关注最新动态 QQ群:313095864
[加群连接](https://jq.qq.com/?_wv=1027&k=5QtXTll)
[微信二维码](https://images.gitee.com/uploads/images/2020/0303/161145_c699935b_608975.png "wxgzh.png")

### 由于采用前后端分离的项目搭建vue 前端项目[下载地址 ](https://gitee.com/slfj/ThinkItCMS-VUE)

门户演示地址：http://www.thinkitcms.com/


管理端演示地址：http://m.thinkitcms.com  账户：manager  密码：111111

### 打赏方式

 

 

#### 参与贡献

感谢 [@sanluan](https://gitee.com/sanluan)  给与的指导和帮助，同时感谢其提供的开源工具类

#### 技术文档资源

由于时间有限，在此整理了一份 技术开发文档，有需要的小伙伴们可以购买看看，文档写的可能有些仓促，但是后期会慢慢修正.文档不免费，保持更新，有能力的小伙伴支持一下，如果您在使用过程中遇到什么问题也可以在群里提问，看到的话会给您回复。感谢！
文档地址：https://www.kancloud.cn/lbcms/lbcms


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)