# DeepinOceanModuleBackend

#### 介绍
DeepinOceanModuleBackend 是旗鱼后台推出的模块化后台项目，旗鱼后台是德州深之海网络技术有限公司推出的跨语言的模块化后台，采用php，python，nodejs，java等语言进行模块开发，通过nginx等反向代理代理服务器将模块整合到一个大后台中！

旗鱼后台 是深海软件推出的基于微服务开发的后台，每个模块独立运行，用户可以在此基础上对接自己的项目也可以单独将某个模块集成到自己的项目中，模块完全独立不受限于开发语言。

更多内容请看 [http://www.c2ccode.com/](http://www.c2ccode.com/)

#### 架构图
- ![avatar](http://img.c2ccode.com/2020-05-23/1590214855_50156.jpg)

#### 效果图
- ![avatar](http://demo.c2ccode.com/uploads/20200322/635391584854706.png)
- ![avatar](http://demo.c2ccode.com/uploads/20200322/38091584854819.png)
- ![avatar](http://demo.c2ccode.com/uploads/20200322/581281584854851.png)
- ![avatar](http://demo.c2ccode.com/uploads/20200322/70151584854884.png)

#### 目录结构
- DeepinOceanCms：
    - pcweb[基于ThinkPHP开发的cms前端项目]
    - c2ccode-backend[后台静态资源]
        - c2ccode-backend-conf.json[线上配置文件]
        - c2ccode-backend-conf-dev.json[开发环境配置文件]
    - c2ccode-backend-dashboard[后台用户中心]
        - pyapi[基于python3的后台接口]
        - adminview[基于vue-admin-element的后台视图]
    - c2ccode-backend-mcenter[会员中心]
        - pyapi[基于python3的后台接口]
        - adminview[基于vue-admin-element的后台视图]
    - c2ccode-backend-bbs[论坛中心]
        - pyapi[基于python3的后台接口]
        - adminview[基于vue-admin-element的后台视图]
    - c2ccode-backend-tools[工具中心]
        - pyapi[基于python3的后台接口]
        - adminview[基于vue-admin-element的后台视图]
    - InitCentos.py[centos环境初始脚本]

#### 常用软件
|软件|版本|
|---|---|
|mysql|>5|
|redis|>5|
|python|>3.6|
|rabbitmq|3.8.3|
|erlang|OTP22.1|
|php|>5|
|nginx|1.15.9|
|thinkphp|5.2|

#### Python扩展

|扩展|版本|安装方法|
|---|---|---|
|tornado|6|pip3 install tornado==6.0|
|Pillow|4|pip3 install Pillow==4.0|
|xlrd|x|pip3 install xlrd|
|pika |x|pip3 install pika |
|geoip2 |x|pip3 install geoip2 |
|redis  |x|pip3 install redis |
|markdown |x|pip3 install markdown |


#### pycurl扩展
```
http://demo.c2ccode.com/pycurl-7.43.0.2.tar.gz
```

#### 配置nginx
```
##
# C2CCODE-BACKEND Nginx配置
# v0.19.10
# 作者：一名无聊的程序员
# 网址: http://www.c2ccode.com
# 日期：2019年10月01日
#
# 注意：
# 1，关闭配置文件对外访问的权限
# 2，注意反向代理的真实IP
# 
# 10012端口本身是为后台通知资讯预留，后因为通知资讯合并在控制台因此版本号至今未用到
# 
##
# 用户中心+控制台
upstream c2ccode_backend_api_dashboard {
    server 127.0.0.1:10010;
}
# 会员管理
upstream c2ccode_backend_api_mcenter {
    server 127.0.0.1:10011;
}
# 工具中心
upstream c2ccode_backend_api_tools {
    server 127.0.0.1:10013;
}
# 论坛管理
upstream c2ccode_backend_api_bbs {
    server 127.0.0.1:10023;
}
server {
    index index.php index.html index.htm index.nginx-debian.html;
    server_name demo.c2ccode.com;
# 用户中心+控制台
    location /apirbac {
        proxy_pass_header Server;
        proxy_set_header Host	$http_host;
        proxy_set_header X-Real-IP	$remote_addr;
        proxy_set_header s-Scheme	$scheme;
        proxy_set_header REMOTE-HOST $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_redirect off;
        proxy_pass http://c2ccode_backend_api_dashboard;
    }
# 工具中心
    location /apitools {
        proxy_pass_header Server;
        client_max_body_size 5m;
        proxy_set_header Host	$http_host;
        proxy_set_header X-Real-IP	$remote_addr;
        proxy_set_header REMOTE-HOST $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_redirect off;
        proxy_pass http://c2ccode_backend_api_tools;
    }
# 会员管理
    location /api-mcenter {
        proxy_pass_header Server;
        client_max_body_size 5m;
        proxy_set_header Host	$http_host;
        proxy_set_header X-Real-IP	$remote_addr;
        proxy_set_header REMOTE-HOST $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_redirect off;
        proxy_pass http://c2ccode_backend_api_mcenter;
    }
# BBS
    location /api-bbs {
        proxy_pass_header Server;
        client_max_body_size 5m;
        proxy_set_header Host	$http_host;
        proxy_set_header X-Real-IP	$remote_addr;
        proxy_set_header REMOTE-HOST $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_redirect off;
        proxy_pass http://c2ccode_backend_api_bbs;
    }
# 禁止访问配置文件
    location =/c2ccode-backend-conf.json {
        return 404;
    }
# 禁止访问sqls目录
    location /sqls/ {
        return 404;
    }
# 首页
    location / {
        root /workspace/c2ccode-backend;
        index index.html index.htm;
    }
# 自定义404
    error_page 404  /404/index.html;
}

```

#### 使用说明

- 配置环境
    - centos系统直接运行InitCentos.py
- 下载项目
```
git clone https://gitee.com/c2ccode/DeepinOceanCms.git
```
- 配置nginx
    - 复制demo.nginx.conf 到nginx配置目录
    - 修改demo.nginx.conf 的后台目录，定位到c2ccode-backend目录
    - 配置php配置文件，定位到pcweb/public目录
- 复制配置文件
    - 复制c2ccode-backend/c2ccode-backend-conf.json 到 c2ccode-backend/c2ccode-backend-conf-dev.json
    - 修改配置文件
    - 修改c2ccode-backend/c2ccode-backend-conf.json文件的tools conf_pathdir 和 tools conf_host
- 创建数据库，并导入mysql文件
    - 数据库跟配置文件中一致
    - 导入表数据，在sqls目录中
    
|文件|描述|
|----|----|
|sqls/c2c_ucenter.sql|后天用户中心|
|sqls/c2c_tools.sql|工具中心|
|sqls/c2c_mcenter.sql|会员中心|
|sqls/c2c_bbs.sql|论坛数据库|
- 启动接口文件
    - 运行启动脚本
```
python3.x sailfish.py start dev
```



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)