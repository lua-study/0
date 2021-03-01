# docker_lnmp_example

This project is about how to build your Docker LNMP environment in Ubuntu 14.04.

+ You should install docker first, please see guide in [https://docs.docker.com/engine/installation/linux/ubuntulinux/](https://docs.docker.com/engine/installation/linux/ubuntulinux/). 
+ After that, you should install docker-compose.

-----
#### Here is some version info: 

+ php:7.0.13-fpm
+ nginx:1.11
+ msql:5.7
+ redis:3.0

-----

You should run ``docker-compose up -d`` in the `project` directory, and the `opt` directory is virtual.

#### Ps:
* ``docker-composer up -d`` will generate the docker instances which the prefix is the parent directory name, eg: project_php_1. **But you can run ``mv ./.env.sample ./.env``, and change the config in .env**

BTW: JUST A NOTE FOR MYSELF


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)