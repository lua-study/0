## mariadb

> 基于centos镜像构建，关系性数据库mariadb，centos7系统下默认安装的是mariadb

### 如何构建

```
git clone https://git.oschina.net/csphere/mariadb.git
cd mariadb
docker build -t csphere/mariadb:5.5 .
```

### 创建容器

```
docker run -d -p 3306:3306 --name mydb -e DB_USER=myuser -e DB_PASS=mypass --restart=always csphere/mariadb:5.5
```

### 保留容器数据

```
docker run -d -p 3306:3306 --name mydb -e DB_USER=myuser -e DB_PASS=mypass --restart=always -v /db-data:/var/lib/mysql csphere/mariadb:5.5
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)