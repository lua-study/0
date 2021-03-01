#LXRowAction

类似iOS中UITableView轻扫删除

##1. 简单布局

```
/*控件容器*/
.RowAction {
	display: flex;
	flex-direction: row;
	justify-content: space-between;
}

/*文本*/
.RowAction text {
	margin: 20px 0 0 20px;
	width: 100%;
}

/*按钮*/
.RowAction button {
	width: 100px;
}

 
	 这是一行文本 
	 删除 
 
```

#2. 监听touch事件

bindtouchmove="bindswipe"

```
bindswipe: function (e) {
		console.log('clientX:'+e.touches[0].clientX);
		console.log('clientY:'+e.touches[0].clientY);
	}
})
```

#3. 计算clientX的位移，使删除按钮移动相应距离

```
	data: {
		startX: 0,
		moveX: 0
	},
	bindstart: function(e) {
		this.setData({
			startX: e.touches[0].clientX
		});
	},
	bindswipe: function (e) {
		// console.log('clientX:'+e.touches[0].clientX);
		// console.log('clientY:'+e.touches[0].clientY);

		// record currentX
		var clientX = e.touches[0].clientX;
		// minus X
		var moveX = clientX - this.data.startX;
		// set moveX for css
		this.setData({
			moveX: -moveX
		});
		console.log(moveX);
		// console.log(e.touches);
	}
```

```
 删除 
```

正文完

源码下载：关注下方的公众号->回复数字1011

对小程序开发有趣的朋友关注公众号: huangxiujie85，QQ群: 575136499，微信: small_application，陆续还将推出更多作品。

![公众号](https://static.oschina.net/uploads/img/201610/07111145_qD6d.jpg "二维码")



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)