#SuperSocketChat
### 说明
此程序使用 SuperSocket [SuperSocket](http://www.supersocket.net)。是一个简单的聊天室例子。服务器通过配置文件启动，使用了江大的 SuperSocket.SocketService.exe 来启动程序（或安装为服务）。

###目前实现了基础的服务器功能
- 加入聊天室
- 一对一发消息
- 群发消息
- 退出聊天室

这些功能目前支持通过 telnet 使用。

### 使用说明
下面以本机测试 localhost 为例
程序默认端口是 >9527
在cmd 中，输入
```
telnet localhost 9527
```
登录成功后，输入
```
JOIN MyNickName
```
以加入聊天。
成功加入后，服务器会返回当前在线的用户昵称列表，输入
```
ONE2ALL MyMessage
```
向所有在线的用户发送消息，输入
```
ONE2ONE toNickName MyMesage
```
向指定用户名的用户发送消息。

若要退出聊天，输入
```
QUIT
```
就可以结束了。

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)