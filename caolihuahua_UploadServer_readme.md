
# 项目一、统一文件上传服务

## 特点
1. 前端直接上传  
2. 使用jwt和origin做权限控制
3. 分块上传
4. 支持多个项目上传

## 配置
```json
{
  "AllowedHosts": "*",
  "urls": "http://localhost:6001",
  "uploadServer": {
    "rootUrl": "http://localhost:6001",//访问网址根目录，如果上面有代理，就是代理的地址
    "entryPoint1": "/upload", //一般上传入口
    "entryPoint2": "/chunkUpload", //分块上传入口
    "virtualPath": "", //本服务监听请求根目录
    "physicalPath": "/Users/loogn/Desktop/uploader",//上传后静态文件根目录物理路径
    "appendMimes": ".htm3:text/html;",//响应访问时添加的mime类型
    "responseCache": 604800, //响应访问时缓存设计，单位（秒）
    "jwtSecret": "1234561234",//jwt加密秘钥
    "limitSize": "20mb", //默认上传大小，只支持mb和kb为单位
    "allowExts": ".txt;.jpg;.jpeg;.png;.doc;.docx;.xls;.xlsx;.ppt;.pptx;.pdf",//默认允许的文件后缀
    "apps": { //特定项目配置
      "default": {   //默认配置
        "allowOrigins": "*",  //允许的origin
        "limitExts":".exe;",  //禁止的文件后缀
        "enableThumbnail": true, //是否启用图片缩率图功能，osx和linux系统需要安装libgdiplus
        "thumbnailExts": ".jpg;.png" //启用缩率图的文件后缀
      },
      "app1": { //app1项目的配置，格式和default一样，没有的项会使用default的设置
        "allowOrigins": "*"
      }
      ......
    }
  }
}
```

