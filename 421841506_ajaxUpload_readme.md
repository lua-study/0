AjaxUpload
========
>
@author：yangjian102621@gmail.com 

插件描述:
--------
AjaxUpload 是一个html5异步批量上传插件


插件依赖:
-------
* jQuery-1.7.1以上版本

##[版本更新记录]
version 1.0
******
实现上传的基本功能，支持批量上传

vesion 1.1
****
* 更改上传框为弹窗式，而不是像之前的嵌入式
* 新增了浏览器版本判断，不支持html5直接抛出异常
* 新增了文件大小和文件个数限制
* 新增了上传文件成功后回调函数
* 新增了README.md 文件 


##[Usage]
使用非常简单，只需要一行代码

```javascript
    var options = {
				uploadUrl : "upload.php",
				maxFileSize : 1024,
				maxFileNum : 20,
				callback : function(data) {
					console.log(data);
				}
		}
    new AjaxUpload(options);
    
```
option参数说明:
-------------

Key  | 类型   | 说明
---|--- | ---
src | string | 必需，上传input的name
uploadUrl | string |必需， 文件上传的后台地址,
dataType | string|必需，后台上传返回的数据格式，目前只支持json，也是默认值
maxFileSize | int | 可选，最大上传文件大小， 单位是kb， 默认为 2048KB
maxFileNum | int | 可选， 最大上传文件个数， 默认是20
extAllow | string | 可选，允许上传的后缀名，用竖线隔开
extRefuse | string | 可选, 拒绝上传的后缀名，用竖线隔开
callback | funtion | 必需，点击确定后的回调函数













 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)