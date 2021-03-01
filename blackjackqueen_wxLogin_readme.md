# wx

#### 项目介绍
微信登陆后端 composer 包

#### 安装教程

```
composer install wx-login/wx-login
```

#### 使用说明

```
use wxLogin/Login;

$wx = new Login($appid, $app_secret);

// 自己验证$getData数据是否存在
$getData = $_GET;

// 登陆
$user = $wx->run($getData);

// todo 保存数据库

*备注* 返回到前端数据的时候别忘了删除 $user['session_key']，这是让你保存到数据库用的。$user['skey'] 是自定义加密串，
使用 wxLogin/Tool::tool_encrypt($user['session_key']); 而来。解密请用 wxLogin/Tool::tool_decrypt($user['skey']);
```



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)