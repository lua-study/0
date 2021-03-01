# Laravel5.5 with Auth

1. `composer install`
1. `php artisan key:generate`
1. 修改 `config/app.php` 的 timezone 为 `Asia/Shanghai`
1. `php artisan storage:link` `http://laravel.with.auth/storage/***` 访问路径
1. `cd publicd/storage && mkdir unlimit-code && sudo chown www:www -R unlimit-code`
1. 上线前 `php artisan route:cache && php artisan config:cache && composer dump-autoload -o`
1. 上线前修改 `.env` `APP_ENV=production`

## 每次更新线上代码
1. `php artisan route:cache` 如果修改了路由
1. `php artisan config:cache` 如果修改了配置项
1. 更新php的缓存。

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)