# anshuoyun

#### Description
安的货运

#### Software Architecture
Software architecture description

#### Installation

1. `git clone https://gitee.com/an_logistics_project/anshuoyun.git`
2. `cd path/to/project`
3. `php init`
4. `composer install`
5. set config in `common/config/main-local.php`
6. 新建`path/to/project/web/storage/uploads`并挂载uploads目录，测试环境：`mount -o rw -t nfs 49.235.220.19:/share/nfs/anshuoyun/web/storage/uploads web/storage/uploads`
7. 设置每分钟任务`php /path/to/yii schedule/run --scheduleFile=path/to/schedule.php 1>> /dev/null 2>&1`

#### 伪静态

##### nginx

    location / {
        try_files $uri $uri/ /index.php$is_args$args;
    }
    location /home {
            try_files $uri $uri/ /home/index.php$is_args$args;
    }
    location /admin {
            try_files $uri $uri/ /admin/index.php$is_args$args;
    }
    
    location / 
    {
         index  index.html index.htm index.php;
         if (!-e $request_filename) {
               rewrite ^/(.*)$ /index.php?s=$1 last;
               rewrite ^/home(.*)$ /home/index.php?s=$1 last;
               rewrite ^/admin(.*)$ /admin/index.php?s=$1 last;
               break;
         }
         #autoindex  on;
    }
    
##### apache
    
    Options +FollowSymLinks
    IndexIgnore */*
    RewriteEngine on
    
    # if a directory or a file exists, use it directly
    RewriteCond %{REQUEST_FILENAME} !-f
    RewriteCond %{REQUEST_FILENAME} !-d
    
    # otherwise forward it to index.php
    RewriteRule . index.php

#### Contribution

1. Fork the repository
2. Create Feat_xxx branch
3. Commit your code
4. Create Pull Request


#### Gitee Feature

1. You can use Readme\_XXX.md to support different languages, such as Readme\_en.md, Readme\_zh.md
2. Gitee blog [blog.gitee.com](https://blog.gitee.com)
3. Explore open source project [https://gitee.com/explore](https://gitee.com/explore)
4. The most valuable open source project [GVP](https://gitee.com/gvp)
5. The manual of Gitee [https://gitee.com/help](https://gitee.com/help)
6. The most popular members  [https://gitee.com/gitee-stars/](https://gitee.com/gitee-stars/)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)