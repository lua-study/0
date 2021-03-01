 **一:RestApi接口增加JWT认证功能**  
用户填入用户名密码后，与数据库里存储的用户信息进行比对，如果通过，则认证成功。传统的方法是在认证通过后，创建sesstion，并给客户端返回cookie。
现在我们采用JWT来处理用户名密码的认证。区别在于，认证通过后，服务器生成一个token，将token返回给客户端，客户端以后的所有请求都需要在http头中指定该token。
服务器接收的请求后，会对token的合法性进行验证。验证的内容包括：

内容是一个正确的JWT格式

检查签名

检查claims

检查权限

处理登录

创建一个类JWTLoginFilter，核心功能是在验证用户名密码正确后，生成一个token，并将token返回给客户端：

该类继承自UsernamePasswordAuthenticationFilter，重写了其中的2个方法：

attemptAuthentication ：接收并解析用户凭证。

successfulAuthentication ：用户成功登录后，这个方法会被调用，我们在这个方法里生成token。


 **二:授权验证** 

用户一旦登录成功后，会拿到token，后续的请求都会带着这个token，服务端会验证token的合法性。

创建JwtAuthenticationFilter类，我们在这个类中实现token的校验功能。

该类继承自BasicAuthenticationFilter，在doFilterInternal方法中，从http头的Authorization 项读取token数据，然后用Jwts包提供的方法校验token的合法性。
如果校验通过，就认为这是一个取得授权的合法请求。


 **三:SpringSecurity配置** 

通过SpringSecurity的配置，将上面的方法组合在一起。

这是标准的SpringSecurity配置内容，就不在详细说明。注意其中的


.addFilter(new JWTLoginFilter(authenticationManager()))
.addFilter(new JwtAuthenticationFilter(authenticationManager()))

这两行，将我们定义的JWT方法加入SpringSecurity的处理流程中。


 **四:简单测试** 
下面对我们的程序进行简单的验证： 
1.请求获取用户列表接口:http://localhost:8080/users/userList接口，会收到403错误 
{
    "timestamp": 1518333248079,
    "status": 403,
    "error": "Forbidden",
    "message": "Access Denied",
    "path": "http://localhost:8080/users/userList"
}
curl http://localhost:8080/users/userList 
原因就是因为这个url没有授权,所以返回403 
![输入图片说明](https://gitee.com/uploads/images/2018/0211/154022_8d9806ae_130820.png "jwt-1.png")


2.注册一个新用户 
curl -H "Content-Type: application/json" -X POST -d '{ 
    "username": "admin", 
    "password": "password" 
}' http://localhost:8080/users/signup 
![输入图片说明](https://gitee.com/uploads/images/2018/0211/154042_74fb2aa6_130820.png "jwt-2.png")


3.登录，会返回token，在http header中，Authorization: Bearer 后面的部分就是token 
curl -i -H "Content-Type: application/json" -X POST -d '{ 
    "username": "admin", 
    "password": "password" 
}' http://localhost:8080/login 
温馨提醒:这里的login方法是spring specurity框架提供的默认登录url
![输入图片说明](https://gitee.com/uploads/images/2018/0211/154308_9576ce90_130820.png "jwt-3.png")


4.用登录成功后拿到的token再次请求/users/userList接口 
 4.1将请求中的XXXXXX替换成拿到的token 
 4.2这次可以成功调用接口了 
curl -H "Content-Type: application/json" 
-H "Authorization: Bearer XXXXXX" 
"http://localhost:8080/users/userList"
![输入图片说明](https://gitee.com/uploads/images/2018/0211/154315_241cd6b2_130820.png "jwt-4.png")

5.设置了1分钟后Token过期，如果1分钟后再次请求/users/userList接口返回Token过期的异常提示如下图: 
![输入图片说明](https://gitee.com/uploads/images/2018/0411/231525_74189dfe_130820.png "Token过期.png")

 **五：建议及改进**  
若您有任何建议，可以通过1）加入qq群715224124向群主提出，或2）发送邮件至827358369@qq.com向我反馈。本人承诺，任何 
建议都将会被认真考虑，优秀的建议将会被采用，但不保证一定会在当前版本中实现。 
扫码加群，一起交流： 
![输入图片说明](https://images.gitee.com/uploads/images/2018/0713/090805_8a9588f2_130820.jpeg "QQ群图片.jpg")

六：集成Swagger-ui，方便前后端分离开发，默认访问地址：http://localhost:8080/swagger-ui.html  
![输入图片说明](https://gitee.com/uploads/images/2018/0606/144813_c5dfeec8_130820.png "1.png")
![输入图片说明](https://gitee.com/uploads/images/2018/0606/144822_b3698637_130820.png "22.png")
![输入图片说明](https://gitee.com/uploads/images/2018/0606/144830_d28eda7f_130820.png "2.png")
温馨提示：这里的登录接口还是使用的默认地址，如果你的token过期了，需要你重新登录生成新的token. 

七：微信号  
![输入图片说明](https://images.gitee.com/uploads/images/2018/1106/120321_db93bba7_130820.jpeg "个人微信.jpg")







 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)