## JWT说明
jwt官方：[jwt.io](https://jwt.io)  
jwt的payload中支持四项设置：
1. exp : utc时间戳，必填，表示过期时间  
2. app : 表示项目名称和存储文件夹，必填,该项目上传的文件会存放在 uploadServer.physicalPath/app/路径下面  
3. size : 该项目上传大小，只支持mb和kb单位，选填，没有该项会使用 uploadServer.limitSize  
4. exts : 该项目额外支持的文件类型，选填，该项目支持的上传类型为 uploadServer.allowExts+exts-limitExts


## 上传
1. 一般上传，FrontEndDemo例子中使用的ajaxfileupload.js，其他的应该也可以，jwt使用form传入上传服务器  
2. 分片上传使用[simple-uploader](https://github.com/simple-uploader/Uploader)，jwt可以从header和form传输

## 返回值
1. 成功,url为rootUrl + physicalPath之后的文件路径
    ```json
    {"ok":true,"msg":null,"url":"http://localhost:6001/test/2019/06/17/abcd.jpg"}
    ```
2. 失败：
      ```json
      {"ok":false,"msg":"The file is too big","url":null}
      ```


## 流程

1. 客户端请求后端获取jwt  
2. 客户端在header或者form中携带jwt请求UploadServer上传接口
3. 成功后UploadServer返回上传文件的Url给前端
4. 客户端使用url显示或者存储到后端  



 
     




# 项目二、aspnetcore分布式上传文件系统
## 系统架构图
![](https://gitee.com/loogn/ufs/raw/master/art.png)

上图描述了用户上传和查看的流程走向，系统主要涉及到ufs和下面的ufs.node。
ufs是web网站或者app上传的统一接口，ufs根据配置把上传的文件分发到某个ufs.node节点。
ufs.node会返回上传结果给ufs，这里主要是上传成功文件的url，ufs收到Url再返回给上层应用。
上层应用获取到url可以展示出来或者存储到数据库。
当用户访问资源的时候，直接从各个ufs.node获取。

##  ufs配置
```json
{
  "ufs": {
    "allowExts": [".txt", ".jpg", ".jpeg", ".png", ".bmp", ".doc", ".docx", ".xls", ".xlsx", ".ppt", ".pptx", ".pdf"],
    "limitSize": 10485760,
    "accessToken": "123456",
    "downstreams": [
      "http://node1.ufs.loogn.com"
    ],
    "test": {
      "limitSize": 10485760,
      "accessToken": "abcd"
    }
  }
}
```
ufs就像上传系统的网关，提供了下面这几个功能配置：
1. allowExts配置可以上传的文件类型
2. limitSize限制文件上传的大小
3. accessToken为访问上传系统的令牌
4. downstreams配置ufs.node节点  

上面配置中，和ufs平级还有一个test节点，里面允许的子节点和ufs的子节点是一样的。目的是实现为不同的应用提供上传服务。“test”就是应用名称，这个名字是和应用程序约定好的，应用app1上传的时候表明是app1，就会使用配置文件中app1的配置，如果配置文件中没有app1这个节点配置，就会使用ufs节点下的默认配置。
这样的配置方式就像该配置文件本身（appsettings.json）的加载方式一样，会使用专门指定的配置覆盖默认配置，非常灵活。至于如何调用，我们后面再说。

## ufs.node配置
```json
{
  "ufsNode": {
    "mimeModifiers": [
      {
        "ext": ".htm3",
        "type": "text/html",
        "opt": "add"
      },
      {
        "ext": ".mp4",
        "opt": "remove"
      }
    ],
    "domain": "http://node1.ufs.loogn.com",
    "physicalPath": "D:/WebSite_Core/ufsnode1/upload",
    "virtualPath": "/ufs",
    "cachePeriod": 604800,
    "enableThumbnail": true,
    "thumbnailExts": [
      ".jpg",
      ".png"
    ],
    "allowIPs": [
      "::1",
      "127.0.0.1",
      "122.114.222.186"
    ]
  }
}
```
node的配置比ufs要多一些，毕竟真正的存储和访问功能是在具体的node：
1. mimeModifiers该数组可以修改node服务的mime类型，每一项有三个字节点，ext为文件后缀名，type为映射的ContentType,opt是枚举add、remove。
2. domain为该node服务运行的域名，影响返回的url
3. physicalPath为上传的物理路径
4. virtualPath为上传的虚拟路径，影响返回的url
5. cachePeriod过期时间（秒）
6. enableThumbnail是否启用缩略图功能
7. thumbnailExts表示那些文件类型可以使用缩略图功能，只能配置图片格式
8. allowIPs访问白名单，即ufs服务的ip地址

当启用缩率图功能后，可以使用在url中加w和h参数来访问想要的缩略图：  
原图：http://node1.ufs.loogn.com/app1/2019/05/10/abc.png  
限宽200：http://node1.ufs.loogn.com/app1/2019/05/10/abc.png?w=200  
限高200：http://node1.ufs.loogn.com/app1/2019/05/10/abc.png?h=200  
限宽高100*200：http://node1.ufs.loogn.com/app1/2019/05/10/abc.png?w=100&h=200  
所有的压缩都是等比的，图片不会变形，而且不管参数怎样，图片是不会放大的。  

从allowIPs配置可以看出，应用层访问ufs是用过accessToken来验证的，而ufs访问node是通过在node中配置允许的ip地址来实现的。


## 应用层调用

由于公开的是http接口，所以任何支撑Http的语言都可以使用。
```csharp
        static async Task  UploadFile(string filePath)
        {
            HttpClient httpClient = new HttpClient();
            httpClient.DefaultRequestHeaders.Add("accesstoken", "abcd");
            httpClient.DefaultRequestHeaders.Add("app", "test");
            
            var buffer = File.ReadAllBytes(filePath);
            ByteArrayContent byteArray = new ByteArrayContent(buffer);
            byteArray.Headers.Add("ext", Path.GetExtension(filePath));
            var response = await httpClient.PostAsync("http://ufs.loogn.com/uploadfile", byteArray);

            var result = await response.Content.ReadAsStringAsync();
            return result;
        }
```
http请求头部需要传输三个参数： 
1. accesstoken为访问ufs的令牌，对用ufs中的配置
2. app为指定app的名称，除了和ufs服务中选择配置相关，node服务也会在physicalPath目录下建立app同名目录，用来存放这个应用上传的文件 
3. ext为上传文件的后缀名，注意，是带.的（比如：.jpg而不是jpg）  

文件内容使用请求体POST到ufs公开的uploadfile地址，响应的字符串是json格式，如下：
```json
{"success":true, "msg":"", "fileUrl":"http://node1.ufs.loogn.com/app1/2019/05/10/abc.png"}
```
如果上传失败，success为false，msg中有错误信息。

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)