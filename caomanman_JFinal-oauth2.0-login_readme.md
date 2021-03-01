##对第三方登陆的基础封装
集成`qq`、`sina`、`baidu`、`renren`、`osc`、`豆瓣` 等，第三方登陆api！

并非只有`jfinal`中可以使用

也可用户其他构架中！具体可参看Test.java测试

`注意` ·oauth.properties· 中含有我的网站的appkey可用来测试

测试时先更改`hosts`（具体可以`google`）
```
127.0.0.1 www.dreamlu.net
```

测试过程为

1. 调用`getAuthorizeUrl()`获取`url`,在浏览器访问url，拿到回调的`code`参数

2. 调用`getUserInfoByCode()`传入刚获取的`code`！

有不明白的可以联系本人，QQ:596392912

# JFinal 中使用示例 

## 跳转去授权
```java
//OAuth2.0标准协议建议，利用state参数来防止CSRF攻击。可存储于session或其他cache中
private static final String SESSION_STATE = "_SESSION_STATE_QQ_";

/**
 * 构造授权请求url
 * @param     设定文件
 * @return void    返回类型
 * @throws
 */
public void index() {
    try {
        String state = TokenUtil.randomState();
        setSessionAttr(SESSION_STATE, state);
        redirect(OauthQQ.me().getAuthorizeUrl(state));
    } catch (Exception e) {
        log.error(e.getMessage());
        redirect("/");
    }
}
```

## 回调可供参考
```java
/**
 * 腾讯回调
 * @Title: callback
 * @param     设定文件
 * @return void    返回类型
 * @throws
 * 返回json: http://wiki.connect.qq.com/get_user_info 
 */
public void callback() {
    String code = getPara("code");
    String state = getPara("state");
    String session_state = getSessionAttr(SESSION_STATE);
    // 取消了授权
    if (StringKit.isBlank(state) || StringKit.isBlank(session_state) || !state.equals(session_state) || StringKit.isBlank(code)) {
        redirect("/admin");
        return;
    }
    removeSessionAttr(SESSION_STATE);
    try{
        JSONObject userInfo = OauthQQ.me().getUserInfoByCode(code);
        log.error(userInfo);
        String type = "qq";
        String openid = userInfo.getString("openid");
        String nickname = userInfo.getString("nickname");
        String photoUrl = userInfo.getString("figureurl_2");
        // 将相关信息存储数据库...
    }catch(Exception e){
        log.error(e);
    }
    redirect("/admin");
}
```

## 注意事项
申请期间可以添加`测试账号`

为了快速的申请通过，请使用QQ官方的最大的那个（图标素材）


## 捐助共勉
 
 
 

 
 


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)