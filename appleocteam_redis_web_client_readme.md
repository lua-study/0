## redis admin
### 安装
#### 环境 python 2.7

```
mkdir -p /data/wwwroot/ && cd /data/wwwroot
git clone https://gitee.com/careyjike_173/redis_web_client.git redis_admin
cd redis_admin && pip install -r requirements.txt
```

### 配置

```
$ vim conf/conf.py
DEBUG = True  //debug模式

LOG_LEVEL = 'INFO'  //日志级别

// 邮件信息
mail_host = 'smtp.exmail.qq.com'
mail_user = 'test@test.com'
mail_pass = 'xxx'
mail_receivers = ["test@test.com", "test2@test.com"]

// 数据库信息
database = {
    "name": "redis_admin",
    "host": "127.0.0.1",
    "username": "root",
    "password": "root",
    "port": "3306",
}
```

  
### nginx
安装nginx, 使用我的另一个开源安装脚本安装nginx

```
git clone https://gitee.com/careyjike_173/script.git
cd script && ./installl
// 根据提示安装nginx
```
配置nginx

```
  server {
  listen 80;
  server_name _;
  access_log /data/wwwlogs/access_nginx.log combined;
  index index.html index.htm index.php;
  location / {
    proxy_pass http://127.0.0.1:8000;
  }
  location /static {
                expires 7d;
                autoindex on;
                add_header Cache-Control provate;
                alias /data/wwwroot/redis_admin/static;
        }
  }
```

### 启动
启动 `redis_admin`

```
chmod +x start.sh
./start.sh start
```
启动`nginx`

```
service nginx start
```

使用`python manage.py createsuperuser` 创建用户  
**访问浏览器 http://ip/** 

![](https://gitee.com/careyjike_173/redis_web_client/raw/master/static/img/1.png)


![](https://gitee.com/careyjike_173/redis_web_client/raw/master/static/img/2.png)

![](https://gitee.com/careyjike_173/redis_web_client/raw/master/static/img/3.png)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)