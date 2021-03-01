fastweixin
==========
作者:peiyu 
[我的微博](http://weibo.com/1728407960) 
QQ:125331682 

项目主页:[https://github.com/sd4324530/fastweixin](https://github.com/sd4324530/fastweixin) 
开源中国主页:[http://git.oschina.net/pyinjava/fastweixin](http://git.oschina.net/pyinjava/fastweixin) 
csdn主页:[https://code.csdn.net/sd4324530/fastweixin](https://code.csdn.net/sd4324530/fastweixin) 
#快速搭建微信公众平台服务器 
简单封装了所有与微信服务器交互的消息:文本消息、图片消息、图文消息等等 
提供了基于`springmvc`以及基于`servlet`框架的控制器，集成了微信服务器绑定、监听所有类型消息的方法 
使用时继承，重写即可，十分方便 
v1.2.0开始支持高级接口的API，https请求基于org.apache.httpcomponents 4.3.X，json解析基于fastjson 1.1.44 
框架中提供MenuAPI、MessageAPI、QrcodeAPI、UserAPI用于实现所有高级接口功能，使用极其简单 
内部实现token过期自动刷新，不用再关注token细节 

##基于`springmvc`项目的集成方法
```Java
@RestController
@RequestMapping("/weixin")
public class WeixinController extends WeixinControllerSupport {
        private static final Logger log = LoggerFactory.getLogger(WeixinController.class);
        private static final String TOKEN = "myToken";
        //设置TOKEN，用于绑定微信服务器
        @Override
        protected String getToken() {
            return TOKEN;
        }
        //重写父类方法，处理对应的微信消息
        @Override
        protected BaseMsg handleTextMsg(TextReqMsg msg) {
            String content = msg.getContent();
            log.debug("用户发送到服务器的内容:{}", content);
            return new TextMsg("服务器回复用户消息!");
        }
        /*1.1版本新增，重写父类方法，加入自定义微信消息处理器
         *不是必须的，上面的方法是统一处理所有的文本消息，如果业务觉复杂，上面的会显得比较乱
         *这个机制就是为了应对这种情况，每个MessageHandle就是一个业务，只处理指定的那部分消息
         */
        @Override
        protected List  getMessageHandles() {
                List  handles = new ArrayList ();
                handles.add(new MyMessageHandle());
                return handles;
        }
        //1.1版本新增，重写父类方法，加入自定义微信事件处理器，同上
        @Override
        protected List  getEventHandles() {
                List  handles = new ArrayList ();
                handles.add(new MyEventHandle());
                return handles;
        }
}
```

##基于`servlet`项目的集成方法
```Java
public class WeixinServlet extends WeixinServletSupport {
        private static final Logger log = LoggerFactory.getLogger(WeixinController.class);
        private static final String TOKEN = "myToken";
        //设置TOKEN，用于绑定微信服务器
        @Override
        protected String getToken() {
            return TOKEN;
        }
        //重写父类方法，处理对应的微信消息
        @Override
        protected BaseMsg handleTextMsg(TextReqMsg msg) {
            String content = msg.getContent();
            log.debug("用户发送到服务器的内容:{}", content);
            return new TextMsg("服务器回复用户消息!");
        }
        //1.1版本新增，重写父类方法，加入自定义微信消息处理器
        @Override
        protected List  getMessageHandles() {
            List  handles = new ArrayList ();
            handles.add(new MyMessageHandle());
            return handles;
        }
        //1.1版本新增，重写父类方法，加入自定义微信事件处理器
        @Override
        protected List  getEventHandles() {
            List  handles = new ArrayList ();
            handles.add(new MyEventHandle());
            return handles;
        }
}
```
 
web.xml配置

```xml
 
     weixin 
	 xxx.xxx.WeixinServlet 
 

 
     weixin 
     /weixin 
 
```


Change Log
=========
[https://github.com/sd4324530/fastweixin/wiki/Change-Log](https://github.com/sd4324530/fastweixin/wiki/Change-Log)

Why Use
=========
[https://github.com/sd4324530/fastweixin/wiki/Why-use](https://github.com/sd4324530/fastweixin/wiki/Why-use)

Maven 项目引入
==========
```xml
 
     com.github.sd4324530 
     fastweixin 
     1.2.0 
 
```

开源协议
==========
[Apache License](http://www.apache.org/licenses/LICENSE-2.0)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)