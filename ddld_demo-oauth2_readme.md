# Demo-oauth2

Spring Cloud OAuth2 自定义授权类型实现其他方式登录(短信验证码登录、手机号密码登录)，令牌申请实现定制返回体。

##  实现效果：

使用手机号密码进行授权:

![pwd](./data/pwd.png)

使用手机号短信验证码进行授权：
![sms](./data/sms.png)

通过访问令牌获取当前用户细节：

![current-info](./data/current-info.png)

##  说明：

通过继承`AbstractCustomTokenGranter`抽象令牌授予者类实现`getUserDetails`方法获取需要的参数并调用`CustomUserDetailsService`用户细节服务的方法认证获取用户细节数据。

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)