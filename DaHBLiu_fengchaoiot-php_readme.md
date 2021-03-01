# 蜂巢物联php-sdk

#### 描述
针对蜂巢物联的功能的API封装。不保证使用

#### 安装
`composer require da-hong/fengchaoiot-php`
#### 使用
A. token申请
```php
use FengChaoIOT\Auth\FengChaoIOTAuth as Auth;
$auth = new Auth('id','scr');
$response = $auth();
$token = $response['data']['accessToken'];
```
B. 门锁使用

```php
new $Devices
```
3. 门禁卡使用
```php
$cards = new Cards()
//写卡
$cards->make();
//读卡
$cards->read();
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)