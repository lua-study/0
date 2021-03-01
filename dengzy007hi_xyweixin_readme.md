###xyweixin

查看将网页分享到微信朋友圈、发送给微信朋友两个功能的代码请点击下面的链接：

http://git.oschina.net/baayso/xyweixin/blob/master/src/main/java/cn/xyspace/xyweixin/fun/weixin/WeixinController.java

http://git.oschina.net/baayso/xyweixin/blob/master/src/main/java/cn/xyspace/common/core/utils/WeixinApiUtils.java


http://git.oschina.net/baayso/xyweixin/blob/master/src/main/webapp/WEB-INF/views/resource/detail.html


resource/detail.html部分js代码：

```javascript
  

 

	var shareUrl = window.location.href.split('#')[0];

	// 进行第一次编码
	var shareUrlEncode = encodeURIComponent(shareUrl);
	// 进行第二次编码
	shareUrlEncode = encodeURIComponent(shareUrlEncode);

	// alert(shareUrlEncode);

	var wxConfig = {};

	// 在DOM加载完成时运行的代码
	$(document).ready(function () {
		// 在这里写你的代码...
	})

	//        wx.checkJsApi({
	//            jsApiList: ['chooseImage'], // 需要检测的JS接口列表，所有JS接口列表见附录2,
	//            success: function (res) {
	//                // 以键值对的形式返回，可用的api值true，不可用为false
	//                // 如：{"checkResult":{"chooseImage":true},"errMsg":"checkJsApi:ok"}
	//            }
	//        });

	$.ajax({
		async: false,
		type: "POST",
		url: "${ctxPath}/weixin/signature",
		data: "shareUrl=" + shareUrlEncode,
		dataType: 'json',
		success: function (result) {
			// alert(result);
			// $("#modalContent").html(msg);
			// $("#your-modal").modal();
			// wxConfig = $.parseJSON(result);
			wxConfig = result;
			// alert(wxConfig.appId);
		}
	});

	// 微信配置
	wx.config({
		debug: true, // 开启调试模式,调用的所有api的返回值会在客户端alert出来，若要查看传入的参数，可以在pc端打开，参数信息会通过log打出，仅在pc端时才会打印。
		appId: wxConfig.appId, // 必填，公众号的唯一标识
		timestamp: wxConfig.timestamp, // 必填，生成签名的时间戳
		nonceStr: wxConfig.nonceStr, // 必填，生成签名的随机串
		signature: wxConfig.signature, // 必填，签名，见附录1
		jsApiList: [
			'onMenuShareTimeline',
			'onMenuShareAppMessage',
			'onMenuShareQQ',
			'onMenuShareWeibo'
		] // 必填，需要使用的JS接口列表，所有JS接口列表见附录2
	});
```



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)