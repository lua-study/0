 
	   
 
 
	 Login, so easy. 
 
 
	 
		  
	 
	 
		  
	 
	 
		  
	 
	 
		  
	 
	 
		 
	 
	 
	    
	 
	 
		  
	 
 

 
     
         
                 
                 
                 
                 
                 
                 
                 
                 
                 
                 
                 
                 
                 
                 
                 
         
     
     
         
                 
                 
                 
                 
                 
                 
                 
                 
                 
         
     
 

-------------------------------------------------------------------------------



JustAuth，如你所见，它仅仅是一个**第三方授权登录**的**工具类库**，它可以让我们脱离繁琐的第三方登录SDK，让登录变得**So easy!**

项目开源地址：[gitee](https://gitee.com/yadong.zhang/JustAuth) | [github](https://github.com/zhangyd-c/JustAuth)

## 特点

废话不多说，就俩字：

1. **全**：已集成十多家第三方平台（国内外常用的基本都已包含），后续依然还有扩展计划！
2. **简**：API就是奔着最简单去设计的（见后面`快速开始`），尽量让您用起来没有障碍感！

## 快速开始

- 引入依赖
```xml
 
     me.zhyd.oauth 
     JustAuth 
     1.9.5 
 
```
- 调用api
```java
// 创建授权request
AuthRequest authRequest = new AuthGiteeRequest(AuthConfig.builder()
        .clientId("clientId")
        .clientSecret("clientSecret")
        .redirectUri("redirectUri")
        .build());
// 生成授权页面
authRequest.authorize();
// 授权登录后会返回code（auth_code（仅限支付宝））、state，1.8.0版本后，可以用AuthCallback类作为回调接口的参数
// 注：JustAuth默认保存state的时效为3分钟，3分钟内未使用则会自动清除过期的state
authRequest.login(callback);
```

**配套Demo**：
- [Springboot版](https://gitee.com/yadong.zhang/JustAuth-demo)
- [jFinal版](https://github.com/xkcoding/jfinal-justauth-demo)
- [ActFramework版](https://github.com/xkcoding/act-justauth-demo)

**扩展工具**

- [justauth-spring-boot-starter](https://github.com/xkcoding/justauth-spring-boot-starter): Spring Boot 集成 JustAuth 的最佳实践

**配套SpringBoot starter**：

[justauth-spring-boot-starter](https://github.com/xkcoding/justauth-spring-boot-starter)

具体的例子可以参考：

- [实现Gitee授权登录](http://t.cn/ExDKxQs)
- [实现Github授权登录](http://t.cn/EJ0Fxqo)
- [Spring Boot 快速集成第三方登录功能](http://t.cn/AiWWx5kH)

#### API列表
|  :computer: 平台  |  :coffee: API类  |  :page_facing_up: SDK  |
|:------:|:-------:|:-------:|
|     |  [AuthGiteeRequest](https://gitee.com/yadong.zhang/JustAuth/blob/master/src/main/java/me/zhyd/oauth/request/AuthGiteeRequest.java)  |  参考文档  |
|     |  [AuthGithubRequest](https://gitee.com/yadong.zhang/JustAuth/blob/master/src/main/java/me/zhyd/oauth/request/AuthGiteeRequest.java)  |   参考文档  |
|     |  [AuthWeiboRequest](https://gitee.com/yadong.zhang/JustAuth/blob/master/src/main/java/me/zhyd/oauth/request/AuthGiteeRequest.java)  |   参考文档   |
|     |  [AuthDingTalkRequest](https://gitee.com/yadong.zhang/JustAuth/blob/master/src/main/java/me/zhyd/oauth/request/AuthDingTalkRequest.java)  |   参考文档   |
|     |  [AuthBaiduRequest](https://gitee.com/yadong.zhang/JustAuth/blob/master/src/main/java/me/zhyd/oauth/request/AuthBaiduRequest.java)  |   参考文档   |
|     |  [AuthCodingRequest](https://gitee.com/yadong.zhang/JustAuth/blob/master/src/main/java/me/zhyd/oauth/request/AuthCodingRequest.java)  |   参考文档  |
|     |  [AuthTencentCloudRequest](https://gitee.com/yadong.zhang/JustAuth/blob/master/src/main/java/me/zhyd/oauth/request/AuthTencentCloudRequest.java)  |   参考文档  |
|     |  [AuthOschinaRequest](https://gitee.com/yadong.zhang/JustAuth/blob/master/src/main/java/me/zhyd/oauth/request/AuthOschinaRequest.java)  |   参考文档  |
|     |  [AuthAlipayRequest](https://gitee.com/yadong.zhang/JustAuth/blob/master/src/main/java/me/zhyd/oauth/request/AuthAlipayRequest.java)  |   参考文档  |
|     |  [AuthQqRequest](https://gitee.com/yadong.zhang/JustAuth/blob/master/src/main/java/me/zhyd/oauth/request/AuthQqRequest.java)  |   参考文档   |
|     |  [AuthWeChatRequest](https://gitee.com/yadong.zhang/JustAuth/blob/master/src/main/java/me/zhyd/oauth/request/AuthWeChatRequest.java)   |   参考文档   |
|     |  [AuthTaobaoRequest](https://gitee.com/yadong.zhang/JustAuth/blob/master/src/main/java/me/zhyd/oauth/request/AuthTaobaoRequest.java)   |   参考文档   |
|     |  [AuthGoogleRequest](https://gitee.com/yadong.zhang/JustAuth/blob/master/src/main/java/me/zhyd/oauth/request/AuthGoogleRequest.java)   |   参考文档   |
|     |  [AuthFacebookRequest](https://gitee.com/yadong.zhang/JustAuth/blob/master/src/main/java/me/zhyd/oauth/request/AuthFacebookRequest.java)   |   参考文档   |
|     |  [AuthDouyinRequest](https://gitee.com/yadong.zhang/JustAuth/blob/master/src/main/java/me/zhyd/oauth/request/AuthDouyinRequest.java)   |   参考文档   |
|     |  [AuthLinkedinRequest](https://gitee.com/yadong.zhang/JustAuth/blob/master/src/main/java/me/zhyd/oauth/request/AuthLinkedinRequest.java)   |   参考文档   |
|     | [AuthMicrosoftRequest](https://gitee.com/yadong.zhang/JustAuth/blob/master/src/main/java/me/zhyd/oauth/request/AuthMicrosoftRequest.java) |  参考文档  |
|     | [AuthMiRequest](https://gitee.com/yadong.zhang/JustAuth/blob/master/src/main/java/me/zhyd/oauth/request/AuthMiRequest.java) |  参考文档  |
|     | [AuthToutiaoRequest](https://gitee.com/yadong.zhang/JustAuth/blob/master/src/main/java/me/zhyd/oauth/request/AuthToutiaoRequest.java) |  参考文档  |
|     | [AuthTeambitionRequest](https://gitee.com/yadong.zhang/JustAuth/blob/master/src/main/java/me/zhyd/oauth/request/AuthTeambitionRequest.java) |  参考文档  |
|     | [AuthRenrenRequest](https://gitee.com/yadong.zhang/JustAuth/blob/master/src/main/java/me/zhyd/oauth/request/AuthRenrenRequest.java) |  参考文档  |
|     | [AuthPinterestRequest](https://gitee.com/yadong.zhang/JustAuth/blob/master/src/main/java/me/zhyd/oauth/request/AuthPinterestRequest.java) |  参考文档  |
|     | [AuthStackOverflowRequest](https://gitee.com/yadong.zhang/JustAuth/blob/master/src/main/java/me/zhyd/oauth/request/AuthStackOverflowRequest.java) |  参考文档  |
|     |  [AuthCsdnRequest](https://gitee.com/yadong.zhang/JustAuth/blob/master/src/main/java/me/zhyd/oauth/request/AuthCsdnRequest.java)  |  无 |

_请知悉：经咨询CSDN官方客服得知，CSDN的授权开放平台已经下线。如果以前申请过的应用，可以继续使用，但是不再支持申请新的应用。so, 本项目中的CSDN登录只能针对少部分用户使用了_

## 后续开发计划

参考：[[开发计划] 待扩展的第三方平台](https://gitee.com/yadong.zhang/JustAuth/issues/IUGRK)

另外，期待您和我一起完善这个项目！

## 贡献代码

1. fork本项目到自己的repo
2. 把fork过去的项目也就是你仓库中的项目clone到你的本地
3. 修改代码
4. commit后push到自己的库
5. 发起PR（pull request） 请求，提交到`dev`分支
6. 等待作者合并

## 致谢

在项目立项初期，也对当前开源圈的一些相同类型的项目作过调研，同时本项目也参考过这些项目，再次感谢开源圈内的朋友。

[YurunOAuthLogin](https://gitee.com/yurunsoft/YurunOAuthLogin): PHP 第三方登录授权 SDK

[阿里妈妈MUX倾力打造的矢量图标库-iconfont](https://www.iconfont.cn/search/index): 本文档中的图标大部分取自该平台

[mica](https://github.com/lets-mica/mica)：Spring Cloud 微服务开发核心包，支持 `web `和 `webflux`。注：JustAuth项目中的[UuidUtils](https://gitee.com/yadong.zhang/JustAuth/blob/master/src/main/java/me/zhyd/oauth/utils/UuidUtils.java)就是直接使用的mica提供的高性能的uuid创建工具类源码[StringUtil.java](https://github.com/lets-mica/mica/blob/master/mica-core/src/main/java/net/dreamlu/mica/core/utils/StringUtil.java#L335)

## 关于OAuth

[The OAuth 2.0 Authorization Framework](https://tools.ietf.org/html/rfc6749)

## 关注&交流

|  公众号  |  微信(备注:加群)  |
| :------------: | :------------: |
|   |   |

 **QQ群** 

- JustAuth交流群 （230017570）：专业交流该项目

- 开源总群 （190886500）：各个开源项目的都有，也有博客建设等方面的朋友。（注意，该群需付费进入，防止发垃圾广告、垃圾推广等人士）


## 请喝咖啡

| 支付宝  | 微信  |
| :------------: | :------------: |
|   |   |


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)