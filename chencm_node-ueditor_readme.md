#node-ueditor

##使用方法

1.在app.js中引用uediotr.js并配置路由

		var ueditor = require('./ueditor');

		app.post('/ueditor/img-manager', ueditor.imgManager);
		app.post('/ueditor/img-up', ueditor.imgUp);

2.修改ueditor.config.js配置

		,imageUrl:URL+"img-up"              				//图片上传提交地址

		,imageManagerUrl:URL + "img-manager"       //图片在线管理的处理地址

##显示效果

在编辑器中插入图片

![在编辑器中插入图片](http://git.oschina.net/wannianchuan/node-ueditor/raw/master/ueditor-insert-img.png)

在文章中显示

![在文章中显示](http://git.oschina.net/wannianchuan/node-ueditor/raw/master/img-show-in-article.png)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)