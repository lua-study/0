# ambari-web
This repository contains required modifications to ambari-web javascripts in order to deploy a keedio stack with ambari  

```
cp app.js /tmp/;gzip /tmp/app.js;cp -f /tmp/app.js.gz /usr/lib/ambari-server/web/javascripts/
cp app.css /tmp/;gzip /tmp/app.css;cp -f /tmp/app.css.gz /usr/lib/ambari-server/web/stylesheets/
cp -r app/assets/img/keedio /usr/lib/ambari-server/web/img/
cp app/assets/font/* /usr/lib/ambari-server/web/font/
cp app/assets/index.html /usr/lib/ambari-server/index.html
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)