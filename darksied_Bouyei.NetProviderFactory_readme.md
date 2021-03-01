#客户端、服务端连接例子

	int port = 12346;
	//服务端
	INetServerProvider serverSocket = NetServerProvider.CreateProvider();      
	//接收到数据包事件
	serverSocket.ReceiveOffsetHandler = new OnReceiveOffsetHandler((sToken, buff, offset, count) =>
	{
		try
		{
			string info = Encoding.UTF8.GetString(buff, offset, count);
			Console.WriteLine(info);
		}
		catch (Exception ex)
		{
			Console.WriteLine(ex.ToString());
		}
	});
	//接收到客户端连接
	serverSocket.AcceptHandler = new OnAcceptHandler((sToken) =>
	{
		serverSocket.Send(new SegmentOffsetToken()
		{
			sToken = sToken,
			dataSegment = new SegmentOffset()
			{
				buffer = Encoding.Default.GetBytes("welcome" + DateTime.Now.ToString())
			}
		}, false);

		Console.WriteLine("accept" + sToken.TokenIpEndPoint);
	});
	//收到断开连接
	serverSocket.DisconnectedHandler = new OnDisconnectedHandler((stoken) =>
	{
		Console.WriteLine("disconnect" + stoken.TokenId);
	});
	bool isOk = serverSocket.Start(port);
	if (isOk)
	{
		Console.WriteLine("已启动服务。。。");
		//客户端
		INetClientProvider clientSocket = NetClientProvider.CreateProvider();

		//异步连接
		clientSocket.ReceiveOffsetHandler = new OnReceiveOffsetHandler((sToken, buff, offset, count) =>
		{
			try
			{
				Console.WriteLine("rec:" + Encoding.Default.GetString(buff,offset,count));
			}
			catch (Exception ex)
			{

			}
		});
		clientSocket.DisconnectedHandler = new OnDisconnectedHandler((stoken) =>
		{
			Console.WriteLine("clinet discount");
		});
		again:
		bool rt = clientSocket.ConnectTo(port, "127.0.0.1");/* 10.152.0.71*/
		if (rt)
		{
			for (int i = 0; i < 10000; i++)
			{
					Thread.Sleep(50);
				if (i % 100 == 0)
				{
					Console.WriteLine(clientSocket.BufferPoolCount + ":" + i);
				}
				bool isTrue = clientSocket.Send(new SegmentOffset(Encoding.Default.GetBytes("hello"+DateTime.Now)), false);
			}
		}
	}

#协议模块例子

	INetProtocolProvider protocolProvider = NetProtocolProvider.CreateProvider();
	//数据内容打包成字节
	byte[] content = new byte[] { 1, 3, 4, 0xfe, 0x01, 0xfd, 0x02 };
	byte[] buffer= protocolProvider.Encode(new Packet()
	{
		pHeader = new PacketHeader()
		{
			packetAttribute = new PacketAttribute()
			{
				packetCount = 1,//自定义,指定该消息需要分多少个数据包发送才完成
			},
			packetId = 0x10//根据业务自定义
		},
		pPayload = content//携带的数据内容
	});
	//使用接收管理缓冲池解析数据包
	INetPacketProvider pkgProvider = NetPacketProvider.CreateProvider(1024);
	bool rt= pkgProvider.SetBlocks(buffer, 0, buffer.Length);
	rt = pkgProvider.SetBlocks(buffer, 0, buffer.Length);
	var dePkg= pkgProvider.GetBlocks();

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)