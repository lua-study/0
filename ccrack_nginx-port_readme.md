#nginx-port
##说明
* nginx的配置文件，功能是将 http://12345.test.com 的访问转换为内网 http://127.0.0.1:12345 的访问。
* 端口号跟随域名变化。

##使用
* 绑定的域名修改配置文件nginx.conf 中的此行：  server_name *.test.com;
* 可以申请免费域名或者直接在host文件中进行配置访问。

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)