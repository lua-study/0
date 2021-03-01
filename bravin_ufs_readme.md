
# aspnetcore分布式上传文件系统
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