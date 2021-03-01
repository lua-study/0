使用方法：

首先安装Docker, 有条件的推荐用前两个方式，老设备用Toolbox

 - [Docker for Mac](https://docs.docker.com/docker-for-mac/)
 - [Docker for Windows](https://docs.docker.com/docker-for-windows/)
 - [Docker Toolbox](https://www.docker.com/products/docker-toolbox)

复制项目

    $ git clone https://gitee.com/linwx/Yii2Docker.git

在项目根目录运行

    $ docker-compose up -d

然后打开浏览器，就可以在http://localhost 访问到项目的首页啦, 通过http://localhost:8080 访问phpmyadmin

安装额外的PHP扩展可修改php/Dockerfile，然后再重新build

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)