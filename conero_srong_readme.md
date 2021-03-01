# srong

## 项目介绍
php 轻量级框架以及常用库, wjtai 项目改进版(学习版)



## 特性

- 轻量级框架/应用
- 项目内部采用``插拔式``架构
- 支持 *phar*
- 支持*web/cli* 模式


![架构](/static/sRong.jpg)

## install/安装

> WEB

``$>php -S 0.0.0.0:1994  server.php``



> CLI

``$>php static/index.php ``




## 框架设计

###  项目结构

- `` ``
  - app 应用，默认为项目控制器文件，可为``cli/web`` 程序
      - http      ``web`` 控制器
      - bin        ``cli`` 控制器
      - config   配置文件列表
      - router   路由配置    ``开启自动路由非必须``
        - web.php   *web router 配置*
          - web.{env}.php 支持模式下不同的配置
        - cli.php  *cli router 配置*
    - static 应用程序入口
      - public   前端静态文件
        - js
        - css
        - asset
    - srong 框架核心程序(*用户无须更改文件*)
    - runtime 运行时目录
    - vendor *composer* 加载库
    - ``开发`` tests  PHPUnit 框架

### 处理过程

接入顺序： *适配器* -> *路由器*

> **适配器**

*判断接入类型，生成初始环境*

> **路由器**

*路由分发请求*



## 模式

### web

> 采用URL地址重写，解析路由

- 重写配置键 ``rewrite_key`` 
- ``auto_router`` 自动路由
  - :controller   控制器
  - :action   方法





```php
// CONFIG.PHP
[auto_router => true]

// ROUTER
Router::match('get|post', '/:controller/:action', function($contrl, $action){
    $instance = new $contrl();
    call_user_func([$instance, $action]);
});

```





### cli

> 通过解析第一个参数

``auto_router`` 自动路由

- :command   命令
- :action   命令方法

```php
// CONFIG.PHP
[auto_router => true]

// ROUTER
Router::match('cli', '/:command/:action', function($cmd, $action){
    $instance = new $cmd();
    call_user_func([$instance, $action]);
});

```



> 格式

``$> php static/index.php {command}  {action} :args :option``

- **command**
- *:参数*
  - **args**
    - ``{key=value}``
  - **option**
    - ``--option``
  - **unfind**
    - 路由失败时处理

> **cli - sr**

![](./doc/cli-sr.png)



## `sr` 默认命令管理

> 访问 sr 命令应用

```powershell
php ./static/index.php sr
```







## 常量

1. *ROOT_DIR* 项目主目录
2. *sR_Version* 版本
3. *sR_Release* 发布日期
4. *sR_Author* 作者
5. *sR_Name* 框架名称
6. *sR_Since* 项目起始日期



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)