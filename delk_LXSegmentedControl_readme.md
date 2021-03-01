#RadioGroup代替方案，类似iOS中UISegmentedControl

![图1](https://static.oschina.net/uploads/img/201610/22095340_uKuW.png "效果图")

![图0](https://static.oschina.net/uploads/img/201610/22095417_Vs9j.gif "动图")

#布局

##1.样式表

外圈是一个圆角的矩形

内部是第N段取值，其中最后一段为空，声明class为last

选中为底色+白字，普通状态则反之，声明class为selected

```
/*LXSegmentedControl容器*/
.segmentedControl {
	/*水平居中*/
	margin: 30px auto;
	/*边框为2px 主色调为蓝*/
	border: 2px solid #39f;
	/*圆角6px*/
	border-radius: 6px;
	/*控件宽度*/
	width: 240px;
	/*控件高度*/
	height: 30px;
}

/*普通文本*/
.segmentedControl text {
	/*水平排列*/
	float: left;
	/*宽度为控件宽度的1/3 再减去2px的右边框*/
	width: 78px;
	/*字体大小*/
	font-size: 14px;
	/*主色调*/
	color: #39f;
	/*行高，与控件高度相等*/
	line-height: 30px;
	/*文本水平居中*/
	text-align: center;
	/*右边距*/
	border-right: 2px solid #39f;
}

/*选中状态文本*/
.segmentedControl text.selected {
	/*同主色调*/
	background-color: #39f;
	/*前景色为白色*/
	color: white;
}

/*最后一个分组按钮*/
.segmentedControl text.last {
	/*不必右边框*/
	border-right: 0;
	/*高度也不必减少2px，就是控件高度的1/3*/
	width: 80px;
}
```

##2.写上静态的数据作为测试

```
 
	 男 
	 女 
	 保密 
 
```

这里有一个坑：

```
 男 
```
不等同于

```
 
	男
 
```

后者会变成占据两行

##3.改进为数组

```
Page({
	data: {
		radioValues: [
			{'value': '男','selected': false},
			{'value': '女','selected': true},
			{'value': '保密','selected': false},
		]
	}
})
```

##4.循环遍历与样式判断

```
 
	 
	 
		 
		 {{item.value}} 
		 
		 {{item.value}} 
		 
		 {{item.value}} 
	 
 
```

注意：以上判断是错的，当最后一个高亮时却不出selected效果，于是后文再重写。

##5.点击text处理高亮与否

```
	indexChanged: function(e){
		// 点中的是组中第个元素
		var index = e.target.dataset.index;
		// 读取原始的数组
		var radioValues = this.data.radioValues;
		for (var i = 0; i  等标签上判断，实在不好用。

```
	clazzStatus: function(){
		/* 此方法分别被加载时调用，点击某段时调用 */
		// class样式表如"selected last","selected"
		var clazz = [];
		// 参照数据源
		var radioValues = this.data.radioValues;
		for (var i = 0; i  
	 
	 
		 {{item.value}} 
	 
 
```


正文完

源码下载：关注下方的公众号->回复数字1010

对小程序开发有趣的朋友关注公众号: huangxiujie85，QQ群: 575136499，微信: small_application，陆续还将推出更多作品。

![公众号](https://static.oschina.net/uploads/img/201610/07111145_qD6d.jpg "二维码")


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)