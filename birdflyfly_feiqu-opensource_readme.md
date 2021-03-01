# 飞趣社区开源版本

#### 介绍
飞趣社区做了快两年了，最近也想不到什么新功能去做了，于是想起了开源的事情，我一个人开发终究不能让这个社区走向前方，于是我下定决心开源，开源之前我也蛮纠结的，就像是把自己辛辛苦苦做的东西送给别人了，但是转念一想，也许这会为我的社区向前发展提供助力，不同人的思想或许会激发灵感，所以我就决定开源了。

社区网站地址：www.flyfun.site 
qq讨论群：632118669

有什么问题可以在下面提问，或者加群讨论。

这个项目一开始使用springmvc开发，后来听了群里的人说springboot多么好多么好的，我也就上了贼船，开始了springboot之旅，从此一发不可收拾。

springmvc项目就不演示给大家看了，毕竟那么多配置文件，想想也烦，大家一起加入springboot 大家庭吧

此项目使用了hutool工具类作支撑，参考了zheng项目（https://gitee.com/shuzheng/zheng）以及ruoyi的项目（https://gitee.com/y_project/RuoYi），这两个项目给了我很多的帮助，
在此谢谢这两个项目的作者，页面ui使用了layui，集成了阿里云oss（支持前端和后端上传）、七牛云，支持代码自动生成，支持数据库读写分离，减去了70%的工作量，让你更多的精力放在写业务代码的过程中。

当然这个项目还可以用来给你们公司做前端展示页面，也是非常方便的。



#### 软件架构
使用java作为后端开发 使用springboot、mysql、druid、 mybatis、pagehelper、javamail、redis、beetl、hutool、layui、jeesuite、webmagic相关技术集成开发的一个web应用
并且支持爬虫、发邮件。你想要的功能在这应有尽有，如果你还希望集成什么，欢迎提issue


#### 安装教程

1. mysql创建一个数据库 cwd_boring
2. 导入sql sql目录下面的
3. 安装redis 6379端口

#### 使用说明

1. 使用jdk8
2. mysql 5.7 用户名密码 root root
3. 配置文件里面为
    application-dev.yml:
        feiqu-redis:
          servers: localhost:6379
          password:
        mail:
            default-encoding: utf-8
            host:  smtp.qq.com #改成你的邮件主机
            username: 123@qq.com #邮件服务 登陆用户名
            password: 2333 #邮件服务 登陆密码
    必须改为自己的配置才能生效
    java类里面
    com.feiqu.framwork.constant.CommonConstant.USER_ID_COOKIE
    com.feiqu.framwork.constant.CommonConstant.USER_COOKIE_SECRET
    com.feiqu.framwork.constant.CommonConstant.FORGET_PASSWORD_SECRET 
    必须改为自己的配置才能生效
4. ip2region.db -> \feiqu-opensource\feiqu-front\src\main\resources\ip2region\ip2region.db 转移到自己的文件位置 application-dev.yml:22
5. com.feiqu.framwork.aspectj.DataSourceAspect 把注释去掉支持读写分离
6. 阿里云和七牛云的配置在——》feiqu-opensource\feiqu-front\src\main\resources\application.properties
   七牛云
       public.filesystem.provider=qiniu
       public.filesystem.bucketName=***
       public.filesystem.urlprefix=***
       public.filesystem.accessKey=***
       public.filesystem.secretKey=***
   阿里云
       aliyun.filesystem.bucketName=***
       aliyun.filesystem.endpoint=***
       aliyun.filesystem.accessKey=***
       aliyun.filesystem.secretKey=***
       aliyun.filesystem.urlprefix=***
   改成你想要的
7. 支持第三方登陆 现已集成了qq、微博  微信好像要钱就没弄。。。。
    application.properties里面
    app_id_qq=***
    app_key_qq=***
    
    app_id_sina=***
    app_key_sina=***
    改成自己的就可以了


#### 参与贡献

1. Fork 本仓库
2. 新建 Feat_xxx 分支
3. 提交代码
4. 新建 Pull Request


#### 码云特技

1. 使用 Readme\_XXX.md 来支持不同的语言，例如 Readme\_en.md, Readme\_zh.md
2. 码云官方博客 [blog.gitee.com](https://blog.gitee.com)
3. 你可以 [https://gitee.com/explore](https://gitee.com/explore) 这个地址来了解码云上的优秀开源项目
4. [GVP](https://gitee.com/gvp) 全称是码云最有价值开源项目，是码云综合评定出的优秀开源项目
5. 码云官方提供的使用手册 [https://gitee.com/help](https://gitee.com/help)
6. 码云封面人物是一档用来展示码云会员风采的栏目 [https://gitee.com/gitee-stars/](https://gitee.com/gitee-stars/)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)