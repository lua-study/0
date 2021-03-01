GetWeixinCode
解决微信OAuth2.0网页授权只能设置一个回调域名的问题

###  **使用方法** 


部署get-weixin-code.html至你的微信授权回调域名的目录下


使用方式类似于直接通过微信回调的方式，只是将回调地址改成了get-weixin-code.html所在的地址，另外省去了response_type参数（因为它只能为code）以及#wechat_redirect（它是固定的），它们会在get-weixin-cod **粗体** e.html里面自己加上


get-weixin-code.html页面从微信那里拿到code之后会重新跳转回redirect_uri里面填写的url，并且在url后面带上code和state


###  **详细示例**
 

前往微信公众平台->接口权限->网页授权获取用户基本信息->修改，填写授权回调页面域名，例如www.abc.com


在www.abc.com域名下部署get-weixin-code.html，不一定是根目录，例如：http://www.abc.com/xxx/get-weixin-code.html


假设你的http://www.xyz.com/hello-world.html这个页面需要获取微信授权，那么你应该使用以下地址来获取授权：http://www.abc.com/xxx/get-weixin-code.html?appid=XXXX&scope=snsapi_base&state=hello-world&redirect_uri=http%3A%2F%2Fwww.xyz.com%2Fhello-world.html


这样最终就会跳转到这样一个地址：http://www.xyz.com/hello-world.html?code=XXXXXXXXXXXXXXXXX&state=hello-world，从而你就拿到了授权code以及自定义的state参数了

### 好项目转载的

欢迎加群交流
   



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)