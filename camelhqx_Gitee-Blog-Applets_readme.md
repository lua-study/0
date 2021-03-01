

 
     
 
 
  码云博客 第三方小程序
 



## 概述
[码云博客小程序] 是 [码云博客] 的小程序版本实现。

小程序后端是基于 [Wext-server-thinkphp3.2] 实现的数据爬虫，使用 [ThinkPHP3.2] 框架开发。[Wext-server-thinkphp3.2] 是集成小程序账号体系的快速开发Demo。

小程序前端使用ES6+小程序原生语法，基于 [ZanUI WeApp] 和 [Wext] 开发的小程序应用。[ZanUI WeApp] 是有赞移动 Web UI 规范 ZanUI 的小程序现实版本。[Wext] 是针对小程序API和部分JS功能实现封装的小程序组件。


## 截图预览

 
     
     
     
     
 

## 下载
``` bash
git clone https://gitee.com/normalcoder/Gitee-Blog-Applets.git
```

## 目录结构
```
│   client  小程序端代码
│   server  服务端代码
│   screenshots  效果截图
```

## 使用
- 小程序账号申请、小程序后台配置和使用语法请自行查阅 [小程序简易教程]、[小程序框架介绍]
- 注册申请小程序，从小程序账号后台获得小程序的 **appid** 和 **appsecret**，同时配置业务域名和请求域名。
- 通过 `server\database\` 下的SQL文件导入数据库到MySQL
- 通过 `server\application\Common\Conf\db.php` 配置修改数据库连接
- 通过 `server\application\Common\Conf\miniapp.php` 配置修改小程序 **appid** 和 **appsecret**
- 修改小程序项目配置文件 `client\project.config.json` 中的 **appid** 为开发者自己的小程序appid
- 通过「微信开发者工具」将 `client` 目录导入为小程序项目即可

## 相关项目/参考网址
[码云博客]、[Wext]、[Wext-server-thinkphp3.2]、[ZanUI WeApp]、[小程序简易教程]、[小程序框架介绍]


[码云博客]: https://blog.gitee.com/
[码云博客小程序]: https://gitee.com/normalcoder/Gitee-Blog-Applets
[Wext]: https://gitee.com/wext/wext
[Wext-server-thinkphp3.2]: https://gitee.com/wext/wext-server-thinkphp3.2
[ThinkPHP3.2]: http://thinkphp.cn
[ZanUI WeApp]: https://github.com/youzan/zanui-weapp
[小程序简易教程]: https://mp.weixin.qq.com/debug/wxadoc/dev/
[小程序框架介绍]: https://mp.weixin.qq.com/debug/wxadoc/dev/framework/MINA.html


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)