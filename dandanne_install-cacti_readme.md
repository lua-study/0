## install cacti

### 脚本安装

mysql6 install mysql5.6

exit and login again

download-install-php56w-wgmf.sh 	download and install php56w

install-cacti.sh 	install cacti

install-spine.sh 	install spine

### web方式安装

http://IP/cacti/

- default passwd:
admin/admin

### 添加device 

- 

### 交换机开snmp

```
system-view
[Sysname] snmp-agent sys-info version v2c 
[Sysname] snmp-agent community read public
```

### crotab 

```
* * * * * /usr/bin/php /opt/cacti/poller.php > /dev/null 2>&1
```

### 细节流程

mysql

按照安装脚本来安装
然后再my.cnf修改下面的配置

/etc/my.cnf
max_heap_table_size=500M
innodb_buffer_pool_size=2560M



issue

1 不能连接数据库
默认的配置文件路径

FATAL: Cannot connect to MySQL server on 'localhost'. Please make sure you have specified a valid MySQL database name in 'include/config.php

默认host是localhost
我是把host改成了IP 192.168.18.90解决的
mysql命令行是可以登录的

mysql权限 确认有3个权限
```
GRANT ALL PRIVILEGES ON cacti.* TO 'cacti'@'192.168.%.%' IDENTIFIED BY 'cacti';
GRANT ALL PRIVILEGES ON mysql.time_zone TO 'cacti'@'192.168.%.%' IDENTIFIED BY 'cacti';
GRANT ALL PRIVILEGES ON mysql.time_zone_name TO 'cacti'@'192.168.%.%' IDENTIFIED BY 'cacti';
```

2 /etc/php.ini

date.timezone =  Asia/Shanghai

修改后要重启

service httpd restart

3 日志

```
touch /opt/cacti/log/cacti.log
```

### TODO

交换机端口对应IP地址




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)