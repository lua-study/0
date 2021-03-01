# layui-ctyun

#### 介绍
layui整合天翼云jssdk

#### 软件架构
layui整合天翼云jssdk


#### 安装教程
1.  下载直接安装到modules目录

#### 使用说明

模块中直接连接的天翼云的官方jssdk，也可以修改成本地路径即可。
使用简单，直接传天翼云的相关参数进去就行，支持自定义FilesAdded、FileUploaded、ChunkUploaded、BeforeUpload等方法。

``` javascript
layui.config({
	base: '__PUBLIC__/layui/' //静态资源所在路径
}).extend({
	ctyun: 'ctyun/index',
}).use(['index', 'ctyun'], function(){
	var $ = layui.$
	,element = layui.element
	,layer = layui.layer
	,ctyun= layui.ctyun;
	ctyun.loader({
		endPoint: '{$config.ctyun_domain}'
		, browse_button: "upload-video" 
		, drop_element: "hahaha" 
		, BucketName: "{$config.ctyun_bucket}"
		, accessKeyId: "{$config.ctyun_access_key}"
		, secretAccessKey: "{$config.ctyun_secret_key}"
		, initial: true
		, UploadProgress: function(response){
			$(".show_video").show();
			$(".layui-progress").hide();
			element.progress('video-progress', response.percent + '%');
		}
		, UploadComplete: function(res){
			// layer.closeAll('loading'); // 可以调用loading
			layer.msg("上传成功！");
			$("#video_url").val(res.Location);
			$(".show_video").find("video").attr("src", res.Location);
			$(".layui-progress").hide();
		}
	})
});
```






 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)