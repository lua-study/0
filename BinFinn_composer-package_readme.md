# Compsoer包汇总

## Awsome Package

|名称|用途说明|说明地址|
|---|---|---|
|[mashape/unirest-php](https://packagist.org/packages/mashape/unirest-php)|简单易用的HTTP请求库|[官网](http://unirest.io/)|
|[guzzlehttp/guzzle](https://packagist.org/packages/guzzlehttp/guzzle)|功能强大的HTTP请求库|[文档](http://guzzlephp.org/)|
|[hassankhan/config](https://packagist.org/packages/hassankhan/config)|轻量级配置加载类,支持多种配置格式`PHP, INI, XML, JSON, and YML`||
|[desarrolla2/cache](https://packagist.org/packages/desarrolla2/cache)|简单的缓存类,提供多种缓存驱动`Apc, Apcu, File, Mongo, Memcache, Memcached, Mysql, Mongo, Redis`||
|[phpFastCache/phpFastCache](https://packagist.org/packages/phpFastCache/phpFastCache)|PHP 缓存库,支持apc, memcache, memcached, wincache, files, pdo and mpdo|[官网](http://www.phpfastcache.com/)|
|[hashids/hashids](https://packagist.org/packages/hashids/hashids)|数字ID生成类似优酷视频ID,支持多语言,支持加盐生成|[官网](http://hashids.org/)|
|[sika/sitemap](https://packagist.org/packages/sika/sitemap)|XML网站地图生成器||
|[catfan/medoo](https://packagist.org/packages/catfan/medoo)|简单易用数据库操作类 支持各种常见数据库|[文档](http://medoo.in/doc)|
|[rize/uri-template](https://packagist.org/packages/rize/uri-template)|URL生成||
|[jdorn/sql-formatter](https://packagist.org/packages/jdorn/sql-formatter)|SQL语句格式化 支持语法高亮||
|[intervention/image](https://packagist.org/packages/intervention/image)|图片处理,提供对图片的各种操作:获取图片信息,上传,格式转换,缩放,裁剪等等等|[文档](http://image.intervention.io/)|
|[phpmailer/phpmailer](https://packagist.org/packages/phpmailer/phpmailer)|邮件发送||
|[phpoffice/phpexcel](https://packagist.org/packages/phpoffice/phpexcel)|excel操作类|[文档](https://github.com/PHPOffice/PHPExcel/wiki/User%20Documentation)|
|[league/route](https://packagist.org/packages/league/route)|路由调度|[文档](http://route.thephpleague.com/)|
|[willdurand/jsonp-callback-validator](https://packagist.org/packages/willdurand/jsonp-callback-validator)|JSONP callback参数验证 防止XSS攻击||
|[michelf/php-markdown](https://packagist.org/packages/michelf/php-markdown)|PHP markdown 解析|[官网](https://daringfireball.net/projects/markdown/)|
|[erusev/parsedown](https://packagist.org/packages/erusev/parsedown)|PHP markdown 解析|[演示](http://parsedown.org/tests/) [文档](https://github.com/erusev/parsedown/wiki/)|
|[league/html-to-markdown](https://packagist.org/packages/league/html-to-markdown)|HTML转markdown||
|[monolog/monolog](https://packagist.org/packages/monolog/monolog)|日志操作 composer官方就是用它做例子|[文档](https://github.com/Seldaek/monolog/blob/HEAD/doc/01-usage.md)|
|[phpcollection/phpcollection](https://packagist.org/packages/phpcollection/phpcollection)|PHP 集合操作|[文档](http://jmsyst.com/libs/php-collection)|
|[seld/jsonlint](https://packagist.org/packages/seld/jsonlint)|JSON 语法检查||
|[geoip2/geoip2](https://packagist.org/packages/geoip2/geoip2)|IP地理位置信息||
|[league/csv](https://packagist.org/packages/league/csv)|CSV操作类|[例子](https://github.com/thephpleague/csv/tree/master/examples)|
|[jalle19/php-whitelist-check](https://packagist.org/packages/jalle19/php-whitelist-check)|IP/网址黑白名检查 支持模糊匹配||
|[shark/simple_html_dom](https://packagist.org/packages/shark/simple_html_dom)|php解析html类库|[文档](http://simplehtmldom.sourceforge.net/)|
|[naux/auto-correct](https://packagist.org/packages/naux/auto-correct)|自动给中英文之间加入合理的空格并纠正专用名词大小写||
|[fabpot/goutte](https://packagist.org/packages/fabpot/goutte)|PHP 爬虫库 它提供了一个优雅的 API，这使得从远程页面上选择特定元素变得简单||
|[meenie/munee](https://packagist.org/packages/meenie/munee)|一个集图片尺寸调整、CSS-JS合并/压缩、缓存等功能于一身的PHP库|[官网](http://mun.ee/)|
|[league/flysystem](https://packagist.org/packages/league/flysystem)|一个文件系统抽象层,为各类型文件操作(本地/Azure/Aws/FTP/内存等)提供统一的操作接口|[官网](https://flysystem.thephpleague.com/)|
|[overtrue/wechat](https://packagist.org/packages/overtrue/wechat)|EasyWeChat 是一个开源的 微信 非官方 SDK|[官网](https://www.easywechat.com/)|
|[php-di/php-di](https://packagist.org/packages/php-di/php-di)|PHP 依赖注入容器|[官网](http://php-di.org/) [文档](http://php-di.org/doc/)|
|[jakub-onderka/php-console-color](https://packagist.org/packages/jakub-onderka/php-console-color)|命令行带颜色输出| 没有文档 可以查看github上的[实例代码](https://github.com/JakubOnderka/PHP-Console-Color/blob/master/example.php)|



## 按用途分类

#### 数据库操作库

```
1、数据库操作 (catfan/medoo)
Install：composer require catfan/medoo
Packagist：https://packagist.org/packages/catfan/medoo
```

```
2、ThinkPHP 数据库操作
Install：composer require topthink/think-orm
packagist：https://packagist.org/packages/topthink/think-orm
文档：https://www.kancloud.cn/manual/thinkphp5_1/354004
```

####  HTTP请求库

```
1、HTTP请求库 (guzzlehttp/guzzle)
Install：composer require guzzlehttp/guzzle
Packagist：https://packagist.org/packages/guzzlehttp/guzzle
```

```
2、HTTP请求库 (mashape/unirest-php)
Install：composer require mashape/unirest-php
Packagist：https://packagist.org/packages/mashape/unirest-php
```

#### 邮件发送

```
1、邮件发送 (phpmailer/phpmailer)
Install：composer require phpmailer/phpmailer
Packagist：https://packagist.org/packages/phpmailer/phpmailer
```

#### Word、Excel、PPT、PDF

```
1、Excel操作类（phpoffice/phpexcel） 
Install：composer require phpoffice/phpexcel
Packagist：https://packagist.org/packages/phpoffice/phpexcel
```

```
2、
Install：
Packagist：
```

#### CSV操作类

```
1、CSV操作类 (league/csv)
Install：
Packagist：https://packagist.org/packages/league/csv
例子：https://github.com/thephpleague/csv/tree/master/examples
```

#### 图片处理

```
1、图片处理 (intervention/image)
Install：composer require intervention/image
Packagist：https://packagist.org/packages/intervention/image
```

#### 日志操作

```
1、日志操作 (monolog/monolog)
Install：composer require monolog/monolog
Packagist：https://packagist.org/packages/monolog/monolog
```

#### 时间类

```
1、时间类 (Carbon/Carbon)
Install：composer require nesbot/carbon
Packagist：https://packagist.org/packages/nesbot/carbon
```

#### 模糊匹配（基于Seatgeek）

```
1、模糊匹配 (基于Seatgeek)
Install：composer require wyndow/fuzzywuzzy
Packagist：https://packagist.org/packages/wyndow/fuzzywuzzy
```

#### 提取替换多个关键字（Flashtext）

```
1、提取替换多个关键字 (Flashtext)
Install：composer require shdev/phpflashtext
Packagist：https://flashtext.readthedocs.io/en/latest/api.html
```

#### 数字ID转字符串

```
1、数字ID转字符串 (hashids/hashids)
Install：composer require hashids/hashids
Packagist：https://packagist.org/packages/hashids/hashids
```



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)