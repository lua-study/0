# 基于Spring Security OAuth2的微信网页登录

研究spring Security有一段时间，放假无聊写了这个小project。

现在做项目，都需要用户认证、授权的，必需但又挺烦的一个功能。现在大家都玩微信，直接使用微信的账号登录就行了。结合Spring Security oauth2也挺容易实现的。

### 根据微信的开发文档，微信网页登录是基于oauth2协议的，但做这个项目的时候，遇到一些不同的地方，如下：
1、oauth2协议中的client_id和client_secret，在微信中是appid与secret； 
2、访问微信的api时，返回的数据是json，但content-type是text/plain，spring的默认的messageConverter是不会转换text/plain的数据为对象map，从而导致不能获取api的返回数据。我的解决方法，增加了一个MappingJackson2HttpMessageConverter，重写mediaTypes，使它处理text/plain的数据。 
3、根据微信的api文档，重定向的url的最后，必需加@wechat_redirect，spring security oauth2的默认处理是没有的。但实际情况是，没有这个也是可以的，但考虑到我是用公众号的测试号开发的，可以正式环境需要，我改了。 
4、微信网页授权的api的方法是Get，spring security oauth2是post，是改。

### 本项目是根据spring的官方教程改写而成，不破坏原教程的情况下，只是重写了部分类的方法，从而实现上面的不同点。
	原官方教程地址：
	https://spring.io/guides/tutorials/spring-boot-oauth2/

设断点分析oauth2的整个流程，才知道上面那些不同点要在哪里改，非常痛苦。真不明白微信既然基于oauth2，但又弄这些不一样的地方是为啥。

此项目可以轻松移植到其它需要使用微信网页登录的项目，当然，前提你要熟悉spring security。

### 要正常运行、测试本项目，你需要准备下面几项目东西：
1、微信公众号的测试号。 
2、在测试号的管理界面上，设置回调域名，这里你随便设，测试用，不带http或https。 
3、修改C:\Windows\System32\drivers\etc\hosts文件，增加一个静态路由，域名就是你刚才设置的域名，指向127.0.0.1，如www.abc.com 127.0.0.1，这样就可以本地测试第三方登录，其实其它的第三方登录如QQ、微博，都是这样，我是不建议使用软件实现，何必呢。 
4、使用微信开发者工具，浏览测试。因为公众号的微信网页授权，只能在微信浏览器访问的，而微信开发者工具实则就是一个微信浏览器。 
5、app微信登录、网页登录申请太麻烦了，要上传太多资料，我就用公众号测试的，基本原理都一样。 

### Over!
### Good luck.

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)