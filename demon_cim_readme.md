#前言：

   现在市面上有很多 xmpp协议的即时通讯方案，openfire androidpn，等等。它们都是使用了apache mina开发，但是这些东西基本都需要二次改造开发。而且改动还很大，我也看过这些东西的源码，发现代码结构不太理想，耦合的情况太多，实在不好扩展。所谓XMPP 协议。只不过是别人使用mina 自定义了一个消息编码解码协议。通俗的讲就是，xml形式消息的编码与解码，我们完全没有必要在国外这套不成熟的openfire 与xmpp 上耗费过多的精力去研究，我们完全可以通过apache mina 自定义自己的通讯协议，并可以为它使用自己的名字。我们不要盲目崇拜国外的有些东西，自己掌握原理，才是最重要的，各位切记~

   这套IM系统为我个人自主开发 使用了 apache mina ，主要功能为 服务端和客户端，客户端 到客户端的即时通信，可以支持包括文字 图片，语音等任何消息形式 服务端使用的 struts2+spring3和 apache mina android端 也使用的apache mina。这套IM系统结构还是非常清晰合理的，非常容易扩展和改造，下面是android版本 的 demo的目的是只是一个演示 ，可以参照它的代码，使用这套系统开发自己的东西，核心价值是一套高灵活性，相对标准化的即时通讯解决方案，即时聊天只是它的一种运用途径！


#成功案例
#http://www.eoeandroid.com/thread-300586-1-1.html
 
　　 
##在需要接受消息的activity里面实现OnCIMMessageListener接口。 实现选择性实现以下方法，当收到服务端消息时回调

```java
public void onReplyReceived(ReplyBody reply)
{
　  System.out.print("收到服务端的响应");
}
public void onMessageReceived(Message msg)
{
　  System.out.print(" 收到服务端的消息:"+msg.getContent();
}
public void onSentSuccessful(SentBody arg0)
{
　　System.out.print("发送请求成功");
}
public void onSentFailed(Exception e, SentBody sent)
{
　　System.out.print("向服务端发送请求失败");
}
public void onConnectionClosed()
{
　 System.out.print("与服务端连接断开!");
}
public void onConnectionFailed(Exception arg0)
{
　 System.out.print("连接服务端失败!");
}
public void onConnectionSuccessful()
{
　 System.out.print("连接服务端成功!");
}
 
public   void onNetworkChanged(NetworkInfo info
{
      if(info ==null)//手机网络连接断开
	 System.out.print("手机网络连接断开!");		
}
``` 
 
#CIM请求的发送，和接收服务端响应. LoginActivity为例 登陆时发送登陆请求
```java
　　private void doLogin()
　　{
	　　SentBody sent = new SentBody();
	　　sent.setKey(CIMConstant.Request Key.CLIENT_AUTH);
	　　sent.put("account", accountEdit.getText().toString().trim());
	　　sent.put("password", passwordEdit.getText().toString().trim());
	　　sent.put("channel", "android");
	　　CIMConnectorManager.getManager(this).send(sent);
　　}
　　 
　　 
　　//收到服务端登录请求响应后，进入onReplyReceived
　　public void onReplyReceived(ReplyBody reply)
　　{
	　　System.out.print("收到请求的响应");
	　　if(reply.getKey().equals(CIMConstant.RequestKey.CLIENT_AUTH       
	　　{
	　　if(reply.getCode().equals(CIMConstant.ReturnCode.CODE_200))
	　　   System.out.print("登陆成功");
	　　if(reply.getCode().equals(CIMConstant.ReturnCode.CODE_403))
	　　  System.out.print("登陆失败，用户名或者密码错误");
	　　}
　　}
```


##客户端接收消息
![image](http://staticres.oss-cn-hangzhou.aliyuncs.com/cim-android_client.png)

##服务端消息 web入口
![image](http://staticres.oss-cn-hangzhou.aliyuncs.com/cim-server.png)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)