#LinuxSocketServer

## 1. 概述
本项目主要是使用Socket实现一个多客户端服务器。服务器提供手机端和PC端的APP进行访问，上传文件
最终控制3D打印机进行打印

## 2. 主要结构
QTcpServer类，QThread类.
使用QSocketNotifier时，防止丢数据，需要注意
1、Disable the notifier. 在接受数据时执行
2、Read data from the socket. QSocketNotifier提供了一个socket()函数，返回socket描述符。
    通过这个描述符，可以创建一个关联的socket
3、Re-enable the notifier if you are interested in more data。在接收完数据之后，重新开启监听的事件




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)