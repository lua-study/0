### 介绍
- http请求api的工具
- 和APP、前端对接时，经常涉及到接口的对接，为了方便管理，写了这么一个工具
- 我们团队用了6-7年了，感觉到大家应该也是需要这么一个工具的
- 最初的代码是用spring-mvc写的，最近改用tio-http了，一健部署和访问
- 前端代码用了easyui，该框架是GPL协议开源的，所以请大家遵循此开源协议

### 安装教程

1. 使用了最新的t-io，请用户自行下载安装：https://gitee.com/tywo45/t-io
2. 导入工程到eclipse，运行org.tio.http.apitool.HttpApiToolStarter即可
3. 运行package.bat，会将项目打包，进入到target/tio-http-apitool目录，双击startup.bat即可运行

### 配置
- 在app.properties文件中可以配置http端口和页面路径（页面路径配不配无所谓，程序会智能判断）

### 运行界面
![](https://images.gitee.com/uploads/images/2019/0710/211032_82a9c53c_355738.png)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)