 
	   
 
 
	 Login, so easy. 
 
 
	 
		  
	 
	 
		  
	 
	 
		  
	 
	 
		  
	 
	 
		  
	 
	 
		 
	 
	 
	    
	 
	 
		  
	 
 

 
     
         
               
               
               
               
               
               
               
               
               
               
               
               
               
               
               
         
     
     
         
               
               
               
               
               
               
               
               
               
               
               
               
               
               
               
               
         
     
      查看更多  
 

-------------------------------------------------------------------------------


JustAuth，如你所见，它仅仅是一个**第三方授权登录**的**工具类库**，它可以让我们脱离繁琐的第三方登录SDK，让登录变得**So easy!**

项目开源地址：[gitee](https://gitee.com/yadong.zhang/JustAuth) | [github](https://github.com/zhangyd-c/JustAuth)    
项目文档：[参考文档](https://docs.justauth.whnb.wang)

## 特点

废话不多说，就俩字：

1. **全**：已集成十多家第三方平台（国内外常用的基本都已包含），仍然还在持续扩展中（[开发计划](https://gitee.com/yadong.zhang/JustAuth/issues/IUGRK)）！
2. **简**：API就是奔着最简单去设计的（见后面`快速开始`），尽量让您用起来没有障碍感！

## 快速开始

- 引入依赖
```xml
 
     me.zhyd.oauth 
     JustAuth 
     1.15.5 
 
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
authRequest.authorize("state");
// 授权登录后会返回code（auth_code（仅限支付宝））、state，1.8.0版本后，可以用AuthCallback类作为回调接口的参数
// 注：JustAuth默认保存state的时效为3分钟，3分钟内未使用则会自动清除过期的state
authRequest.login(callback);
```

如下**任选一种** HTTP 工具 依赖，_项目内如果已有，请忽略_

- hutool-http

  ```xml
   
       cn.hutool 
       hutool-http 
       5.2.5 
   
  ```

- httpclient

  ```xml
   
  	 org.apache.httpcomponents 
    	 httpclient 
    	 4.5.12 
   
  ```

- okhttp

  ```xml
   
     com.squareup.okhttp3 
     okhttp 
     4.4.1 
   
  ```

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

## 贡献者名单

[contributors](https://docs.justauth.whnb.wang/#/contributors)

## 更新记录

[CHANGELOGS](https://docs.justauth.whnb.wang/#/update)

## 致谢

在项目立项初期，也对当前开源圈的一些相同类型的项目作过调研，同时本项目也参考过这些项目，再次感谢开源圈内的朋友。

- [YurunOAuthLogin](https://gitee.com/yurunsoft/YurunOAuthLogin): PHP 第三方登录授权 SDK
- [阿里妈妈MUX倾力打造的矢量图标库-iconfont](https://www.iconfont.cn/search/index): 本文档中的图标大部分取自该平台
- [mica](https://github.com/lets-mica/mica)：Spring Cloud 微服务开发核心包，支持 `web `和 `webflux`。注：JustAuth项目中的[UuidUtils](https://gitee.com/yadong.zhang/JustAuth/blob/master/src/main/java/me/zhyd/oauth/utils/UuidUtils.java)就是直接使用的mica提供的高性能的uuid创建工具类源码[StringUtil.java](https://github.com/lets-mica/mica/blob/master/mica-core/src/main/java/net/dreamlu/mica/core/utils/StringUtil.java#L335)
- 感谢 JetBrains 提供的免费开源 License：
 

   

## 开源推荐
- `spring-boot-demo` 深度学习并实战 spring boot 的项目: [https://github.com/xkcoding/spring-boot-demo](https://github.com/xkcoding/spring-boot-demo)
- `mica` SpringBoot 微服务高效开发工具集: [https://github.com/lets-mica/mica](https://github.com/lets-mica/mica)
- `pig` 宇宙最强微服务认证授权脚手架(架构师必备): [https://gitee.com/log4j/pig](https://gitee.com/log4j/pig)
- `SpringBlade` 完整的线上解决方案（企业开发必备）: https://gitee.com/smallc/SpringBlade
- `MaxKey` 马克思的钥匙，寓意是最大钥匙,是用户单点登录认证系统（Sigle Sign On System）,OAuth 2.0/OpenID Connect、SAML 2.0、JWT、CAS等标准化的开放协议，使用JustAuth集成OAuth第三方认证。: [https://shimingxy.github.io/MaxKey/](https://shimingxy.github.io/MaxKey/)

## 关注&交流

|  公众号  |  微信(备注:JustAuth)  |
| :------------: | :------------: |
|   |   |

 **QQ群** 

- JustAuth交流群 （230017570）：专业交流该项目

## 请喝咖啡

| 支付宝  | 微信  |
| :------------: | :------------: |
|   |   |

通过“[爱发电](https://afdian.net/@zhangyadong)”赞助，感谢您的支持

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)