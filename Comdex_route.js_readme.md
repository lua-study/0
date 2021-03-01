#route.js
路由注册/解析器，它在不刷新页面的情况下，利用“#”符号组织不同的URL路径，并根据不同的URL路径来匹配不同的回调方法

[原生 js前端路由系统实现1](http://my.oschina.net/diqye/blog/476286) 

[原生 js前端路由系统实现2之代码可读性 和可扩展性](http://my.oschina.net/diqye/blog/477083) 

[原生 js前端路由系统实现3之代码 构建工具 和 querystring功能](http://my.oschina.net/diqye/blog/477602) 

[原生 js前端路由系统实现4之 低版本ie兼容性](http://my.oschina.net/diqye/blog/478127) 

[runjs演示](http://sandbox.runjs.cn/show/mg3ch4e4) 

如果要兼容IE8以下 在head标签里面加入以下代码

```
 
  
 
```

url：xxx#home?a=a&b=b
```
var get=diqye.route.get;
get('/home',function(req,next){
	//调用next会继续匹配后面的路由
	console.log(req.query)// 输出 {"a":"a","b":"b"}
})

diqye.route.start();//调用此函数 所有路由才会生效  下面代码省略
```

url: xxx#test/id001
```
var get=diqye.route.get;
get('/test/:string',function(req,next){
	//调用next会继续匹配后面的路由
	console.log(req.para)// 输出  id001
});
get('/test*',function(req){
	//do .....
});
```

url: xxx##homediqyeddddd
```
var get=diqye.route.get;
get(/(.*)diqye(.*)/g,function(req,next){
	console.log(req.para); //输出 ["/homediqyeddddd", "/home", "ddddd", index: 0, input: "/homediqyeddddd"]
});
```
未知的路由
```
var get=diqye.route.use; //use类似node中的use函数 拦截器功能
use(function(req,next){
	//把这个函数放到最后  如果前面所有的路由没有匹配到 会走到这里
});
```
build.js 说明
```
//命令行 切换到当前目录
node build.js //将src目录文件 按照名字规则合并到js目录里

node build.js watch //与上面不同的是 会监控src目录 有变化就执行合并操作
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)