# 東木书屋
使用 追书神器 的API进行采集，每个浏览的用户都可以自行采集小说到服务器，减少管理员的工作。

基本可以使用了。

# DEMO

做了一个DEMO站点，请大家不要暴力...
http://218.23.64.132:3535
管理员：admin
密码：1234

# 安装要求

1. php 7.1以上版本，最好是7.2
2. php-curl php-zip 模块

# 安装方法

1. 将下列目录修改可写。
    创建未上传的3个目录
    ```
    mkdir assets/sessions 
    mkdir assets/uploads
    mkdir Logs
    ```
    修改目录所有者
    ```
    sudo chown www-data:www-data assets/cache assets/sessions \
    assets/uploads assets/images/covers assets/images/avatar Logs -R
    ```

2. 创建并导入数据库
    ```
    mysql -u root -p
    create database novel;
    use novel;
    source novel.sql;
    ```
    
3. 修改配置文件
    1. 修改Config\Config.php
    ```
    $config['title'] = '東木书屋';
    $config['baseUrl'] = '/DMNovel';
    ```
    
    2. 修改Config\Database.php
    ```
    'user' => 'root',
    'pass' => '***',
    ```

    3. 修改.htaccess
    ```
    RewriteBase /DMNovel
    ```
    
4. 打开浏览器输入地址

默认用户名admin,密码1234

# Nginx 配置

    简单的例子

    ```
    server {
        listen 80 default_server;
        listen [::]:80 default_server;

        root /var/www/html;

        index index.php index.html index.htm;

        server_name _;

        location / {
            if (!-e $request_filename) {
                rewrite ^/(.*)$ /index.php?$1 last;
            }
        }

        location ~ \.(css|js|jpg|png|woff2|svg)$ {
            expires 30d;
            access_log off;
        }
        
        location ~ \.php$ {
            fastcgi_pass 127.0.0.1:9000;
            #fastcgi_pass unix:/run/php7.2-fpm.pid;
            fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
            fastcgi_param  PATH_INFO  $fastcgi_path_info;
            fastcgi_param  PATH_TRANSLATED  $document_root$fastcgi_path_info;
            include snippets/fastcgi-php.conf;

        }

        # deny access to .htaccess files, if Apache's document root
        # concurs with nginx's one
        #
        location ~ /\.ht {
            deny all;
        }
    }
    ```
# 自动更新

    使用cron进行自动更新。在服务器上增加。每天早上1点进行更新。
    # crontab -e 

    ```
    0 1 * * * curl http://localhost/update
    ```

# 预览图

![首页](https://images.gitee.com/uploads/images/2019/0509/095730_7a907ae5_62743.png "首页")
![书籍详情](https://gitee.com/uploads/images/2019/0507/162219_83a1cb0c_62743.png "书籍详情")
![章节](https://gitee.com/uploads/images/2019/0507/162248_a0e9077d_62743.png "章节")
![排行](https://images.gitee.com/uploads/images/2019/0509/095608_e28ffa12_62743.png "排行")
![分类](https://images.gitee.com/uploads/images/2019/0516/092944_4b454d81_62743.png "分类")
![搜索](https://images.gitee.com/uploads/images/2019/0516/093117_13a77575_62743.png "搜索")

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)