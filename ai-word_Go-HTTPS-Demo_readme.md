#Go HTTPS Demo

1. 生成https证书，运行 go run gen.go
	* ca.key,ca.pem 自定义 CA证书
	* server.key,server.pem 自定义CA证书 签名的服务端证书
	* client.key,client.pem 自定义CA证书 签名的客户端证书
	
2. 运行服务端程序  go run ser.go

3. 运行客户端程序  go run client.go

参考资料  
1. http://tonybai.com/2015/04/30/go-and-https/  
2. https://github.com/nareix/blog/blob/master/posts/golang-tls-guide.md  


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)