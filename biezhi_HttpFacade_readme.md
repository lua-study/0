#HttpFacade

一款轻量级(Very Very Light)HTTP客户端工具. 大部分代码拷贝自[jsoup](https://github.com/jhy/jsoup),但去除了HTML的解析部分。

## HttpFacade 能做什么？
使用简单API发起HTTP请求

1. 简单HTTP请求
```
String body = HttpFacade.connect("http://.....")
  .data("arg1","a parameter")
  .data("arg2","another parameter")
  .get();//or post()
```
`.data()`方法加入的参数默认都会进行`URLEncode`编码，编码方式默认为`UTF-8`.
`body`为返回值字符串。

2. POST报文体
```
HttpFacade.connect("http://.....")
    .post("  I am a message post to server.  ");
```
需要注意的是，使用`.data()`方法加入的参数会追加到URL的`?`后面而不会干扰您传入的报文体，这种直接POST的报文不会进行URLEncode。如果需要，你可以自己先进行编码：
```
String xml=URLEncoder.encode(" ... ", "UTF-8")
HttpFacade.connect("http://.....")
    .post(xml);
```

3. 其它自定义选项
```
String body = HttpFacade.connect("http://....../")
    .ignoreBlankParameters(false)//空字符串（包括null）不会被忽略
    .ignoreHttpErrors(true)//即使返回的`HttpStatus`不在200~400之间时也不抛出异常
    .charset("GBK")//使用GBK编码
    .contentType("application/x-www-form-urlencoded")
    .accept("application/json")
    .userAgent("Mozilla/5.0 (Windows NT 5.1; rv:5.0) Gecko/20100101 Firefox/5.0")
    .data("ID", null)//因为设置了*不忽略空参数*,所以会生成"&ID="到url后面（GET）或报文里（POST）
    .data("LOGIN_NO", loginNo)
    .signer(signer)//追加签名参数, signer必须实现`org.terramagnet.http.signature.Signer`接口
    .post();
```
更多配置项请参考[JavaDoc].

4. 上传文件
```
InputStream is = null;
try {
    is = new FileInputStream("C:\\Users\\Administrator\\Pictures\\psb.png");
    HttpFacade.connect("http://....../")
        .data("file", "我的图片1.png", is)
        .post();
} finally {
    if(is!=null){
        is.close();
    }
}
```

## 为什么选择 HttpFacade ？

除`org.slf4j.slf4j-api`这个日志依赖外，没有其他第三方依赖。

这个是个比[OkHttp](http://square.github.io/okhttp/)还要小的HttpClient

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)