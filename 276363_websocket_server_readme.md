1. 创建.env文件
```
host=http://localhost #websocket访问网址
port=8080                #node运行端口   
redis_host=192.168.10.10 #redis地址，一般为localhost
redis_post=6379          #redis运行端口
channel=order            #redis订阅的频道
```
2. npm run serv
3. 将host反向代理到nginx
4. 使用socket.io客户端连接
```
socket = io('http://localhost');
socket.on('news', (data) => {
    console.log(data);
});
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)