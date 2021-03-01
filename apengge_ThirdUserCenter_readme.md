#NotificationServer
===========================

## 产品说明

消息通知服务的服务器程序。程序只通过http、socket.io、socket方式对外提供restful风格的服务，不包含任何与WEB浏览器的应用程序或代码。

## 目录结构说明

```
./NotificationServer
├── api
│  ├── controllers                //控制器代码，参考sails官方文档
│  ├── models                     //业务模型代码，参考sails官方文档
│  ├── policies                   //自定义安全认证，参考sails官方文档
│  ├── responses                  //自定义回复，参考sails官方文档
│  └── services                   //自定义服务，参看sails官方文档
├── assets                        //资源文件，主要存放JS、图片文件。由于程序只提供restfule风格的服务，不开放使用。
├── config                        //全局配置，参看sails官方文档
├── doc                           //服务器设计文档说明
├── tasks                         //grunt测试任务，参看sails官方文档
├── test                          //测试代码
│  ├── unit                       //单元测试
│  │  ├── controllers             //测试控制器代码
│  │  ├── models                  //测试业务模型代码
│  │  └── ...                     //
│  ├── fixtures
│  ├── ...
│  ├── bootstrap.test.js          //运行单元测试前，预先需要设置的代码
│  └── mocha.opts                 //抹茶测试启动配置
├── views                         //HTML文件。由于程序只提供restfule风格的服务，不开放使用。
├── autoClearService              //自动清除服务
└── reminderService               //事件提醒服务
```

## 测试
### 单元测试

单元测试采用mocha（抹茶）。测试代码存放位置按目录结构说明存放。

运行单元测试的命令

```
$mocha
```



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)