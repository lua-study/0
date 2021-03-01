![nginx](https://csphere.cn/assets/45169590-0653-4ec5-9a2e-57b4a49fea56)

## 如何使用该镜像

轻量级的HTTP服务 - Nginx,用来展示网页

### 提供静态内容服务
```console
$ image=index.csphere.cn/microimages/nginx
$ docker run --name some-nginx -v /some/content:/app:ro -d $image
```

### 把静态文件存放到当前目录下，并创建一个Dockerfile文件

```Dockerfile
from index.csphere.cn/microimages/nginx
add . /app/
```

"."表示当前目录，add 操作会把当前目录的静态文件拷贝到网站根目录/app/

下面开始build并运行:
```console
$ docker build -t some-content-nginx .
$ docker run --name some-nginx -d some-content-nginx
```

### 导出端口
```console
$ docker run --name some-nginx -d -p 8080:80 some-content-nginx
```

这样就可以在浏览器里打开 `http://host-ip:8080`

### 复杂的配置
```console
$ image=index.csphere.cn/microimages/nginx
$ docker run --name some-nginx -v /some/nginx.conf:/etc/nginx/nginx.conf:ro -d $image
```

有关Nginx配置语法，请参考[Nginx文档](http://wiki.nginx.org/Configuration)。需要特别注意的是配置文件中应包含 `daemon off;` ，让Nginx进程呆在前台。

另外自定义的配置文件也可以放到 `/etc/nginx/conf.d` 目录下。

### nginx结合php-fpm

```console
$ docker pull index.csphere.cn/microimages/php-fpm
$ docker run -d -p 80:80 --name my-php-fpm index.csphere.cn/microimages/php-fpm
$ docker run -d --name my-app --net=container:my-php-fpm index.csphere.cn/microimages/nginx
```

具体的使用，可以参考php-fpm镜像的[使用说明](https://csphere.cn/hub/php-fpm)

## 授权和法律

该镜像由希云制造，未经允许，任何第三方企业和个人，不得重新分发。违者必究。

## 支持和反馈

该镜像由希云为企业客户提供技术支持和保障，任何问题都可以直接反馈到: `docker@csphere.cn`



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)