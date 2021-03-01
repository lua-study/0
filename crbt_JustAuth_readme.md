 
	   
 
 
	 Login, so easy. 
 
 
	 
		  
	 
	 
		  
	 
	 
		  
	 
 

 
     
         
             
                     
                     
                     
                     
                     
                     
                     
                     
                     
                     
                     
             
         
         
             
                  Gitee  
                  Github  
                  Weibo  
                  钉钉  
                  百度  
                  CSDN  
                  Coding  
                  腾讯云开发者平台  
                  OSChina  
                  QQ  
                  微信  
             
         
     
 

-------------------------------------------------------------------------------



JustAuth，如你所见，它仅仅是一个**第三方授权登录**的**工具类库**，它可以让我们脱离繁琐的第三方登录SDK，让登录变得**So easy!**

## 快速开始
- 引入依赖
```xml
 
     me.zhyd.oauth 
     JustAuth 
     1.0.0 
 
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
// 授权登录后会返回一个code，用这个code进行登录
authRequest.login("code");
```

具体的例子可以参考：[实现Gitee授权登录](http://t.cn/ExDKxQs)

#### API列表
|  :computer: 平台  |  :coffee: API类  |  :page_facing_up: SDK  |
|:------:|:-------:|:-------:|
|     |  [AuthGiteeRequest](https://gitee.com/yadong.zhang/JustAuth/blob/master/src/main/java/me/zhyd/oauth/request/AuthGiteeRequest.java)  |  参考文档  |
|     |  [AuthGithubRequest](https://gitee.com/yadong.zhang/JustAuth/blob/master/src/main/java/me/zhyd/oauth/request/AuthGiteeRequest.java)  |   参考文档  |
|     |  [AuthWeiboRequest](https://gitee.com/yadong.zhang/JustAuth/blob/master/src/main/java/me/zhyd/oauth/request/AuthGiteeRequest.java)  |   参考文档   |
|     |  [AuthDingTalkRequest](https://gitee.com/yadong.zhang/JustAuth/blob/master/src/main/java/me/zhyd/oauth/request/AuthDingTalkRequest.java)  |   参考文档   |
|     |  [AuthBaiduRequest](https://gitee.com/yadong.zhang/JustAuth/blob/master/src/main/java/me/zhyd/oauth/request/AuthBaiduRequest.java)  |   参考文档   |
|     |  [AuthCsdnRequest](https://gitee.com/yadong.zhang/JustAuth/blob/master/src/main/java/me/zhyd/oauth/request/AuthCsdnRequest.java)  |  待续 |
|     |  [AuthCodingRequest](https://gitee.com/yadong.zhang/JustAuth/blob/master/src/main/java/me/zhyd/oauth/request/AuthCodingRequest.java)  |   参考文档  |
|     |  [AuthTencentCloudRequest](https://gitee.com/yadong.zhang/JustAuth/blob/master/src/main/java/me/zhyd/oauth/request/AuthTencentCloudRequest.java)  |   参考文档  |
|     |  [AuthOschinaRequest](https://gitee.com/yadong.zhang/JustAuth/blob/master/src/main/java/me/zhyd/oauth/request/AuthOschinaRequest.java)  |   参考文档  |
|     |  AuthQqRequest  |   参考文档   |
|     |  AuthWechatRequest  |  待续  |

### 参考图例

#### 授权gitee

![Gitee授权登录](https://images.gitee.com/uploads/images/2019/0221/140015_4c09610e_784199.png "Gitee授权登录")

#### 授权github

![Github授权登录](https://images.gitee.com/uploads/images/2019/0221/140032_58f7dfb5_784199.png "Github授权登录")

#### 授权weibo

![微博授权登录](https://images.gitee.com/uploads/images/2019/0222/191210_67d5597c_784199.png "微博授权登录")

#### 授权钉钉

![钉钉授权登录](https://images.gitee.com/uploads/images/2019/0221/140540_8da8d959_784199.jpeg "钉钉授权登录")

#### 授权百度

![百度授权登录](https://images.gitee.com/uploads/images/2019/0221/140607_ebf1dcb6_784199.png "百度授权登录")

#### 授权csdn

待续

#### 授权coding

![Coding授权登录](https://images.gitee.com/uploads/images/2019/0224/192106_fd53b3d7_784199.png "Coding授权登录")

#### 授权腾讯云开发者平台

![腾讯云开发者平台授权登录](https://images.gitee.com/uploads/images/2019/0224/192128_db9e203b_784199.png "腾讯云开发者平台授权登录")

#### 授权oschina

![授权oschina登录](https://images.gitee.com/uploads/images/2019/0322/230652_05b4fd8a_784199.png "授权oschina")

#### 授权qq

待续

#### 授权微信

待续

## 更多链接

[gitee](https://gitee.com/yadong.zhang/JustAuth)

[github](https://github.com/zhangyd-c/JustAuth)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)