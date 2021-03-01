轻量级的高性能Socket通信库封装，底层基于IOCP完成端口的通讯模型，对象池的应用，轻松应对大规模连接
封装实现了应用层心跳包检测丶Tcp-KeepAlive，可满足一般应用快速开发。
实现了PULL丶PACK模型
PULL模型:仅接收数据
PACK模型:全自动处理分包

使用示例
            ITcpSocketSaeaServerConfiguration serverConfig = new TcpSocketConfiguration();
            //serverConfig.KeepAlive = true;//Tcp-KeepAlive 
            serverConfig.AppKeepAlive = true;//使用应用层心跳包
            serverConfig.PendingConnectionBacklog = options.PendingConnectionBacklog;

            var _server = TcpSocketsFactory.CreateServerAgent(TcpSocketSaeaSessionType.Packet, serverConfig, (notify, session) =>
             {
                 switch (notify)
                 {
                     case TcpSocketCompletionNotify.OnConnected:
                         //session连接
                         break;
                     case TcpSocketCompletionNotify.OnSend:
                         //session发送
                         break;
                     case TcpSocketCompletionNotify.OnDataReceiveing:
                         //session接受数据(如果是PULL模型，数据接受完成)
                         break;
                     case TcpSocketCompletionNotify.OnDataReceived:
                         //如果是PACK模型，整包接受完成
                         break;
                     case TcpSocketCompletionNotify.OnClosed:
                         //session离线
                         break;
                     default:
                         break;
                 }

             });

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)