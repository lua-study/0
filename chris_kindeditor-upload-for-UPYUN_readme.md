# 常见问题

##upyun接口运用
*	上传模式采用目前流行的HTTP REST API接口形式
*	Upyun响应的API错误全部封装返回到KindEditor中，可以清楚的调试自己的应用

##Kindeitor怎么样使用Upyun
* 此插件保留kindeditor源代码，未进行任何改写，而是采用新增类库的方式。
* kindeditor的配置保持不变，想采用upyun上传,只需更改kindeditor初始化变量uploadJson的对应路径即可（详细查看demo中的index.html）
```javascript
 
		var editor;
			KindEditor.ready(function(K) {
				editor = K.create('textarea[name="content"]', {
					allowFileManager : true,
					'uploadJson' : 'kindeditor/php/upyunUpload.php'
				});
			});
	 

```
* upyunUpload类中由于作者兼顾低版本PHP没有json格式解析问题，所以引入了json的库，如需用到实际生产环境，可以更改对应的alert方法即可。也可复制此类到自己项目对应的目录做自己的规划。
* 上传过程不保留本地文件，有用户需要保留备份到本地的可以对上传类进行对应的修改
* Kindeditor 支持多种类型的上传，所以在Upyun创建空间的时候请选择文件类，如果选择图片类 很多文件将上传不成功
* 使用前请修改upyunUpload类中的配置信息，和调用的初始化信息。demo中改用的是作者的空间（仅供测试使用）,实际生产环境请改成自己的。

##作者信息
* QQ 531209114 从事PHP开发和前端js开发

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)