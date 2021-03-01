# cocos creater斗地主

1. 客户端cocos creater 使用typescript

2. 服务端easyswoole+mysql

# 启动说明
    
    1. 因为服务端也客户端都丢在一个项目中了，所望共用了一个gitignore。所以在服务端的根目录要手动创建两个文件夹，不然报错 Temp Log

    2. 服务端启动 在服务端目录下 php easyswoole start --d (要安装Swoole扩展)

    3. 客户端中的QM.js(Ts)中，写了连接服务器的ip。可以修改源码编译，也可以直接改QM.js

# 界面说明

    1. 没有素材，所以界面超级难看。
    
    2. 没有做客户端的断线重连(懒)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)