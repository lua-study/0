#HashGoLink
**这是一个轻量级的前端页面跳转/传值方案**。一共包括两种:  
1.在页面的url后面加入'#/',参数跟在后面,然后下一个页面从中获取这些参数  
2.通过本地存储localStorage(HTML5).


插件依赖于[jQuery库](http://apps.bdimg.com/libs/jquery/2.1.4/jquery.min.js)，在引入HashGoLink.js之前请确保已引入[jQuery库](http://apps.bdimg.com/libs/jquery/2.1.4/jquery.min.js).
首先你需要通过'new'来创建一个实例:
> var myapp = new link();


link()下的参数简单说明:
```
 
var myapp = new link();
myapp.go(url,value,element,toggle);
```


- **url**:代表需要跳转的下个页面
- **value**:需要传递的参数,一般为字符串或数组
- **element**:传递一个元素,该元素下的所有a链接将会被绑定该跳转传值事件.如果每个A链接对应的参数都不相同,你也可以将这些参数写在A连接的rel属性里，同时将Value的值设置为'rel'.
- **toggle**:[非必要],默认值为true.设置为false时会取消url改变，仅仅使用本地存储传值

```
 
myapp.link();
```
↑无参数,返回**上一个页面的链接**中带有的参数,如果链接中没有参数则不返回.

```
 
myapp.data();
```
↑无参数,返回**上一个页面本地存储**中的值,在myapp.go时这个值已经被自动存储到了本地.


两个简单的使用示例:

```
 
 
			 链接A 
			 链接B 
			 链接C 
		 
		 
			var api = new link(),
				e = $(".index-box");
				api.go('list.html','rel',e,false)
		 
```

```
 
		 
			 链接A 
			 链接B 
			 链接C 
		 
		 
			var api = new link(),
				e = $(".index-box");
			api.go('list.html',['a',2,'qwe',1414],e);
		 
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)