# NewApi

#### 介绍
基于ApiAdmin二次开发，自带代码生成器的项目，只需建立项目表结构即可生成：APP接口文档，管理系统的前后端所有代码等，达到快速上线的目的！
本开源项目只提供简易功能，生成的代码文件需要手动移到指定目录！
商业版项目请加群 477492698 联系群主索要！
商业版除简易功能外，可以自动生成代码到程序运行目录，无需手动移动，
支持一键生成多语言，自动前后端路由，自动生成需要APPID和AppSecret的授权接口以及文档，无需手动录入接口数据，极大提高了项目开发效率，缩短项目开发周期，无需关注底层代码实现，可以集中精力进行项目的业务逻辑处理，更多功能敬请期待！

## 更多案例
请关注微信公众号   量子互联网络科技   获取
 
![输入图片说明](https://gitee.com/GionConnection/NewApi/raw/bda80f5625c098adbf08d989dad1f2571779d9ab/ewm.jpg "ewm.jpg")


## 快速安装

> 第一步：项目搭建
```
由于本项目是基于ApiAdmin开发，使用过程中请参考https://www.apiadmin.org/
先获取基础代码 git clone https://gitee.com/GionConnection/NewApi.git  再使用composer安装依赖包 composer install
代码生成器是Nodejs开发，需要安装Nodejs环境
```

> 第二步：数据库建立

```
database的数据库文件还原至数据库
网站账号：root
网站密码：123456
```
> 第三步：代码生成器设置
```
参考表结构以及命名规范建立数据表
打开BuildCode文件夹修改index.js文件里面的db和newdb的数据库连接信息
其中的db的数据库名字不要改
执行node index
退出系统重新登录
```

**注：安装完成后执行第三步，后台管理员的账号密码请查看：application/install/lock.ini**

**效果展示**  http://www.56.com/u72/v_MTYxNTA3MDc3.html

**新手教学**  http://www.56.com/u16/v_MTYxNTA2NDA1.html

## 项目简介

**系统需求**

- PHP >= 5.6
- MySQL >= 5.5.3
- Redis
- NodeJs

**项目构成**

- ThinkPHP v5.1.*
- Vue 2.0
- BuildCode
- ...

**功能简介**

 1. 接口文档自动生成
 2. 接口输入参数自动检查
 3. 接口输出参数数据类型自动规整
 4. 灵活的参数规则设定
 5. 支持三方Api无缝融合
 6. 本地二次开发友好
 7. 自带代码生成器一键生成所有代码

#### 联系我们

1.  码云 https://gitee.com/GionConnection/NewApi.git
2.  官方唯一QQ群 477492698
3.  微信公众号 量子互联网络科技


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)