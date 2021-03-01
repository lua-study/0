# lss php 框架


#### 介绍
php 框架，基于mvc模式 我们在努力~~~~~

#### 软件架构
软件架构说明

#### 安装教程

第一种方法：需要服务器，安装lamp环境以及swoole，把全部代码置入其中

第二种方法：开启虚拟机linux，安装lamp环境以及swoole，把websocket.php放进去，再开启本地的PHP环境，运行index.html

#### 使用说明

1. config

    chat.sql 数据库
    
    config.php 本地配置定义
    
    doAction.fun.php 封装登陆注册等方法
    
    mysql.fun.php 数据库增删改查代码的封装
    
    page.fun.php 分页封装
    
    upload.fun.php 上传代码封装

2. css

    页面样式
3. images

    头像、样式等图片集合
4. js

   common.js 实现ajax跳转
   
   tabs.js 实现聊天房间的显示、隐藏，以及websocket的主要功能
5. doAction.php 

   前端与后端的连接桥梁
6. include.php 
   
   包含文件
7. websocket.php swoole
   
   实现websocket的主要方法
8. index.html 

   首页，登陆
9. home.php  
   
   主页面，聊天页面

#### 参与贡献

1. Fork 本仓库
2. 新建 Feat_xxx 分支
3. 提交代码
4. 新建 Pull Request

#### 贡献人
小珊珊 雨呱呱 

### 版本说明
#####1.0.0
由珊珊开发

####1.1.1
添加APP 类 ，run 执行方法 移植到APP类

loader 类移植到config文件夹，添加psr4 自动加载标准

修改文件目录符，统一使用DIRECTORY_SEPARATOR

####1.1.2
规范文件名

新建.env环境配置文件，存放

数据库配置

引入composer

使用 http-foundation组件，用于对请求进行处理，文档  
https://symfony.com/doc/current/index.html 

使用 phpunit 组件，用于代码单元测试，文档  
https://phpunit.readthedocs.io/zh_CN/latest/



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