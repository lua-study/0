# 开发说明

1、将代码下载到GOPATH的src目录下面，并且将项目目录名称改成 alpaca_demo

2、数据库脚步在 doc/sql下面 

3、环境相关的配置文件在dev下面，具体使用哪一个文件是由环境变量ENV_MODE决定，默认是使用development.json

4、运行或者调试cmd/alpaca下面的main函数

5、浏览器中打开http://127.0.0.1:9999/web/admin, 默认用户名admin，密码111111

![img](https://oscimg.oschina.net/oscnet/up-e9c6a05249f55b24e5382480ee053f87681.png)

输入用户名、密码登录成功后，内容如下

![img](https://oscimg.oschina.net/oscnet/up-e65d328aeedd599168793765a5129068201.png)


# 目录说明

主要的几个目录的解释如下

![img](https://oscimg.oschina.net/oscnet/up-99e99677fb61129764c80d3a392d1767c32.png)

---

-- **app** 目录放项目代码

-- **app/api** 放接口调用的入口函数

-- **app/api/admin** 是后台管理的模块的接口

-- **app/api/v1** 是前台模块的接口

-- **app/bootstrap** 目录放项目启动时候，初始化的一个函数，例如加载配置文件，配置log，启动gin的路由监听等

-- **app/common** 存放公共调用函数，例如接口的返回状态码，日志log，链接mysql，加密、解密函数等待

-- **app/config** 存放配置文件的目录，要注意这里和env目录的区别，env目录下是为了项目在不同的环境下加载不同的配置文件，一些固定不变的配置可以放到 app/config下


-- **app/models** 存放数据库访问的相关函数，一般是一个数据表 对应一个文件

-- **app/routers** 存放路由配置信息

-- **app/service** 存放编写复杂的业务逻辑

---

-- **cmd** 存放项目的入口文件

---

-- **doc** 存放一些文档资料，例如sql脚步也放到这里了

---

-- **env** 存放环境相关的配置，具体使用哪一个文件是由环境变量ENV_MODE决定，默认是使用development.json

---

-- **storage** 存放程序运行时的一些配置，例如日志，程序pid默认放到这里了

---

-- **vendor** 项目的依赖包在这里，用govendor管理

---

-- **web** 静态资源目录在这里

---

## 设计架构

入口函数内容如下：

![img](https://oscimg.oschina.net/oscnet/up-e8dfc357732ee7c5d9072f9458a38fd6121.png)


代码的总体结构设计如下图：

![img](https://oscimg.oschina.net/oscnet/up-75905893702a4524a3d38ac1e7be11c7f02.png)

**bootstrap** 包是启动相关的函数。main函数调用bootstrap包中的函数初始化配置信息，如加载配置文件，配置log，开启http监听等。

**common包** 里面是一些公用函数，任何其他包都可以引用common包，但是common包禁止引用除了vendor以外的其他一切包

**api接口** 函数可以引用common包、models包、services包等实现具体的业务逻辑

**services包** 函数可以引用common包，models包实现具体的业务逻辑

**models包** 可以引用common包，但是不可以引用services包

Go语言初学经常会遇到包循环引用的问题，因此梳理清晰包与包直接的调用关系很重要


## log服务

**log服务**使用的是logrus框架，在app/bootstrap/log 中进行初始化配置

common.Log 是一个logrus的实例，使用log的时候，可以直接使用common.Log.Info(""log内容") 函数记录log

![img](https://oscimg.oschina.net/oscnet/up-1eff4f9366e013787a697ba522a74b85407.png)


## config服务

**config服务**基于viper框架搭建，加载env环境变量使用是viper，在app/bootstrap/config 中进行初始化配置

并且封装了一个config包，在app/config下面，使用时候，可以直接使用这个包。

![img](https://oscimg.oschina.net/oscnet/up-cf4f2329c885480a5d2a636647d32ab65e9.png)


## mysql服务

**mysql服务**使用的gorm框架

建立链接的函数是app/common/mysql.go里面的 ``` Mysql() ```

主要的操作封装在了models

![img](https://oscimg.oschina.net/oscnet/up-a88544f11bcf7ccf89c980b0213452af733.png)


## Http服务

**Http服务**使用的是gin框架

在 app/bootstrap/router 中进行初始化配置，路由配置文件在 app/routers中

![img](https://oscimg.oschina.net/oscnet/up-61e4c3b29a01d7ebf990ffb65f35dc7059c.png)


## 获取Http服务请求参数

可以使用gin框架提供的方法进行获取http服务的请求参数

也可以使用实例中封装的  ``` api.Input(c, "UserName", "") ``` 函数获取


## 返回Http服务的请求结果

可以使用gin框架提供的方法进行获取http服务的请求参数

也可以使用实例中封装的  ``` 	api.Output(c, res, err) ```  返回结果

![img](https://oscimg.oschina.net/oscnet/up-33cfd702d9ad2657d72fb686da1df20d9e1.png)


## Http返回结果的设计


返回结果包括三部分，code、data、error

code必有，内容用字符串表示，不是数字

data是在有请求结果集的时候，用于放结果集

error是在出错的时候会用


code 有三大类

** 结果正常 **
``` code:"success"" ``` 表示请求正常


** 用户错误 **

格式就是 ```fail.xxx``` ,以fail开头，后面接具体错误内容，用逗号分割，例如:

``` code:"fail.param.null.password" ``` 可以表示用户输入的密码是空


** 系统错误 **

``` code:"error"" ``` 表示系统内部错误，例如mysql没恋上，其他panic错误

返回的code放在了 app/common/code包里面

![img](https://oscimg.oschina.net/oscnet/up-7b35ca4fe9dbf84611b2668433a93383474.png)


## 后台管理Web段

**后台管理Web段**使用的是alpaca-spa框架

在 app/web/admin里面


## 参考资料

**go语言参考资料**

**gin框架**

**gorm框架**

**logurs框架**

**viper框架**

**alpaca-spa框架**


## 沟通交流

有问题可以加入QQ群或者我的微信交流沟通

**QQ群**

![img](https://oscimg.oschina.net/oscnet/up-3ae028bf6e563febeba77c084bfb9113f36.png)


**微信，添加时请做好备注**

![img](https://oscimg.oschina.net/oscnet/up-ced8a95f5863746169486178b29c6b186f1.png)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)