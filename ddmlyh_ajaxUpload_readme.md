AjaxUpload
========
>
@author：yangjian102621@gmail.com 

插件描述:
--------
javascript异步上传插件，包含3个子项目BUpload, JUpload, TUpload.
* BUpload : 基于HTML5， UI仿百度编辑器的图片上传, 支持图片上传，浏览图片，和图片搜索，支持图片预览，有进度条
* TUpload : 基于HTML5， UI仿腾讯的QQ空间上传图片，支持图片预览，有进度条。
* JUpload : 基于iframe的异步上传。


插件依赖:
-------
* jQuery-1.7.1以上版本

使用demo
------
####BUpload
```javascript
	$("#upload-btn").on("click", function() {

		new BUpload({
			upload_url : "upload.php",
			list_url : "image_list.php",	//图片列表数据获取url
			search_url : "image_search.php",	//图片搜索页面url
			max_filesize : 1024,
			max_filenum : 10,
			callback : function(data) {
				$.each(data, function(idx, item) {
					$("#image-box").append(' ');
				});
				console.log(data);
			}
		});

	});
```

####TUpload
```javascript
	$("#upload-btn").on("click", function() {

		new TUpload({
				uploadUrl : "upload.php",
				maxFileSize : 1024,
				maxFileNum : 20,
				callback : function(data) {
					$.each(data, function(idx, item) {
						$("#image-box").append(' ');
					});
					console.log(data);
				}
			});

	});
```

####JUpload
```javascript

    $("#upload-btn").JUpload({
		url : "upload.php",
		src : "src",
		image_container : "image-box"
	});

	$("#upload-btn2").JUpload({
		url : "upload.php",
		src : "src",
		callback : function(data) {
			$("#img-src").val(data.message);
		}
	});
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)