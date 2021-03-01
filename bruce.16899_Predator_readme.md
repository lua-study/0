Predator 
=====

Predator 是一款基于基于xhgui改进的图形管理系统，使用方法和xhgui完全一致。主要调整和优化的以下功能：

1、修复原来系统中的BUG。

2、更改bytes为kb或者mb，µs改为ms或者s，日期格式改为年-月-日 时：分：秒。

3、列表项新增IP地址、显示完整访问地址。

4、增加多域名筛选功能，增加登录验证功能（用户名密码请在配置文件中自行配置）

运行环境
===================

Predator运行有以下需求:

 * PHP 版本大于或者等于5.5.
 * 系统支持[XHProf](http://pecl.php.net/package/xhprof),
   [Uprofiler](https://github.com/FriendsOfPHP/uprofiler) or
   [Tideways](https://github.com/tideways/php-profiler-extension) 这几个性能监控组件.
 * [MongoDB PHP 扩展](http://pecl.php.net/package/mongo) 版本必须大于或者等于1.3.0.
 * [MongoDB](http://www.mongodb.org/)版本必须大于或者等于 2.2.0.

安装说明
============

请将文档中__PATH__替换为你项目的实际部署路径。

1. 从Github上克隆Predator项目代码.

2. 服务器根目录指定到 Predator 文件夹下的 webroot目录.

3. 设置 cache 目录权限为 0777。Linux运行如下命令：chmod 0777 cache -R

4. 安装并启动MongoDB（需要自己把config目录下的config.default.php重命名为config.php,配置选项请根据实际情况进行调整。）.

5. 使用db.collection.ensureIndex()命令为MongoDB添加索引.代码示例如下：系统默认使用
predator数据库。代码示例如下：

 ```
   $ mongo
   > use predator
   > db.results.ensureIndex( { 'meta.SERVER.HTTP_HOST' : -1 } )
   > db.results.ensureIndex( { 'meta.SERVER.REQUEST_TIME' : -1 } )
   > db.results.ensureIndex( { 'profile.main().wt' : -1 } )
   > db.results.ensureIndex( { 'profile.main().mu' : -1 } )
   > db.results.ensureIndex( { 'profile.main().cpu' : -1 } )
   > db.results.ensureIndex( { 'meta.url' : 1 } )
   > db.results.ensureIndex( { 'meta.simple_url' : 1 } )
   ```

6. 进入目录后使用php install.php 来安装 composer 来管理系统所需要的扩展。代码示例如下：

   ```bash
   cd __PATH__/
   php install.php
   ```

7. 对Web服务器进行配置。

服务器配置
=============

配置服务器重写规则
----------------------------------

建议使用Rewrite重写规则来进行配置，Apache服务器可以进行如下配置:

1. 允许Apache使用rewrite模块对 URL 进行重写，Apache 2.4 配置示例如下:
    ```apache
     
        Options Indexes FollowSymLinks
        AllowOverride FileInfo
        Require all granted
     
    ```
2. 加载mod_rewrite模块:

    ```apache
    LoadModule rewrite_module libexec/apache2/mod_rewrite.so
    ```

3. 利用项目自带的 `.htaccess`文件对项目进行重写.

Nginx配置示例如下:

```nginx
server {
    listen   80;
    server_name example.com;

    # root directive should be global
    root   __PATH__/webroot/;
    index  index.php;

    location / {
        try_files $uri $uri/ /index.php?$args;
    }

    location ~ \.php$ {
        try_files $uri =404;
        include /etc/nginx/fastcgi_params;
        fastcgi_pass    127.0.0.1:9000;
        fastcgi_index   index.php;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
    }
}
```

配置 Predator 采样率
-------------------------------
修改config/config.php文件中的profiler.enable方法可以自定义采样率（并且可以自定义采集条件）。


```php
// In config/config.php
return array(
    // Other config
    'profiler.enable' => function() {
        $url = $_SERVER['REQUEST_URI'];
        if (strpos($url, '/blog') === 0) {
            return false;
        }
        return rand(1, 100) === 42;
    }
);
```

直接返回true 100%采样。

```php
// In config/config.php
return array(
    // Other config
    'profiler.enable' => function() {
        return true;
    }
);
```

自定义 'Simple' 选项
--------------------------------

你可以修改config/config.php文件中的profiler.simple_url对simple_url进行自定义。


```php
// In config/config.php
return array(
    // Other config
    'profile.simple_url' => function($url) {
        // Your code goes here.
    }
);
```

The URL argument is the `REQUEST_URI` or `argv` value.

使用方法
==============================
在你的应用加载 external/header.php 文件或者在PHP.INI文件中配置[auto_prepend_file](https://secure.php.net/manual/en/ini.core.php#ini.auto-prepend-file)。
 自动加载external/header.php 文件。

Apache服务器配置示例如下：

```apache
 
  php_admin_value auto_prepend_file "__PATH__/external/header.php"
  DocumentRoot "__PATH__/webroot/"
  ServerName site.localhost
 
```
Nginx 服务器配置示例如下：


```nginx
server {
  listen 80;
  server_name site.localhost;
  root __PATH__/webroot/;
  fastcgi_param PHP_VALUE "auto_prepend_file=__PATH__/external/header.php";
}
```

命令行模式的使用方法
====================

最简单的使用方法就是在项目中加载`external/header.php`文件:

```php
  use predator
> db.results.ensureIndex( { "meta.request_ts" : 1 }, { expireAfterSeconds : 432000 } )
```

使用 Tideways 扩展（推荐）
========================

该扩展支持PHP7+版本，具体详情请查看 [tideways extension](https://github.com/tideways/php-profiler-extension).

安装好扩展后，你可以参考以下代码修改PHP配置文件


```ini
[tideways]
extension="/path/to/tideways/tideways.so"
tideways.connection=unix:///usr/local/var/run/tidewaysd.sock
tideways.load_library=0
tideways.auto_prepend_library=0
tideways.auto_start=0
tideways.sample_rate=100
```

发布和更新
====================

你可以到这里查看有关 [Predator](https://github.com/Longjianghu/Predator) 的发布和更新信息

其它说明
=======

欢迎任何企业或者个人使用 Predator，如果你在使用过程中遇到任何问题请到 [这里](https://github.com/Longjianghu/Predator/issues) 提交，非常感谢！


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)