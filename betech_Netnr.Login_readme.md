# Netnr.Login
> 第三方OAuth授权快捷登录（QQ、微信、微博、GitHub、淘宝/天猫、Microsoft）

### 支持第三方登录
- QQ
- 微信
- 微博
- GitHub
- 淘宝（天猫）
- Microsoft

----------
> 如果该项目对你有帮助，请你为项目Star，谢谢，这是对我精神上的支持，也是能一直坚持下去的动力。

----------
### [更新日志](CHANGELOG.md)

----------
### 安装 (NuGet)
```
Install-Package Netnr.Login
```
修改配置信息（密钥、回调等）

### 框架
- .NETStandard 2.0
- .NETFramework 4.0

### Code
```csharp
using System;

namespace Netnr.Login.Sample
{
    public class Demo
    {
        public Demo()
        {
            // 配置
            QQConfig.APPID = "101511xxx";
            QQConfig.APPKey = "f26b4af4a9d68bec2bbcbeee443fexxx";
            //回调地址，与申请填写的地址保持一致
            QQConfig.Redirect_Uri = "https://rf2.netnr.com/account/authcallback/qq";

            WeChatConfig.AppId = "";
            WeChatConfig.AppSecret = "";
            WeChatConfig.Redirect_Uri = "";

            WeiboConfig.AppKey = "";
            WeiboConfig.AppSecret = "";
            WeiboConfig.Redirect_Uri = "";

            GitHubConfig.ClientID = "";
            GitHubConfig.ClientSecret = "";
            GitHubConfig.Redirect_Uri = "https://rf2.netnr.com/account/authcallback/github";
            //申请的应用名称，非常重要
            GitHubConfig.ApplicationName = "netnrf";

            TaobaoConfig.AppKey = "";
            TaobaoConfig.AppSecret = "";
            TaobaoConfig.Redirect_Uri = "";

            MicroSoftConfig.ClientID = "";
            MicroSoftConfig.ClientSecret = "";
            MicroSoftConfig.Redirect_Uri = "";
        }

        ///  
        /// 生成请求链接
        ///  
        ///   
        public string Auth(LoginBase.LoginType loginType)
        {
            var url = string.Empty;

            switch (loginType)
            {
                case LoginBase.LoginType.QQ:
                    url = QQ.AuthorizationHref(new QQ_Authorization_RequestEntity());
                    break;
                case LoginBase.LoginType.WeiBo:
                    url = Weibo.AuthorizeHref(new Weibo_Authorize_RequestEntity());
                    break;
                case LoginBase.LoginType.WeChat:
                    url = WeChat.AuthorizationHref(new WeChat_Authorization_RequestEntity());
                    break;
                case LoginBase.LoginType.GitHub:
                    url = GitHub.AuthorizeHref(new GitHub_Authorize_RequestEntity());
                    break;
                case LoginBase.LoginType.TaoBao:
                    url = Taobao.AuthorizeHref(new Taobao_Authorize_RequestEntity());
                    break;
                case LoginBase.LoginType.MicroSoft:
                    url = MicroSoft.AuthorizeHref(new MicroSoft_Authorize_RequestEntity());
                    break;
                default:
                    break;
            }

            return url;
        }

        ///  
        /// 回调方法
        ///  
        ///  请求链接得到的code 
        ///  登录类型 
        public void AuthCallback(string code, LoginBase.LoginType loginType)
        {
            //唯一标示
            string openId = string.Empty;

            switch (loginType)
            {
                case LoginBase.LoginType.QQ:
                    {
                        //获取 access_token
                        var tokenEntity = QQ.AccessToken(new QQ_AccessToken_RequestEntity()
                        {
                            code = code
                        });

                        //获取 OpendId
                        var openidEntity = QQ.OpenId(new QQ_OpenId_RequestEntity()
                        {
                            access_token = tokenEntity.access_token
                        });

                        //获取 UserInfo
                        var userEntity = QQ.OpenId_Get_User_Info(new QQ_OpenAPI_RequestEntity()
                        {
                            access_token = tokenEntity.access_token,
                            openid = openidEntity.openid
                        });

                        //身份唯一标识
                        openId = openidEntity.openid;
                    }
                    break;
                case LoginBase.LoginType.WeiBo:
                    {
                        //获取 access_token
                        var tokenEntity = Weibo.AccessToken(new Weibo_AccessToken_RequestEntity()
                        {
                            code = code
                        });

                        //获取 access_token 的授权信息
                        var tokenInfoEntity = Weibo.GetTokenInfo(new Weibo_GetTokenInfo_RequestEntity()
                        {
                            access_token = tokenEntity.access_token
                        });

                        //获取 users/show
                        var userEntity = Weibo.UserShow(new Weibo_UserShow_RequestEntity()
                        {
                            access_token = tokenEntity.access_token,
                            uid = Convert.ToInt64(tokenInfoEntity.uid)
                        });

                        openId = tokenEntity.access_token;
                    }
                    break;
                case LoginBase.LoginType.WeChat:
                    {
                        //获取 access_token
                        var tokenEntity = WeChat.AccessToken(new WeChat_AccessToken_RequestEntity()
                        {
                            code = code
                        });

                        //获取 user
                        var userEntity = WeChat.Get_User_Info(new WeChat_OpenAPI_RequestEntity()
                        {
                            access_token = tokenEntity.access_token,
                            openid = tokenEntity.openid
                        });

                        //身份唯一标识
                        openId = tokenEntity.openid;
                    }
                    break;
                case LoginBase.LoginType.GitHub:
                    {
                        //申请的应用名称，非常重要
                        GitHubConfig.ApplicationName = "netnrf";

                        //获取 access_token
                        var tokenEntity = GitHub.AccessToken(new GitHub_AccessToken_RequestEntity()
                        {
                            code = code
                        });

                        //获取 user
                        var userEntity = GitHub.User(new GitHub_User_RequestEntity()
                        {
                            access_token = tokenEntity.access_token
                        });

                        openId = userEntity.id.ToString();
                    }
                    break;
                case LoginBase.LoginType.TaoBao:
                    {
                        //获取 access_token
                        var tokenEntity = Taobao.AccessToken(new Taobao_AccessToken_RequestEntity()
                        {
                            code = code
                        });

                        openId = tokenEntity.open_uid;
                    }
                    break;
                case LoginBase.LoginType.MicroSoft:
                    {
                        //获取 access_token
                        var tokenEntity = MicroSoft.AccessToken(new MicroSoft_AccessToken_RequestEntity()
                        {
                            code = code
                        });

                        //获取 user
                        var userEntity = MicroSoft.User(new MicroSoft_User_RequestEntity()
                        {
                            access_token = tokenEntity.access_token
                        });

                        openId = userEntity.id.ToString();
                    }
                    break;
            }

            //拿到登录标识
            if (string.IsNullOrWhiteSpace(openId))
            {
                //TO DO
            }
        }
    }
}
```

### Source
-  
-  

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)