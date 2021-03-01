# hm-tools-wxmp-adapter

[![996.icu](https://img.shields.io/badge/link-996.icu-red.svg)](https://996.icu)
[![Maven Central](https://img.shields.io/maven-central/v/top.hmtools/hm-tools-wxmp-adapter.svg?label=Maven%20Central)](https://search.maven.org/search?q=g:%22top.hmtools%22%20AND%20a:%22hm-tools-wxmp-adapter%22)

#### 前言
同微信服务器交互，是以http方式交互，总体为主动请求微信服务器获取反馈数据、被动接收微信服务器发送的数据并处理之后反馈数据至微信服务器。即：
- 主动请求微信服务器
	- get方式
	  - 获取的数据类型为json
	  - 获取的数据类型为 字节流（比如素材管理中的获取图片素材接口）
	- post方式
	  - 请求参数数据类型为json，获取反馈的数据类型为json
	  - 请求参数数据类型为form表单，获取反馈的数据类型为json （比如素材管理中上传图片素材接口）
- 被动接收微信服务器的请求，接收到的数据类型均为xml  
  
关于微信接口收发数据类型分析可参照[微信公众号接口分析.xlsx](documents/微信公众号接口分析.xlsx)

#### 介绍
对微信公众号API接口的封装，官方API文档地址：[https://mp.weixin.qq.com/wiki](https://mp.weixin.qq.com/wiki)  
**封装微信接口过程是极度辛苦的，因为腾讯的文档总是写的不明不白，客服也总是联系不上！~**    
本工具包，参照并借鉴了mybatis、spring MVC的一些设计思路，故使用起来会有熟悉的感觉~

#### 架构说明
- `/hm-tools-wxmp-adapter/wxmp-core`		本工具包的核心，主要实现 accessToken 的获取、管理、缓存、扩展（自定义分布式方案等），http方式请求微信服务器，基础的数据类型，Javabean与xml的相互转换工具
- `/hm-tools-wxmp-adapter/wxmp-menu`		自定义菜单相关api接口、请求/响应数据结构以及事件通知数据结构封装。对应微信公众号开发文档“[自定义菜单](https://mp.weixin.qq.com/wiki?t=resource/res_main&id=mp1434698695)”章节。
- `/hm-tools-wxmp-adapter/wxmp-message`			消息管理相关api接口、请求/响应数据结构以及事件通知数据结构封装。对应微信公众号开发文档“[消息管理](https://developers.weixin.qq.com/doc/offiaccount/Message_Management/Receiving_standard_messages.html)”章节。
- `/hm-tools-wxmp-adapter/wxmp-webpage`			微信网页开发相关接口，对应微信对应微信公众号开发文档“[微信网页开发](https://developers.weixin.qq.com/doc/offiaccount/OA_Web_Apps/iOS_WKWebview.html)”章节。
- `/hm-tools-wxmp-adapter/wxmp-material`			素材管理相关api接口、请求/响应数据结构封装。对应微信对应微信公众号开发文档“[素材管理](https://developers.weixin.qq.com/doc/offiaccount/Asset_Management/New_temporary_materials.html)”章节
- `/hm-tools-wxmp-adapter/wxmp-comment`			图文消息管理相关api接口、请求/响应数据结构封装。对应微信对应微信公众号开发文档“[图文消息管理](https://developers.weixin.qq.com/doc/offiaccount/Comments_management/Image_Comments_Management_Interface.html)”章节
- `/hm-tools-wxmp-adapter/wxmp-user`			用户管理相关api接口、请求/响应数据结构封装。对应微信对应微信公众号开发文档“[用户管理](https://developers.weixin.qq.com/doc/offiaccount/User_Management/User_Tag_Management.html)”章节
- `/hm-tools-wxmp-adapter/wxmp-account`			账号管理相关api接口、请求/响应数据结构封装。对应微信对应微信公众号开发文档“[账号管理](https://developers.weixin.qq.com/doc/offiaccount/Account_Management/Generating_a_Parametric_QR_Code.html)”章节

#### 封装进度
[查看封装进度](接口封装进展.md)

#### 使用说明
###### maven parent 引用
```
 
     top.hmtools 
     hm-tools-wxmp-adapter 
     1.0.0 
 
```

###### 最基础的使用方式
//以获取自定义菜单为例

//引用所需要的jar包（本工具包完全对标微信公众号文档分类，按需引用jar包即可）
```
 
   top.hmtools 
   wxmp-menu 
   1.0.0 
 
```

```
//初始化全局所使用的配置文件对象实例
WxmpConfiguration configuration = new WxmpConfiguration();
		
//设置 存储appid，appsecret 数据对 的盒子
AppIdSecretBox appIdSecretBox = new AppIdSecretBox() {
	
	@Override
	public AppIdSecretPair getAppIdSecretPair() {
		AppIdSecretPair appIdSecretPair = new AppIdSecretPair();
		appIdSecretPair.setAppid("你的微信公众号appid");
		appIdSecretPair.setAppsecret("你的微信公众号secret");
		return appIdSecretPair;
	}
};

//设置 获取access token 的中间件
DefaultAccessTokenHandle accessTokenHandle = new DefaultAccessTokenHandle(appIdSecretBox);
configuration.setAccessTokenHandle(accessTokenHandle);

//获取session创建工厂
WxmpSessionFactory factory = WxmpSessionFactoryBuilder.build(configuration);

//获取会话
WxmpSession wxmpSession = factory.openSession();

//获取被动态代理后的api mapper 对象实例
IMenuApi menuApi = wxmpSession.getMapper(IMenuApi.class);	

//执行请求，获取反馈结果并打印
MenuWapperBean menu = menuApi.getMenu();
System.out.println(JSON.toJSONString(menu));
```
打印的内容是：
```
{
    "menu": {
        "button": [
            {
                "name": "哈哈",
                "sub_button": [
                    {
                        "name": "官网",
                        "sub_button": [],
                        "type": "view",
                        "url": "http://m.hybo.net/main/index/index.html"
                    },
                    {
                        "name": "动态",
                        "sub_button": [],
                        "type": "view",
                        "url": "http://hm.hn.cn/main/news/index.html"
                    },
                    {
                        "name": "视频",
                        "sub_button": [],
                        "type": "view",
                        "url": "http://hm.hn.cn/main/news/video.html"
                    }
                ]
            }
        ]
    }
}
```

###### 优雅一点的使用方式
`TODO` 

###### 整合spring boot
参照：[wxmp-server-demo](wxmp-server-demo)

#### 各子组件使用说明
- [核心包](wxmp-core/readme.md)
- [自定义菜单](wxmp-menu/readme.md)
- [消息管理](wxmp-message/readme.md)
- [微信网页开发](wxmp-webpage/readme.md)
- [素材管理](wxmp-material/readme.md)
- [图文消息留言管理](wxmp-comment/readme.md)
- [用户管理](wxmp-user/readme.md)
- [账号管理](wxmp-account/readme.md)


#### 如何使用本组件的快照版本

1. 在自己的私服建立一个快照代理仓库即可。https://oss.sonatype.org/content/repositories/snapshots/
![如何使用快照版本](/images/howToUseSnapshot.jpg)

2. 将建好的参考纳入公共库
![如何使用快照版本](/images/howToUseSnapshot-2.jpg)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)