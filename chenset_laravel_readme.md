### required

- 80 port for nginx
- 3306 port for mysql
- directory /data/youbao 

### Docker
```
cd /data/youbao/docker
docker-compose build
docker-compose up -d
sh ./init.sh
```

### mysql create database https://dev.mysql.com/doc/refman/8.0/en/charset-database.html
```
# via docker
docker exec -it mysql mysql -p11111111 -e"CREATE DATABASE IF NOT EXISTS laravel CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci"

# sql
CREATE DATABASE IF NOT EXISTS laravel CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci;
```



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)