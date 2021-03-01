 
	   
 
 
	 Login-OAuth2, so easy. 
 
 
	 
		  
	 
	 
		  
	 
	 
		  
	 
	 
	    
	 
 

 
     
         
               
               
               
               
               
               
               
               
               
               
               
               
               
               
               
         
     
     
         
               
               
               
               
               
               
               
               
               
               
               
               
               
               
               
               
         
     
      查看更多  
 

-------------------------------------------------------------------------------

## 特别感谢
**JustAuth**：这里特别感谢JustAuth开源项目作者提供架构思路(特别是Readme大部分来自于JustAuth，本人比较懒)


.Net平台下 **CollectiveOAuth**，它仅仅是一个 **第三方授权登录**的**工具类库**，它可以让我们脱离繁琐的第三方登录SDK，让登录变得**So easy!**

- 项目开源地址：[gitee](https://gitee.com/rthinking/CollectiveOAuth) 
- 项目文档：[参考文档(暂未开放)]

## 特点

废话不多说，就俩字：

1. **全**：已集成十多家第三方平台（国内外常用的基本都已包含），仍然还在持续扩展中（[开发计划(制作中)]！
2. **简**：API就是奔着最简单去设计的（见后面`快速开始`），尽量让您用起来没有障碍感！

## 快速开始

- 引入依赖
  

- 配置授权信息(默认配置在webconfig中, 可以改造存储数据库或者其它任意地方)
```C#
 
 
 
 
 
```

- 调用api
```C#
// 创建授权request
var clientConfig = new ClientConfig();
clientConfig.clientId = AppSettingUtils.GetStrValue($"CollectiveOAuth_XXXXXX_ClientId");
clientConfig.clientSecret = AppSettingUtils.GetStrValue($"CollectiveOAuth_XXXXXX_ClientSecret");
clientConfig.redirectUri = AppSettingUtils.GetStrValue($"CollectiveOAuth_XXXXXX_RedirectUri");
clientConfig.scope = AppSettingUtils.GetStrValue($"CollectiveOAuth_XXXXXX_Scope");

AuthRequest authRequest = new GiteeAuthRequest(clientConfig);
// 生成授权页面
authRequest.authorize("state");
// 授权登录后会返回code（auth_code（仅限支付宝））、state，可以用AuthCallback类作为回调接口的参数
// 注：CollectiveOAuth默认保存state的时效为5分钟，5分钟内未使用则会自动清除过期的state
authRequest.login(callback);
```

#### API列表
|  :computer: 平台  |  :coffee: API类  |  :page_facing_up: SDK  |
|:------:|:-------:|:-------:|
|     |  [GiteeAuthSource](https://gitee.com/rthinking/CollectiveOAuth/blob/master/Come.CollectiveOAuth/Request/AuthRequests/GiteeAuthRequest.cs)  |  参考文档  |
|     |  [GithubAuthRequest](https://gitee.com/rthinking/CollectiveOAuth/blob/master/Come.CollectiveOAuth/Request/AuthRequests/GithubAuthRequest.cs)  |   参考文档  |
|     |  [WeiboAuthRequest] |   参考文档   |
|     |  [DingTalkScanAuthRequest](https://gitee.com/rthinking/CollectiveOAuth/blob/master/Come.CollectiveOAuth/Request/AuthRequests/DingTalkScanAuthRequest.cs)  |   参考文档   |
|     |  [BaiduAuthRequest](https://gitee.com/rthinking/CollectiveOAuth/blob/master/Come.CollectiveOAuth/Request/AuthRequests/BaiduAuthRequest.cs)  |   参考文档   |
|     |  [CodingAuthRequest](https://gitee.com/rthinking/CollectiveOAuth/blob/master/Come.CollectiveOAuth/Request/AuthRequests/CodingAuthRequest.cs) |   参考文档  |
|     |  [AuthTencentCloudRequest] |   参考文档  |
|     |  [OschinaAuthRequest](https://gitee.com/rthinking/CollectiveOAuth/blob/master/Come.CollectiveOAuth/Request/AuthRequests/OschinaAuthRequest.cs) |   参考文档  |
|     |  [AlipayMPAuthRequest](https://gitee.com/rthinking/CollectiveOAuth/blob/master/Come.CollectiveOAuth/Request/AuthRequests/AlipayMpAuthRequest.cs)  |   参考文档  |
|     |  [AuthQqRequest]  |   参考文档   |
|     |  [WeChatOpenAuthRequest] |   参考文档   |
|    | [WeChatMPAuthRequest](https://gitee.com/rthinking/CollectiveOAuth/blob/master/Come.CollectiveOAuth/Request/AuthRequests/WeChatMpAuthRequest.cs) |  参考文档  |
|     | [WeChatEnterpriseAuthRequest](https://gitee.com/rthinking/CollectiveOAuth/blob/master/Come.CollectiveOAuth/Request/AuthRequests/WeChatEnterpriseAuthRequest.cs) |  参考文档  |
|     | [WeChatEnterpriseScanAuthRequest](https://gitee.com/rthinking/CollectiveOAuth/blob/master/Come.CollectiveOAuth/Request/AuthRequests/WeChatEnterpriseScanAuthRequest.cs) |  参考文档  |
|     |  [TaobaoAuthRequest]  |   参考文档   |
|     |  [GoogleAuthRequest]  |   参考文档   |
|     |  [FacebookAuthRequest]  |   参考文档   |
|     |  [DouyinAuthRequest]  |   参考文档   |
|     |  [LinkedInAuthRequest](https://gitee.com/rthinking/CollectiveOAuth/blob/master/Come.CollectiveOAuth/Request/AuthRequests/LinkedinAuthRequest.cs)  |   参考文档   |
|     | [MicrosoftAuthRequest]  |  参考文档  |
|     | [XiaoMiAuthRequest] |  参考文档  |
|     | [ToutiaoAuthRequest] |  参考文档  |
|     | [TeambitionAuthRequest] |  参考文档  |
|     | [RenrenAuthRequest] |  参考文档  |
|     | [PinterestAuthRequest] |  参考文档  |
|     | [StackOverflowAuthRequest] |  参考文档  |
|     | [HuaweiAuthRequest] |  参考文档  |
|     |  [KujialeAuthRequest]  |   参考文档  |
|     |  [GitlabAuthRequest] |   参考文档  |
|     |  [MeituanAuthRequest]  |   参考文档  |
|     |  [ElemeAuthRequest]  |   参考文档  |
|     |  [TwitterAuthRequest]  |   参考文档  |

_请知悉：经咨询CSDN官方客服得知，CSDN的授权开放平台已经下线。如果以前申请过的应用，可以继续使用，但是不再支持申请新的应用。

## 后续开发计划
正在筹备中

另外，期待.Net大牛和我一起完善这个项目！

## 贡献代码

1. fork本项目到自己的repo
2. 把fork过去的项目也就是你仓库中的项目clone到你的本地
3. 修改代码
4. commit后push到自己的库
5. 发起PR（pull request） 请求，提交到`dev`分支
6. 等待作者合并

## 致谢

在项目立项初期，也对当前开源圈的一些相同类型的项目作过调研，同时本项目也参考过这些项目，再次感谢开源圈内的朋友。

- [JustAuth](https://gitee.com/yadong.zhang/JustAuth): Java 第三方登录授权 SDK
- [YurunOAuthLogin](https://gitee.com/yurunsoft/YurunOAuthLogin): PHP 第三方登录授权 SDK
- [阿里妈妈MUX倾力打造的矢量图标库-iconfont](https://www.iconfont.cn/search/index): 本文档中的图标大部分取自该平台
- 感谢 JetBrains 提供的免费开源 License：
 


## 关于OAuth

- [The OAuth 2.0 Authorization Framework](https://tools.ietf.org/html/rfc6749)
- [OAuth 2.0](https://oauth.net/2/)

## 关注&交流

|  公众号  |  QQ群  |
| :------------: | :------------: |
|   |   |

 **QQ群** 

- CollectiveOAuth交流群 （836803890）：专业交流该项目

## 请喝咖啡

| 支付宝  | 微信  |
| :------------: | :------------: |
|   |   |

开源不求盈利，多少都是心意，生活不易，随缘随缘……


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)