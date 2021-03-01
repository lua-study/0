### 依赖

1. laravel 5.5.* [官网](https://laravel.com/)|[文档](http://https://laravel.com/docs/5.5)
2. laravel-admin 1.5.* [官网](http://laravel-admin.org)|[文档](http://laravel-admin.org/docs/#/)
3. curl/curl 1.8.* [官网](https://github.com/php-mod/curl)|[文档](https://packagist.org/packages/curl/curl)

### 安装   

```
$ git clone **** admin
$ cd admin
$ cp .env.example .env # *配置数据库链接信息*
$ composer install
$ php artisan key:generate
$ php artisan migrate --seed
```
### 使用示例   
1. [CURL 使用示例](./docs/curl_example.md)    


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)