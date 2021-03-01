# dockerPHP

#### 介绍
dockerPHP开发环境，包含Redis，PHP7.2，不包括MySQL，composer

#### 目录结构
```
/
├── conf                        配置文件目录
│   ├── conf.d                  Nginx用户站点配置目录
│   ├── nginx.conf              Nginx默认配置文件
│   ├── php-fpm.conf            PHP-FPM配置文件（部分会覆盖php.ini配置）
│   └── php.ini                 PHP默认配置文件
├── Dockerfile                  PHP镜像构建文件
├── extensions                  PHP扩展源码包
├── log                         日志目录
├── docker-compose-sample.yml   Docker 服务配置示例文件
├── env.smaple                  环境配置示例文件
└── www                         PHP代码目录
```


#### 安装教程
1. 本地安装`git`、`docker`和`docker-compose`(**需要1.7.0及以上版本**)。
2. `clone`项目：
    ```
    $ https://gitee.com/Colorado/dockerPHP.git
    ```
3. 如果不是`root`用户，还需将当前用户加入`docker`用户组：
    ```
    $ sudo gpasswd -a ${USER} docker
    ```
4. 拷贝并命名配置文件（Windows系统请用copy命令），启动：
    ```
    $ cd dockerPHP
    $ cp env.sample .env
    $ cp docker-compose-sample.yml docker-compose.yml
    $ docker-compose up
    ```
    注意：Windows安装360安全卫士的同学，请先将其退出，不然安装过程中可能Docker创建账号过程可能被拦截，导致启动时文件共享失败；
5. 访问在浏览器中访问：

```

 - [http://localhost](http://localhost)： 默认*http*站点
 - [https://localhost](https://localhost)：自定义证书*https*站点，访问时浏览器会有安全提示，忽略提示访问即可

两个站点使用同一PHP代码：`./www/localhost/index.php`。

```

6.添加自定义项目：
    
```
    1. 复制项目目录到 dockerPHP/www里，如dockerPHP/www/laravel
    2. 添加NGINX配置文件 dockerPHP/conf/conf.d里复制一份配置文件进行配置
    3. 添加host，如：127.0.0.1 www.laravel.com
    4. 访问域名
```




#### 其他说明
    没有composer，使用宿主机的composer  
    木有mysql，使用自己的数据库

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)