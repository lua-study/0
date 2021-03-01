##Usage
    var express = require('express'),
    	express_velocity = require('./express_velocity.js');

    var app = express();

    app.configure(function(){
      app.set('views', __dirname + '/views');
      app.set('view engine', 'vm');
      app.engine('.vm',express_velocity.render);
    });

    app.get('/', function(req, res){
      res.render('index.vm', {
        title: 'Home'
      });
    });




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)