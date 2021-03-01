# virtualphp
## system enviroment
* Linux-Ubuntu16.04
* PHP5.6 (ext:xml,mbstring,gd,mysql,mysqli,pdo)
* Apache2.4 / nginx
* MariaDB 10
* PHP Framework : ThinkPHP 3.2.3
* pure-ftpd
## project config
* this project web root : /home/www/html
* Apache document root : /home/www
* Apache site config root : /etc/apache2/sites-enabled/
* edit /Application/Conf/config.php for your domain and IP and emailServer
## system setting
* change system sudoers
```console
sudo visudo
```
* add content:  `www-data ALL=(ALL) NOPASSWD: /bin/chown, (ALL) NOPASSWD: /bin/mv, (ALL) NOPASSWD: /etc/init.d/apache2`


use your host create a virtual space domain

Demo domain:  v.zuozishu.com 


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)