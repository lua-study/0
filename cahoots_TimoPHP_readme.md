##TimoPHP

一个简单、快速、规范、灵活、扩展性好的PHP MVC+框架。

目前，已经用TimoPHP做了4个项目，包括TimoPHP官网，MiniApi（管理app接口文档的工具），app接口、项目后台（公司内部不方便透露）

官网：http://www.timophp.com/

文档：http://www.timophp.com/document/

##我们的目标

做一个轻量级并支持大型应用开发的PHP框架

##框架名称由来

原本设计的时候名称是carPHP，取名car的原因是，整个框架运行就像一辆汽车的运行过程，从点火（fireUp）到发动机（boot）启动，再到引擎（Engine）开始运作，带动各部件（components）协调工作，carphp.com被注册了，所有，再取一个名字吧，想了半天也想不出什么好名字，最后，就用Timo这个词得了。

##MVC+模式

除了M层，我们还可以根据项目实际情况增加层，比如基础层（Base）业务逻辑层（Business/Logic）服务层（Service）策略层（strategy）等等

##MVVC模式

把MVC模式的V（视图）分成了视图模型层和视图层（也可以说是模版层），当然，视图模型层是可选，没有的话就是经典的MVC模式

##特点
    1、PHP5.4+（支持PHP7）
    2、PSR标准
    3、轻量级，扩展灵活
    4、自定义异常处理，如404
    5、原生模版解析
    6、支出视图组件
    7、模板支持多主题、layout（布局）
    8、写app接口还是挺爽的
    9、加入对cli模式支出，用来写服务、定时脚本挺好的
    10、增加依赖注入服务容器，实现组件之间的松耦合
    11、支持数据库读写分离设置，可具体到某张表
    12、支持控制器分组路由，降低控制器复杂度
    
##目录结构

```
/data
  |-TimoSNS                         项目目录(自己项目名称，比如用TimoPHP开发的社区应用，叫TimoSNS，自定义)
  |   |-app                         应用目录
  |   |   |-admin                   后台
  |   |   |-api                     APP接口
  |   |   |-m                       H5
  |   |   |_web                     PC端应用
  |   |   |   |-controller          控制器目录
  |   |   |   |-[business]          复杂的业务逻辑可以存放在这里，[]表示可选，名称自定义，如business、logic等
  |   |   |   |-model               单个项目会用到的模型，公共模型放到common/model目录下面
  |   |   |   |-[service]           定义一些单个项目需要用到的底层服务（可选、可自定义名称）
  |   |   |   |-template            模版目录
  |   |   |   |   |-default         默认主题
  |   |   |   |   |   |-Index
  |   |   |   |   |   |-Space
  |   |   |   |   |   |-default.layer.php   layout布局
  |   |   |   |   |-win10           一个win10的扁平化主题
  |   |   |   |-[view]              视图目录，可以封装一些方法供模版中使用（可选）
  |   |   |   |_config.php          项目配置文件
  |   |-cache                       运行时缓存目录
  |   |-[common]                    公共类库目录
  |   |   |-business                公共业务逻辑
  |   |   |-contract                约定、协议（接口）
  |   |   |-model                   公共模型目录
  |   |   |-provider                服务提供者目录
  |   |   |-task                    异步任务
  |   |-config                      公共配置目录
  |   |-lib                         自定义组建、类库、服务等
  |   |-logs                        debug日志目录
  |   |-public                      WEB目录（对外访问目录）名称自定义，如wwwroot、public
  |   |   |-admin                   admin应用目录
  |   |   |-api
  |   |   |-m
  |   |   |_web
  |   |       |-static              静态资源目录
  |   |       |   |-css
  |   |       |   |-images
  |   |       |   |-js
  |   |       |   |_lib             js第三方库
  |   |       |_index.php           web应用入口文件
  |   |_fireUp.php                  点火，启动框架（钥匙/火花塞）
  |-TimoPHP                         框架，和项目在同一级目录
      |-cli
      |-config
      |-ext                         第三方组建目录
      |-Library
      |   |--Cache
      |   |   |--File.php
      |   |--Core
      |   |   |--Application.php
      |   |   |--Cache.php
      |   |   |--Config.php
      |   |   |--Container.php      服务容器
      |   |   |--Controller.php
      |   |   |--Db.php
      |   |   |--Engine.php         引擎
      |   |   |--Exception.php
      |   |   |--Input.php
      |   |   |--Log.php
      |   |   |--Model.php
      |   |   |--Request.php
      |   |   |--Response.php
      |   |   |--Router.php
      |   |   |--Session.php
      |   |   |__View.php
      |   |--Image
      |   |   |--Gif.php
      |   |--Session
      |   |   |--Memcached.php
      |   |   |--Redis.php
      |   |--Support
      |   |   |--ServiceProvider.php    服务提供者基类
      |   |--Auth.php
      |   |--Captcha.php
      |   |--Curl.php
      |   |--Helper.php
      |   |--Image.php
      |   |--Loader.php
      |   |--UploadFiles.php
      |   |--Validate.php
      |_boot.php                    框架启动脚本（发动机）
 ```       
 
## 基本骨架
 
 http://git.oschina.net/tomener/timo-skeleton
 
## 参考项目
 
 TimoPHP官网 http://www.timophp.com/
 TimoSNS社区 http://git.oschina.net/tomener/TimoSNS

## 新建一个项目

php cli/tools create project_name(你要建立的项目名称，如TimoSNS)


## 第二种目录部署

 ```
  app
    |-admin
    |-api
    |-m
    |_web
  wwwroot
    |-admin
    |    |-static
    |    |-index.php
    |-api
    |-m
    |-static
    |    |-css
    |    |-images
    |    |-js
    |    |_lib
    |-.htaccess
    |-favicon.ico
    |-index.php

 ```
## 访问方式：

    web下面的
    1、http://www.timophp.com/index/index
    2、http://www.timophp.com/blog/show/10001
    
    admin下面的
    1、http://www.timophp.com/admin/index/index
    2、http://www.timophp.com/admin/user/detail/10008
    
    api、m和admin一样
    


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)