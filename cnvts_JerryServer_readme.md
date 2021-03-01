# 一：前言
拿Java举例，现在的网站系统开发模式，对于web端和服务端的数据交互，无外乎两种：一种是交给后端处理，jsp，freemark模板引擎之流，这种需要前端人员做好静态页面交给后端去处理一些其它工作。注意这种模式并非真正的前后端分离！另一种是交给前端处理，前端处理只能使用JS，一些前端js模板引擎也有不少，无论再花哨，本质还是JS，依赖JS处理前端页面存在弊端，如果没弊端那第一种jsp的模式早就淘汰了。

使用JerryServer的好处有两点：

    一是完全真正的前后端分离，后端只做JSON接口，只做接口有啥好处？一套接口适用web、Android、ios各个平台。前端的任务更轻松，使用JerryServer的语法基本一看就懂，后端接口没做好也不影响前端开发。

    二是非JS加载，非JS加载，自然不存在JS加载页面的弊端。

JerryServer正在做的功能：

    一：负载均衡

    二：监控系统

如果你觉得还不错，欢迎私信我！

# 二：功能
- 只需要一行配置，写明服务端JSON接口地址，即可实现自动渲染。
- 支持自定义标签，但千万不要和html标签重复。
- 我的邮箱：yster@foxmail.com
- 我的博客：https://yueshutong.cnblogs.com/

# 三：下载
Github下载：[https://github.com/yueshutong/JerryServer/blob/master/Jerry.rar](https://github.com/yueshutong/JerryServer/blob/master/Jerry.rar)

Gitee下载：[https://gitee.com/zyzpp/JerryServer/blob/master/Jerry.rar](https://gitee.com/zyzpp/JerryServer/blob/master/Jerry.rar)

# 四：如何启动
###### 1.在config可以配置启动端口，在template里有404页面，webapps里放置项目。
![这里写图片描述](https://oscimg.oschina.net/oscnet/facd79c02198850dd045971f1e6a24a34b9.jpg)
##### 2.	windows用户双击startup.exe启动服务器，Linux执行./startup.sh
![这里写图片描述](https://oscimg.oschina.net/oscnet/c9782f0ef183d53629f01f53f7437f13dfe.jpg)

# 五：使用文档
##### 1.	web项目目录
![这里写图片描述](https://oscimg.oschina.net/oscnet/d3574c8c7b74d0ae89c56f48932c2fd7e83.jpg)
##### 2.编辑page.json 
![这里写图片描述](https://oscimg.oschina.net/oscnet/630ad31bf5b236f158cca1296b38a0f62dd.jpg)
##### 3.带JE自定义标签的HTML
![这里写图片描述](https://oscimg.oschina.net/oscnet/7f7c504e3c545fd29bb7a3e5c269c473fc9.jpg)
##### 4.访问该HTML页面
![这里写图片描述](https://oscimg.oschina.net/oscnet/dab778e4bc44db48c89437773d5287091cd.jpg)
##### 5.对比服务端提供的JSON数据
![这里写图片描述](https://oscimg.oschina.net/oscnet/b4ead4c097c2a8191886c4b621c04c92f38.jpg)


----------
# 六：核心依赖

### Maven

```
         
         
             io.netty 
             netty-all 
             4.1.22.Final 
         
```
# 七：响应类型
响应类型非常易扩展！只需要找到此方法扩展一下即可。
```
	public void prepare() {
		if (ENUMTYPE.getType(request.getType()) == null) {
			response = response(response, request, request.getType());
			return;
		}
		switch (ENUMTYPE.getType(request.getType())) {
		case HTML:
			response = response(response, request, ENUMTYPE.HTML.getType());
			break;
		case CSS:
			response = response(response, request, ENUMTYPE.CSS.getType());
			break;
		case JS:
			response = response(response, request, ENUMTYPE.JS.getType());
			break;
		case PNG:
			response = response(response, request, ENUMTYPE.PNG.getType());
			break;
		case GIF:
			response = response(response, request, ENUMTYPE.GIF.getType());
			break;
		case ICO:
			response = response(response, request, ENUMTYPE.ICO.getType());
			break;
		case JPG:
			response = response(response, request, ENUMTYPE.JPG.getType());
			break;
		}
	}
```

## 声明：原创作品，禁止申请专利！


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)