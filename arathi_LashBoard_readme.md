# LashBoard

一个基于Laravel和AdminLTE的后台系统框架。

## 一. 简介

### 1. 用户

提供对用户的增删改查等功能。

### 2. 菜单（正在开发）

提供对菜单的增删改等功能。

### 3. 角色

角色相当于用户的分组，一个用户暂时只能拥有一个角色。

### 4. 权限管控（未开发）

对于某个页面没有权限的用户或角色，无法访问这个页面，也无法看到页面对应的菜单项。

## 二. 开发环境部署

### 0. 环境要求

* PHP版本要在5.6.4以上
* 开启Laravel依赖的OpenSSL、PDO、Mbstring、Tokenizer、XML等扩展
* 需要安装Composer

详见[Laravel的安装指南](http://d.laravel-china.org/docs/5.4/installation)与[Composer相关文档](https://pkg.phpcomposer.com/#how-to-install-composer)。

### 1. 下载依赖包

本项目基于Laravel，Laravel使用composer作为包依赖管理工具，因此下载完源码以后还要使用composer下载依赖包到vendor目录下，命令如下：

```bash
composer install
```

### 2. 修改配置文件

根据`.env.example`中的格式，生成一个叫`.env`的文件，参考内容如下：

```bash
APP_ENV=local
APP_KEY=
APP_DEBUG=true
APP_LOG_LEVEL=debug
APP_URL=http://localhost

DB_CONNECTION=sqlite

BROADCAST_DRIVER=log
CACHE_DRIVER=file
SESSION_DRIVER=file
QUEUE_DRIVER=sync
```

为了开发、部署方便，暂时先用sqlite作为数据库，`DB_DATABASE`或者`DB_FILENAME`可以不填，默认放在`database/database.sqlite`。

上面的`APP_KEY`这一项可以先空着，在文件保存后执行以下命令生成`APP_KEY`：

```bash
php artisan key:generate
```

### 3. 建立数据库

在迁移数据库之前，数据库首先要存在，哪怕是空的也可以。然而如果数据库不存在，就要手动创建一个。不同的DBMS创建数据库的方式也不一样，这里只讲一下SQLite。

SQLite的空数据库就是个空文件。使用touch命令创建就行了：

```bash
touch database/database.sqlite
```

### 4. 迁移数据库

Laravel中使用迁移方式来部署数据库，详见[Laravel 的数据库迁移 Migrations](http://d.laravel-china.org/docs/5.4/migrations)。

迁移相关脚本位于`database/migrations`目录下，原则上每次改动要写一个迁移文件。

输入以下命令进行数据库迁移：

```
php artisan migrate
```

### 5. 启动服务

```bash
# 可以按实际需要修改host和port参数的值
php artisan serve --host=127.0.0.1 --port=8000
```

当输出

```
Laravel development server started:  
```

时，服务启动成功，即可使用浏览器访问`http://127.0.0.1:8000/home`。

登陆界面：

![](http://ww1.sinaimg.cn/large/6d8d51f9gy1fdpu6tshb2j20z20ryt9o.jpg)

注册界面：

![](http://ww1.sinaimg.cn/large/6d8d51f9gy1fdpu6ttiktj20z20ry758.jpg)

用户管理界面：

![](http://ww1.sinaimg.cn/large/6d8d51f9gy1fdpu6trw0ej21490ry41a.jpg)



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)