
## 项目概述

* 产品名称：澳洲摄影与绘画
* 项目代号：sheying





## 功能如下


## 运行环境要求

- Nginx 1.8+
- PHP 7.0+
- Mysql 5.7+
- imagick 以及扩展


## 开发环境部署/安装

本项目代码使用 PHP 框架 [Laravel 5.5](https://d.laravel-china.org/docs/5.5/) 开发，

下文将在假定读者已经安装好了 Homestead 的情况下进行说明。如果您还未安装 Homestead，可以参照 [Homestead 安装与设置](https://laravel-china.org/docs/5.5/homestead#installation-and-setup) 进行安装配置。

### 基础安装

#### 1. 克隆源代码



#### 2. 配置本地的 Homestead 环境

1). 运行以下命令编辑 Homestead.yaml 文件：



2). 加入对应修改，如下所示：



3). 应用修改

修改完成后保存，然后执行以下命令应用配置信息修改：



随后请运行 `homestead reload` 进行重启。

#### 3. 安装扩展包依赖

	composer install

#### 4. 生成配置文件

```
cp .env.example .env
```

你可以根据情况修改 `.env` 文件里的内容，如数据库连接、缓存、邮件设置等：

```
APP_NAME=摄影艺术
APP_ENV=local
APP_KEY=base64:IMFAyGoSeEzugSOj3N+qqwCGSM9D0aFeRshiuiGRRqQ=
APP_DEBUG=true
APP_LOG_LEVEL=debug
APP_URL=http://xu.sheying.com:9003
DEBUGBAR_ENABLED=true
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=sheying
DB_USERNAME=root
DB_PASSWORD=root

BROADCAST_DRIVER=log
CACHE_DRIVER=file
SESSION_DRIVER=file
QUEUE_DRIVER=sync

REDIS_HOST=127.0.0.1
REDIS_PASSWORD=null
REDIS_PORT=6379

MAIL_DRIVER=smtp
MAIL_HOST=smtp.163.com
MAIL_PORT=25
MAIL_USERNAME=15036158397@163.com
MAIL_PASSWORD=love8269464
MAIL_ENCRYPTION=null
MAIL_FROM_ADDRESS=15036158397@163.com
MAIL_FROM_NAME=摄影艺术

PUSHER_APP_ID=
PUSHER_APP_KEY=
PUSHER_APP_SECRET=

```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)