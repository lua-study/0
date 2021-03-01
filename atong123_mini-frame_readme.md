# mini-frame

#### 介绍
简单粗暴的一款PHP框架，代码易读易扩展，性能接近原生，支持使用 Composer 引用开源类库。

## 目录结构
```
www  WEB部署目录
├─application          应用目录
│  ├─controller        控制器目录
│  ├─view              视图目录
│  │   ├─ctl           控制器对应目录
│  │   │   ├─act.php   对应视图文件
│  │   │   └─ ...      更多视图文件
│  │   └─ ...          更多控制器对应目录
│  ├─common.php        公共函数文件
│  ├─config.php        自定义配置文件
├─config               应用配置目录
│  ├─app.php           应用配置
│  ├─database.php      数据库配置
├─public               对外访问目录
│  ├─index.php         入口文件
│  ├─.htaccess         用于apache的重写
├─system               框架系统目录
│  ├─library           框架类库目录
│  │   ├─App.php       启动类库
│  │   ├─Config.php    配置类库
│  │   ├─Db.php        数据库类库
│  │   ├─Mysql.php     mysqli基础类库
│  │   ├─Router.php    路由类库
│  ├─base.php          基础定义文件
│  ├─function.php      框架内置函数库
├─vendor               第三方类库目录Composer依赖库
├─composer.json        composer 定义文件
├─README.md            README 文件

```


#### 安装教程

1.  xxxx
2.  xxxx
3.  xxxx


#### 使用说明

1.  代码简单，易读易扩展， php 新手也能参考阅读
2.  使用 composer 自动加载机制，可直接引入第三方类库丰满框架，如 ORM 类库。 

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