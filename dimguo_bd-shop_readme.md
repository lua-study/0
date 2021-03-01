------------------------------------------------

> BDShop 

------------------------------------------------
##交流QQ群:107304892

 **2017-10-03  半年第一次更新了 修复所有bug 请大家更新一下** 


BDShop是国内少有前后端完全分离的java商城项目.
## BDShop 系统简介
BDShop商城系统是B2C模式的电子商城

后端基于springboot 职责单一提供api服务

前端基于nodejs 纯html5 css3 通过json 和后端api交互。


实现的前后端分离架构的项目

![前后端分离架构](https://git.oschina.net/uploads/images/2017/0426/154407_2f5bf086_127930.png "前后端分离架构")





相关技术文章

[前后端分离的思考与实践](http://blog.jobbole.com/65513/)

[浅谈前后端分离技术](http://www.jianshu.com/p/f1287e1aee50)


##BDShop技术路线
后端构建:spring-boot+mybatis+pagehelper+Swagger2构建RESTful API

前端构建:nodejs+gulp+requirejs+art-template+bootstrap+weui


安装运行步骤

一、api-server

前提要安装好 jdk8 maven 

1.  $ mvn clean install

2   $ cd api-server

3   $ mvn spring-boot:run

4  打开浏览器：http://localhost:8080/swagger-ui.html

二、front-project

    前提安装好nodejs 6.9


    1 安装node http://www.cnodejs.org 官网下载 傻瓜式安装 一直确定就行 默认安装在 C:\Program Files\nodejs


    2 检测安装结果 打开 命令行 输入 node -v 会出现node版本 输入 npm -v 会出现npm版本


    3 配置npm全局环境 在C:\Program Files\nodejs 这里新建连个文件夹 "node_global"及"node_cache" 打开cmd 用管理员 身份打开 输入命令：npm config set prefix "C:\Program Files\nodejs\node_global" 输入命令 ：npm config set cache "C:\Program Files\nodejs\node_cache"


    4：配置环境变量 在系统变量下新建"NODE_PATH"，输入”C:\Program Files\nodejs\node_global\node_modules“用户变量 用户变量"PATH"修改为“C:\Program Files\nodejs\node_global\”；


    5：检查 cmd命令 输入npm install gulp -g 然后看看 node_global文件夹有没有gulp文件


    
    6.$ npm install -g cnpm --registry=https://registry.npm.taobao.org

    7.$ cnpm install -g gulp 

    8.$ cd front-projec

    9.$ cnpm install

    10.$ gulp

    11 打开浏览器：http://localhost:4865

    12 后台管理：http://localhost:4865/page/manage_login.html

    13 管理员帐号：admin 密码：111111



## BDShop 后端项目截图
![商品列表](https://git.oschina.net/uploads/images/2017/0424/120936_4639108f_127930.png "商品列表")
![输入图片说明](https://git.oschina.net/uploads/images/2017/0424/121305_0af0cadc_127930.png "在这里输入图片标题")

![输入图片说明](https://git.oschina.net/uploads/images/2017/0424/121319_82d079a1_127930.png "在这里输入图片标题")
## BDShop 前端项目截图
![输入图片说明](https://git.oschina.net/uploads/images/2017/0424/121753_bb301169_127930.png "在这里输入图片标题")

![输入图片说明](https://git.oschina.net/uploads/images/2017/0424/121915_65a1accd_127930.jpeg "在这里输入图片标题")

![输入图片说明](https://git.oschina.net/uploads/images/2017/0424/121956_2d6f6900_127930.jpeg "在这里输入图片标题")

##捐赠 金额随意：
![输入图片说明](https://git.oschina.net/uploads/images/2017/0424/145453_3d03f160_127930.png "在这里输入图片标题")





```
这里输入代码
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)