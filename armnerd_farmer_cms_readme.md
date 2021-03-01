server {
   listen 80;
   server_name www.kaixiang.com;
   root /data/kaixiang/public;
   index index.html
   index.php;
   location / {
        try_files $uri $uri/
        /index.php$is_args$query_string;
   }
   location ~ \.php$ {
        try_files $uri =404;
        fastcgi_pass 127.0.0.1:9000;
        fastcgi_index index.php;
        fastcgi_param SCRIPT_FILENAME
        $document_root$fastcgi_script_name;
        include fastcgi_params;
   }
}


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)