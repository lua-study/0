![](http://www.tpframe.com/data/assets/images/mark_logo.jpg) 

TPFrame 6.x
===============
TPFrame 6.0基于最新版thinkphp6开发，保持了ThinkPHP6的所有特性，延续了tpframe 3.x版本的高扩展、高效率、低耦合的特性，在代码上做了更深的强化，优化核心，减少依赖，为个人或企业建站提供高效、快速解决的方案，TPFrame 6.x的主要特性：

 + 采用`PHP7`强类型（严格模式）
 + 全新的事件系统
 + 模板引擎分离出核心
 + 内部功能中间件化
 + 对Swoole以及协程支持改进
 + 网站目录结构清晰、合理
 + 保留ThinkPHP6所有模式，你可以运用任何ThinkPHP6可用的操作
 + 系统插件式模板扩展，丰富的免费插件可直接下载使用
 + 基于命名空间和众多PHP新特性
 + 核心功能组件化
 + 更灵活的控制器
 + 重构的模型和数据库类
 + 配置文件可分离
 + 简化扩展机制
 + API强化支持，几句代码搞定接口、接口文档问题
 + 命令行访问支持
 + REST支持
 + 引导文件支持
 + 方便的自动生成定义
 + 分布式环境支持
 + 更多的社交类库

> TPFrame 6.x的运行环境要求PHP7.1+。

## TPFrame 3.x 版本
tpframe 3.x (https://gitee.com/37duman/tpframe)

## 标准目录结构

初始的目录结构如下：

~~~
www  WEB部署目录（或者子目录）
├─addon           		插件目录
│  └─...        		可扩展模块目录
├─app           		应用程序目录
│  ├─common             公共模块目录
│  ├─backend            后台模块目录
│  ├─frontend           前台模块目录
│  ├─extra           	配置文件目录
│  ├─install            安装模块目录（安装后建议删除）
│  ├─module_name        模块目录（可以更改）
│  │  ├─config      	模块配置文件目录
│  │  ├─controller      控制器目录
│  │  ├─logic      		逻辑层目录
│  │  ├─model           模型目录
│  │  ├─service      	服务层目录
│  │  ├─validate      	数据验证层目录
│  │  ├─middleware      模块中间件
│  │  ├─event	      	模块事件
│  │  ├─lang	      	模块语言包
│  │  └─ ...            更多类库目录
│  ├─app.php            应用主配置文件
│  ├─common.php         公共函数文件
│  ├─lang.php           语文包配置文件
│  ├─middleware.php     中间件配置文件
│  ├─route.php          路由配置文件
│  ├─tags.php           应用行为扩展定义文件
│  └─database.php       数据库配置文件
├─coreframe           	核心代码目录
│  ├─source        		tpframe源码目录
│  ├─package        	第三方程序包
│  └─...        		更多可扩展模块目录
├─data                	数据资源目录（对外访问目录）
│  ├─runtime         	运行时目录
│  ├─install.lock       安装标识文件
│  └─...		        其它文件
│─public                程序入口文件目录
│  ├─index.php          应用入口文件
│  ├─assets             插件、模板等资源文件目录
│  ├─data           	数据目录
│  └─...            	其它更多目录
│─extend                扩展类库目录
├─theme              	模板目录
│  ├─backend            后台模板文件目录
│  ├─frontend           前台模板文件目录
│  └─install            安装模板文件目录
│─vendor                第三方类库目录
│
├─composer.json         composer 定义文件
├─LICENSE.txt           授权说明文件
├─README.md             README 文件
├─think                 命令行入口文件
├─...            		其它文件
~~~

## 自动安装
系统运行后会自动安装
重新安装的用户,请手动删除`data/install.lock`文件和'app/extra/database.php'文件

## 命名规范

`TPFrame`遵循PSR-2命名规范和PSR-4自动加载规范，并且注意如下规范：

### 目录和文件

*   目录不强制规范，驼峰和小写+下划线模式均支持；
*   类库、函数文件统一以`.php`为后缀；
*   类的文件名均以命名空间定义，并且命名空间的路径和类库文件所在路径一致；
*   类名和类文件名保持一致，统一采用驼峰法命名（首字母大写）；

### 函数和类、属性命名
*   类的命名采用驼峰法，并且首字母大写，例如 `User`、`UserType`，默认不需要添加后缀，例如`UserController`应该直接命名为`User`；
*   函数的命名使用小写字母和下划线（小写字母开头）的方式，例如 `get_client_ip`；
*   方法的命名使用驼峰法，并且首字母小写，例如 `getUserName`；
*   属性的命名使用驼峰法，并且首字母小写，例如 `tableName`、`instance`；
*   以双下划线“__”打头的函数或方法作为魔法方法，例如 `__call` 和 `__autoload`；

### 常量和配置
*   常量以大写字母和下划线命名，例如 `APP_PATH`和 `THINK_PATH`；
*   配置参数以小写字母和下划线命名，例如 `url_route_on` 和`url_convert`；

### 数据表和字段
*   数据表和字段采用小写加下划线方式命名，并注意字段名不要以下划线开头，例如 `think_user` 表和 `user_name`字段，不建议使用驼峰和中文作为数据表字段命名。

### 网站指示:

[tpframe官网](https://www.tpframe.com)

[tpframe演示网站](http://demo3.tpframe.com/backend)

### QQ群:
`TPFrame 官方交流群`:129822766  

### 特别感谢如下项目的支持
ThinkPHP：(http://www.thinkphp.cn)

Font Awesome：(http://fontawesome.dashgame.com/)

LayUi：(http://layer.layui.com/)

Bootstrap：(http://www.bootcss.com/)

jQuery：(http://jquery.com/)

jsTree：(http://www.jstree.com/)

## 版权信息

TPFrame遵循Apache2开源协议发布，并提供免费使用。

本项目包含的第三方源码和二进制文件之版权信息另行标注。

版权所有Copyright © 2018-2020 by TPFrame (https://www.tpframe.com)

All rights reserved。

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)