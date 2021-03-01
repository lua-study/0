dubboplus 
aruanruan@vip.sina.com/阿阮
qq:33224696

1.本项目目标是对dubbo进行扩展，使得移动端和服务端可以相同
的方式访问dubbo提供的服务
2.提供多种语言客户端访问dubbo，包括常见的php,android,ios等
3.由于对外网提供的服务，因此对dubbo协议进行相应的扩展，提供
相应的安全机制

具体已经(部分)提供的扩展有：
1.com.alibaba.dubbo.remoting.Interceptor
提供服务端的服务拦截，对客户端请求进行拦截处理，dubbo over netty4,和dubbo over http已经提供的相应的处理，这里用来实现
类似黑白名单，信息校验等
2.com.alibaba.dubbo.remoting.MessageEncode/MessageDecode提供对数据
的加解密处理
3.提供了类似http协议的header机制，用户可以自定义各种字符串的K-V值
4.com.alibaba.dubbo.common.configure.ExtensionConfigurator用来提供
各种SPI等的配置扩展

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)