### 一、简介
>基于Java简化微信公众号的开发，本项目几乎封装了所有的开发内容，如：消息关系、菜单管理、用户管理、网页授权等.

### 二、使用
#### 1、创建菜单
- 在`menu-test.json`中写上待创建的菜单内容，菜单项的授权认证url可以调用`ClientTest.getAuthorizeBaseUrl()`获得；
- 调用`WeChatClient.main()`即可创建菜单；
#### 2、二次封装
>本项目只是基础包，其中是不包含公众号的`AppId和Secret`，如果要在自己项目中使用，需要继承本项目的`AbstractWeChatClient`进行二次封装；

**示例：**
```java
/**
 * Created by hoaven on 2017/3/25.
 */
@Slf4j
@Component
public class AliAdminWechatClient extends AbstractWeChatClient implements ApplicationListener  {
    @Resource
    AliAdminConfigService aliAdminConfigService;
    @Resource
    RedisTemplate  kvLockTemplate;

//    private final String accessTokenKey = "aliadmin_new_accessToken";


    @Override
    protected String getAccessToken() {
        String accessTokenKey = aliAdminConfigService.getString("weixin.access.token.redis.key","aliadmin_test_accessToken");
        return kvLockTemplate.opsForValue().get(accessTokenKey);
    }

    @Override
    public String getAppId() {
        return aliAdminConfigService.getString("weixin.app.id", "");
    }

    @Override
    public String getSecret() {
        return aliAdminConfigService.getString("weixin.secret", "");
    }

    public String getEncodingAesKey() {
        return aliAdminConfigService.getString("weixin.encodingAesKey", "");
    }

    @Override
    public void onApplicationEvent(ContextRefreshedEvent event) {
        if (event.getApplicationContext().getParent() == null) {
            this.refreshAccessToken();
        }
    }

    public void refreshAccessToken() {
        String accessTokenKey = aliAdminConfigService.getString("weixin.access.token.redis.key","aliadmin_test_accessToken");
        boolean shouldRefreshAccessToken = false;
        String token = getAccessToken();
        if (token != null) {
            Long expireIn = kvLockTemplate.getExpire(accessTokenKey);
            if (expireIn   供未绑定微信时登录使用
            request.getSession().setAttribute(SESSION_OPEN_ID, openId);

            //检查有没有获取过用户信息
            List  wechatAuthList = aliAdminBaseService.listQueryBySQL(String.format("openId = '%s'", openId), WechatAuth.class);
            if (wechatAuthList == null || wechatAuthList.size() == 0) {
                WeChatUserInfo weChatUserInfo = aliAdminWechatClient.getWeChatSubscribeUserInfo(openId);
                WechatAuth wechatAuth = convertToWechatAuth(weChatUserInfo);
                aliAdminBaseService.insert(wechatAuth);

                return "redirect:" + domain + loginUrl;
            }

            //检查有没有建立openId--userId关联
            List  userWechatList = aliAdminBaseService.listQueryBySQL(String.format("openId = '%s'", openId), UserWechat.class);
            if (userWechatList == null || userWechatList.size() == 0) {
                return "redirect:" + domain + loginUrl;
            }

            Long userId = userWechatList.get(0).getUserId();
            List  userList = aliAdminBaseService.listQueryBySQL(String.format("id = %d", userId), User.class);
            if (userList == null || userList.size() == 0) {
                //脏数据
                return "redirect:" + domain + loginUrl;
            }

            User user = userList.get(0);
            //没有登录则程序自动登录
            if (!SecurityUtils.getSubject().isAuthenticated()) {
                Subject subject = SecurityUtils.getSubject();
                subject.login(new UsernameToken(user.getUsername()));
            }

            //检查用户补充信息是否完成、注册审核是否通过
            List  workUnitList = aliAdminBaseService.listQueryBySQL("where userId = #{0}", WorkUnit.class, user.getId());
            if (workUnitList == null || workUnitList.size() == 0) {
                log.warn("user {} need profile", user.getId());
                String url = aliAdminConfigService.getString("weixin.aliadmin.need.profile.url", "");
                return "redirect:" + domain + url;
            } else if (!RegisterStatus.审批通过.toString().equals(user.getVerifyStatus())) {
                log.warn("user {} wait register approval", user.getId());
                String url = aliAdminConfigService.getString("weixin.aliadmin.wait.register.approval.url", "");
                return "redirect:" + domain + url;
            }

            String url = aliAdminConfigService.getString("weixin.outh2.redirect.h5.url." + state, "");
            String stateKeys = aliAdminConfigService.getString("weixin.outh2.states", "");
            log.info("openId {} click {}", openId, state);

            if (stateKeys.contains(state)) {
                return "redirect:" + domain + url;
            } else {
                return "redirect:" + domain + loginUrl;
            }
        }
        return "";
    }
}
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)