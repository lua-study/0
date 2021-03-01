#DuxShop功能说明
1、多终端适配，PC+APP+手机网页端+微信公众号+小程序多种购物方式,任意渠道方便用户购买，部分功能后期支持

2、简单易用，采用自主开发php框架与UI设计，给您全新的用户体验

3、简化模板，系统封装了大量通用购物模板，您只需要修改少部分展示类模板即可

4、标签语法，采用dux经典标签语法，只需要三种标签类型即可玩转模板定制

5、易于扩展，系统采用类app模式开发多层多模块任意扩展，采用强大高效的钩子系统，各个模块互不影响即插即用。


#DuxShop版权说明

1、您可以完全遵循本协议的情况下，将本软件用于商业用途，而不必支付软件的使用费用，但我们也不承诺对非商业用户提供任何形式的技术支持与帮助。

2、程序最终版权贵原作者所有，免费使用本程序时需要您在网站底部明显部位注明：powered by duxshop，商业用户不必保留版权信息。

3、您可以免费使用本软件，但是禁止对软件进行改名发布、转卖或出售，禁止以任何形式对DuxSHOP造成利益冲突。

4、您可以对程序进行二次开发，但是二次开发后的软件也禁止公开发布，可以自己分配使用版权参考第四条。

5、如果您使用了DuxSHOP表示您默认了以上协议内容，如有问题请参考以上协议内容。


#安装需求

操作系统：win/mac/linux

运行环境：Apache/Nginx

PHP版本：5.6 ~ 7.x

Mysql版本：5.5+

#Apache伪静态规则

```
Options +FollowSymlinks -Multiviews
RewriteEngine on

RewriteCond %{REQUEST_FILENAME} !-d
RewriteCond %{REQUEST_FILENAME} !-f
RewriteRule ^(.*)$ index.php/$1 [QSA,PT,L]
```


#Nginx伪静态规则

```
location / {
   if (!-e $request_filename) {
   rewrite  ^(.*)$  /index.php/$1  last;
   break;
    }
}
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)