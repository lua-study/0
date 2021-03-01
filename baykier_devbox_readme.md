devbox
======

    devbox 是基于docker的开发环境封装项目，用于简化开发的环境搭建和迁移 如果喜欢欢迎star

### 如何简化开发环境

    对于开发来说，需要用到的工具包，软件包，有可能非常非常多，而且经常出现冲突，docker的出现对于解决这个问题提
    供的非常好的途径，并且还能保持系统的干净，清洁。对于单个的开发测试，封装在同一个环境，能有效解决依赖冲突

### 如何解决容器内外的权限问题

    各个容器内的服务，如nginx 或者php-fpm，都是以用户角色运行，如果对于线上环境，我们可以把源码包直接 打入镜像内
    部来避免权限问题。但是对于开发环境，还是挂载到容器内部最为实用，这时候，假如开发目录和容器内部运行服务的用户
    不一致，就会出现权限问题，为了解决这个问题，我们有两种方法可以解决:
    
   - gosu root
   
    这种方法就是容器内服务运行时候用[gosu](https://github.com/tianon/gosu)命令启用,只不过这里我们用gosu root启用，
    下面以php 5.6 的Dockerfile为例:
   
   ```
        ENV GOSU_VERSION 1.10
        RUN set -x \
        	&& apk add --no-cache --virtual .gosu-deps \
        		                                dpkg \
        		                                gnupg \
        		                                openssl \
        	&& dpkgArch="$(dpkg --print-architecture | awk -F- '{ print $NF }')"  \
        	&& wget -O /usr/local/bin/gosu "https://github.com/tianon/gosu/releases/download/$GOSU_VERSION/gosu-$dpkgArch"  \
        	&& wget -O /usr/local/bin/gosu.asc "https://github.com/tianon/gosu/releases/download/$GOSU_VERSION/gosu-$dpkgArch.asc" \
        	&& chmod +x /usr/local/bin/gosu \
            # verify that the binary works
        	&& gosu nobody true \
        	&& apk del .gosu-deps
        
        ENTRYPOINT gosu root php-fpm
   
   ```
   > 这样 php-fpm就会以root运行，避免挂载的目录权限不足问题，切记生产环境慎用
   
   - 修改UID和GID
   
    这种方法，就是容器启动时候将容器内服务的用户UID和GID改成同开发者的主机用户UID和GID一致，来避免权限不足的问题
    我们以nginx Dcoekrfile 为例:
    

        ## 将nginx uid gid 更新为开发环境用户ID
        RUN set -x \
        && usermod -u ${DEVBOX_UID} nginx \
        && groupmod -g ${DEVBOX_GID} nginx

   
   以上里两种方法均可
    
   
###  所需要的依赖环境

- docker
- docker-compose
- git

> 对于win10之前的可能需要安装vagrant来搭建
   

### 整体架构说明

```
devbox
  |--- bin                   可执行命令脚本
  |--- build                 各个项目Docker镜像构建目录，可根据需要自行修改，添加
  |    |--- nginx            Nginx Build目录
  |    |--- mongo            MogonDb Build目录
  |    |--- mysql            MysqlDb Build目录
  |    |--- php              Php Build目录
  |--- conf                  容器运行时挂着各项目配置目录 
  |--- data                  MongoDb 或MysqlDb数据文件
  |--- log                   各个容器内部日志文件，例如Nginx 或Php
  |--- plugins               需要用到的一些扩展
  |--- project               项目目录
  |--- .env.example          Docker-Compose的环境变量配置文件demo
  |--- .gitignore            
  |--- docker-compose.yml    Docker-Compose的配置文件
  |--- README.md
  |--- Vagrantfile.exmaple   Vgrantfile 参考Demo文件

```
### 如何使用

使用很简单，根据需要，复制docker-compose.yml.example为docker-compose.yml,.env.example为.env,修改.env里面的配置后
执行下面命令:

```
docker-compose up [-d]  

```

将 devbox/bin 目录链接到~/bin 目录

rm -fr ~/bin && sudo ln -s /pathro/devbox/bin /home/user/bin

这样可以直接用bin目录提供的php和composer命令了

### License

MIT   License

相关资源
--------

* [docker](https://www.docker.com/)

* [docker仓库](https://hub.docker.com/explore/)

* [git](https://git-scm.com/)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)