# WebServer

#### 项目介绍
  .C++实现的简易Web服务器   
  目前实现了GET方法,网页文件目录可以修改src/include/Global.h中的FILEPATH，修改完再次编译即可生效


#### 运行无LOG版本
```
1. git clone https://gitee.com/chendilin/WebServer.git
2. cd Webserver
3. sudo mkdir -p /srv/Girl/www
4. sudo cp -rf www/* /srv/Gril/www
5. make
6. ./WebServer
7. 浏览器输入 localhost:8888即可看到index.html内容
```
#### 运行带LOG输出版本:
```
1. make debug
2. ./debug
```

#### 运行gdb调试版本:
```
1. make debuggdb
2. gdb ./debuggdb
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)