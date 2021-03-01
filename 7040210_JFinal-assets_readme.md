## 说明
JFinal框架结合jsp、beetl、freemarker模版的js、css在线合并压缩插件！

结合CDN使用效果更佳哦

## 依赖
1. JFinal

2. yuicompressor

3. commons-io

## 使用
```
 
     net.dreamlu 
     JFinal-assets 
     1.0.0 
 
```

###Beetl中使用
###自定义标签
```
##自定义标签
TAG.assets = net.dreamlu.ui.beetl.AssetsTag
```
###js
```
 
      
 
```
###css
```
 
     
 
```

file: 需要压缩的js、css列表

assets.jjs示例：
```
#开头表注释
/js/jquery.min.js
/js/jquery-ui.min.js
/js/modernizr.min.js
/js/superfish.min.js
/js/application.js
```

###JSP中使用

首先、导入标签库
```
 
```

同理如beetl
```
 
	  
 
```
###freemarker中使用

首先、配置（可在JFinal的config中完成）
``` 
FreeMarkerRender.getConfiguration().setSharedVariable("assets", new AssetsDirective());
```

同理如beetl
```
 
	  
 
```

## 文章
[对css，js压缩之combo以及七牛cdn的思考:http://blog.dreamlu.net/blog/47](http://blog.dreamlu.net/blog/47)

## 更新说明
>## 2015-12-30 v0.0.3
>1. 升级到JFinal2.1，JFinal低版本用户请使用`v0.0.3`

## 交流群
如梦技术：[`237587118`](http://shang.qq.com/wpa/qunwpa?idkey=f78fcb750b4f72c92ff4d375d2884dd69b552301a1f2681af956bd32700eb2c0)

## 捐助共勉
 
 
 

 
 

## License

( The MIT License )

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)