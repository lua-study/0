# dmcloud

#### 介绍
学习各大开源框架和自己的技术栈融合

#### 软件架构
软件架构说明 
springcloud eureka 注册中心

springcloud zuul 网关鉴权

spring cloud oauth2 

MySQL

redis

prometheus+granfa

elk日志收集


#### 安装教程

1. git clone https://gitee.com/08081/dmcloud.git
2.  启动eureka 注册中心
3.  启动 dm-zuul 网关
4.  启动 dm-auth 认证服务器
5.  启动 dm-system 用户服务

#### 使用说明

1.  请求网关 localhost:9070/token/oauth/token
curl --location --request POST 'localhost:9070/token/oauth/token' \
--header 'Content-Type: application/json' \
--header 'Authorization: Basic ZG06ZG0=' \
--data-urlencode 'username=tom' \
--data-urlencode 'password=1' \
--data-urlencode 'grant_type=password' \
--data-urlencode 'scope=read write'

 获取token
2.根据token 请求其他服务
 
  在header里 Authorization     bearer 你获取的access_token 
3.  xxxx

#### 参与贡献

1.  Fork 本仓库
2.  新建 Feat_xxx 分支
3.  提交代码
4.  新建 Pull Request


#### 码云特技

1.  使用 Readme\_XXX.md 来支持不同的语言，例如 Readme\_en.md, Readme\_zh.md
2.  码云官方博客 [blog.gitee.com](https://blog.gitee.com)
3.  你可以 [https://gitee.com/explore](https://gitee.com/explore) 这个地址来了解码云上的优秀开源项目
4.  [GVP](https://gitee.com/gvp) 全称是码云最有价值开源项目，是码云综合评定出的优秀开源项目
5.  码云官方提供的使用手册 [https://gitee.com/help](https://gitee.com/help)
6.  码云封面人物是一档用来展示码云会员风采的栏目 [https://gitee.com/gitee-stars/](https://gitee.com/gitee-stars/)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)