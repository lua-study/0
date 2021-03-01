#描述

最近在云栖社区的雨客的博客上看到了一个设计图形验证码的案例，经过试验和目前OpenResty的最新功能，对原来代码进行了调整（采用OpenResty自带的Redis库、替换了原来有问题的随机数种子设置逻辑），另外也增加了独立删除验证码的接口，后续可能会视需要增加图形验证码的分片存储等功能

#代码结构

lua_scripts  接口的实现逻辑脚本

lualib       替换lua-uuid库的lua脚本实现

nginx        nginx配置文件


#依赖

gd图形处理库[http://www.boutell.com/gd/http/gd-2.0.33.tar.gz](http://www.boutell.com/gd/http/gd-2.0.33.tar.gz "gd-2.0.33")

nginx sysguard模块[https://github.com/alibaba/nginx-http-sysguard/archive/master.zip](https://github.com/alibaba/nginx-http-sysguard/archive/master.zip "nginx sysguard模块")

OpenResty[http://openresty.org/download/openresty-1.9.15.1.tar.gz](http://openresty.org/download/openresty-1.9.15.1.tar.gz "OpenResty")

Lua-Resty-UUID[https://github.com/dcshi/lua-resty-UUID/archive/master.zip](https://github.com/dcshi/lua-resty-UUID/archive/master.zip "Lua-Resty-UUID")

Lua-GD[http://jaist.dl.sourceforge.net/project/lua-gd/lua-gd/lua-gd-2.0.33r2 (for Lua 5.1)/lua-gd-2.0.33r2.tar.gz]

Redis[http://download.redis.io/releases/redis-3.2.3.tar.gz](http://download.redis.io/releases/redis-3.2.3.tar.gz "Redis")

#使用方法

请求验证码：
http://192.168.10.112:9000/captcha-require
http://192.168.10.112:9000/captcha-require?picgid=abcd1234
http://192.168.10.112:9000/captcha-require?picgid=abcd1234&picwidth=100&picheight=40

验证验证码：
http://192.168.10.112:9000/captcha-check?picgid=abcd1234&picstr=1234
直接返回true或者false



#安装说明

[https://git.oschina.net/kevin158/captcha_server/blob/master/INSTALL.md](https://git.oschina.net/kevin158/captcha_server/blob/master/INSTALL.md "进入")



#联系

堂吉诃德
 
421093703@qq.com




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)