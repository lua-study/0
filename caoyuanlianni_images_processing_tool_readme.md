# 图片处理工具

#### 介绍
本工具是使用lumen和Intervention Image开发的图片处理工具。

#### 软件架构

* Lumen

```
PHP >= 7.0
OpenSSL PHP Extension
PDO PHP Extension
Mbstring PHP Extension
```

* Intervention Image

```
GD Library (>=2.0)
Imagick PHP extension (>=6.5.7)
```

#### 安装教程

1. 下载代码

```
git clone https://gitee.com/caoyuanlianni/images_processing_tool.git
```

2. composer安装工具

```
composer install
```
3. 复制 .env.example 并重命名为 .env, 给APP_KEY设置一个随机字符串到应用程序密钥（32个字符）。
4. 配置 storage 目录的可写权限。

#### 使用说明

1. 在线获取远程图片并且支持裁剪

```
image/handle?url=图片地址&width=宽度&height=高度&crop=是否裁剪（yes/y是裁剪，其他为不裁剪）
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)