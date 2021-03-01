# layui-qiniuyun

#### 介绍
layui整合七牛云jssdk

#### 软件架构
layui整合七牛云jssdk


#### 安装教程

1.  下载直接安装到modules目录

#### 使用说明

模块中直接连接的七牛云的官方jssdk，也可以修改成本地路径即可。
使用简单，直接传域名和token进去就行，支持自定义next、error、complete方法。

``` javascript
layui.config({
    base: '__PUBLIC__/layui/' //静态资源所在路径
  }).extend({
    qiniuyun: 'qiniuyun/index',
  }).use(['index', 'qiniuyun'], function(){
    var $ = layui.$
    ,element = layui.element
    ,layer = layui.layer
    ,qiniuyun = layui.qiniuyun;
	qiniuyun.loader({
		domain: '{$domain}'              // 后台设置的域名项
		, elem: "#upload-video"          // 绑定的element
		, token: "{$token}"              // 授权token
		, retryCount: 6                  // 重连次数，默认6(可选)
		, region: qiniu.region.z0        // 选择上传域名区域，默认自动分析(可选)
		, next: function(response){
			element.progress('video-progress', response.total.percent + '%');       // 进度条
		}
		, complete: function(res){
			// layer.closeAll('loading'); // 关闭loading关闭
			layer.msg("上传成功！");
			console.log(res) 
		}
	});
});
```




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)