 IDPNativeAppSDK-iOS - 开发手册 

更新时间 2016年11月
SDK版本号 1.0.0
IDPNativeApp演示应用使用MIT License；
IDPNativeAppSDK.framework公开使用，但代码为私有License，未经授权，不得修改、复制或散播。

### 一、介绍
北京九州云腾科技有限公司的IDP产品的口号是统一身份、安全便捷，而IDP单点登录iOS SDK能够实现IDP身份管家到第三方开发者应用的身份管理和单点登录。

如果对于IDP不熟悉的话，可以联系我们info@idsmanager.com，或者去我们公司的网站[北京九州云腾 - 统一身份、云中漫步](http://www.idsmanager.com) 了解详细。IDP产品针对的是企业级用户，单点登录SDK针对的也即企业内部开发者。IDP系统能够很安全便捷地统一管理企业人员在内部应用中的账号信息。

除了SDK以外，我们还开源地为你提供了一个demo应用IDPNativeApp，地址如下：https://git.oschina.net/sz_ids/IDP2-NativeApp-IOS (即本页面)，在 MIT License 下可以随意参照修改。该demo应用使用xcode8.0和Swift 3.0开发，如果您的开发方式不一致，可能会导致未知错误。

 **集成NaitveApp之后,通过IDP身份管家实现如下效果:** 

1.通过IDP身份管家点击集成的NativeApp

2.选择您要单点登录的用户(如果只关联一个用户则直接跳转到NativeApp应用单点登录)

3.打开NativeApp并且根据你选择的用户实现单点登录

![输入图片说明](https://shimo.im/doc/QKTbYxre0OskmwUl"在这里输入图片标题")

已实现的功能：
- 用U+P(用户名+密码)的方式从IDP身份管家跳转到第三方应用，并且获取到由应用：IDP身份管家 传来的账号信息，以在本地应用中无缝连接单点登录，直接进入登录状态。
- 支持framework下载安装

将实现的功能：
- 除了U+P外，提供基于OAuth或OIDC的token验证方式，更加安全有效
- 支持cocoapods或者carthage安装，更加傻瓜式便捷

系统版本支持： 
iOS9.0+

如有问题，请联系info@idsmanager.com，或致电 010-58732285。

 

### 二、如何安装
Framework安装方法
1. 从我们的网站直接下载sdk的framework包，或者从demo应用IDPNativeApp https://git.oschina.net/sz_ids/IDP2-NativeApp-IOS 中直接获取IDPNativeAppSDK.framework。
2. 将IDPNativeAppSDK.framework拖入到项目中的framework文件夹中。

![输入图片说明](http://git.oschina.net/uploads/images/2016/1125/165707_d544abcd_938102.png "在这里输入图片标题")

3. 在Targets -> General 中下方有一栏叫做Embedded Binaries，将我们的IDPNativeAppSDK添加进去。
  1. 点击下方的 + 号
  2. 在Frameworks中选取IDPNativeAppSDK
  3. 成功将SDK添加到Embedded Binaries中

![输入图片说明](http://git.oschina.net/uploads/images/2016/1125/165727_48007fbc_938102.png "在这里输入图片标题")

尝试build或运行。如果没有出错误的话，到这里SDK的安装就完成了，下面要介绍在Xcode中如何设置和使用SDK。如果在这一步出现错误的话，请删掉重复上面的步骤。您也可以打开我们的demo应用来看我们的集成结果，互相比较。

### 三、使用IDPNativeAppSDK
使用IDPNativeApp一共有三步。
1. 前往Targets -> Info -> URL Types新创建一个URL Type，这之中唯一必填的内容就是 URL Schemes，该项代表着在app之间跳转的唯一标识，在之后的网页上的步骤中会需要填写。URL Scheme不需要和bundle ID或者应用名称一致。

![输入图片说明](http://git.oschina.net/uploads/images/2016/1125/165759_9900100a_938102.png "在这里输入图片标题")

2. 在AppDelegate中import进IDPNativeAppSDK，并且在AppDelegate中添加方法（Demo中提供的是Swift3版本，请自行转换成您开发所使用的对应版本）：

```
func application(_ application: UIApplication, open url: URL, sourceApplication: String?, annotation: Any) -> Bool {
   
    // IDPNativeAppSDK的方法，负责处理从IDP跳转过来的机制
    return IDPNativeAppSDK.handleOpenApp(url: url, sourceApplication: sourceApplication);
       
}
```

本方法初始化了当从IDP身份管家应用中跳转过来时候的处理机制。

3. 最后，在希望获取到用户的账户信息的地方，调用IDPNativeAppSDK.getUserInformation()方法，在successBlock中获取到返回的账号信息。该方法在IDP身份管家中跳转过来之后，只能被调用一次。如果需要多次使用用户信息，请自行保存。

successBlock返回的Dictionary 内容:
```
{ "errorNumber": 0, "username": "xxxxxx", "password": "xxxxxx" }
```

failureBlock返回的Dictionary 内容:
```
{ "errorNumber": 0, "detail": "错误信息" }
```
4.如果从SP发起,去IDP授权后登录需要调用,IDPNativeAppSDK.open(),参数scheme是调起应用的URL Scheme,appType调起应用的类型,paramString参数: paramString格式: username=xxx&age=xxx&phonexxxx
```
IDPNativeAppSDK.open(scheme: "jiuzhou", appType: IDPNativeAppType.IDP_BasicNativeApp, paramString: "username=lisi&xxx=xxx){ (success) in
            print(success)
        }

```
5.获取单点登录的token,IDPNativeAppSDK.getIdToken(infoURL:"url")

```
    func application(_ app: UIApplication, open url: URL, options: [UIApplicationOpenURLOptionsKey : Any] = [:]) -> Bool {

      IDPNativeAppSDK.getIdToken(infoURL: url as NSURL)
    }

```
到这里，Xcode中的SDK设置和使用也已经全部完成，我们现在需要在IDP页面上为本应用配置信息。

 

### 四、IDP单点登录设置
IDP(Identity Provider)产品市场名称为：IDP身份管家，支持iOS和Android，在App Store和应用宝上可以下载到。该产品是IDP产品线的重要组成部分，配合网页端可以做到安全、便捷地统一管理和使用自己的账号身份信息。IDP身份管家对于本地应用的身份管理支持，是移动端实现统一所有网络身份的重要模块。IDP提供的本SDK，目的是为企业开发者提供一个可以接入IDP的方法，能够实现从IDP应用到第三方开发应用的账号管理和单点登录。

想要实现IDP的统一账号管理和单点登录，您所在的公司必须要正在使用IDP产品，并且您必须拥有管理员权限。开发者权限是不能够添加Native App应用的，请注意。


1. 在管理员的IDP界面中，点击添加应用，搜索Native App，这里看到的使我们提供的统一模板，我们使用这个模板，点击添加应用。（如果没有找到该模板，请与九州云腾联系）

![输入图片说明](http://git.oschina.net/uploads/images/2016/1125/165835_e8b01bf2_938102.png "在这里输入图片标题")

2. 继续填写需要添加的应用内容。
  - 所属领域：请根据情况选择最合适的，这里的选项不会影响到应用的实现
  - iOS/Android Scheme URL
    - iOS 的Scheme Url填写您在第三节第一部在Xcode中创建的URL Scheme
  - 账号关联方式：这里选择您希望通过什么方式从IDP身份管家把用户的身份信息传递给你的应用，我们目前只支持账号密码的方式，以后会提供基于OIDC或OAuth的token方式。

![输入图片说明](http://git.oschina.net/uploads/images/2016/1125/165853_1774c4d7_938102.png "在这里输入图片标题")

3. 请为应用授权用户，以便能让公司用户开始使用。如果您知道如何授权应用，请自行授权并跳过本节讲解。
  - 如何授权：授权指的是将一个企业添加进来的应用交给用户使用的过程。IDP系统中，应用添加好以后，需要授权给用户组，如果应用实在开启（默认）的状态的话，那么该用户组的人就可以在他们的IDPs侯爷看到新添加进来的应用。
    - 从左侧进入授权菜单
    - 从列表中选择刚创建的应用
    - 添加新授权
    - 在新页面中选择想要授权的用户组，比如测试组，管理组等。
      - 如果未创建用户组，可以自行创建。如果未添加用户，请先添加用户，并将其归入一个用户组内。

![输入图片说明](http://git.oschina.net/uploads/images/2016/1125/165917_b654e4e0_938102.png "在这里输入图片标题")

4. 应用到这步已经添加完成，但是我们还需要为授权的用户组中的用户添加该用户在该应用的账号信息，这样才能一一对应将这些信息在跳转时传入第三方应用。如果您知道如何授权添加应用子账号，请自行授权并跳过本节讲解。
  1. 退出登录，并以刚才授权过的用户组中某个用户的身份重新登录系统。如果您刚才的管理员是授权成员组成员之一，那么您不需要登出，只要在右上方导航条下拉菜单中选择用户界面即可跳转到用户身份。
  2. 进入应用子账号菜单，会看到你的所有被授权的应用所添加的账号信息的列表。点击右上角的添加应用子账号按钮。

![输入图片说明](http://git.oschina.net/uploads/images/2016/1125/165951_6a46b391_938102.png "在这里输入图片标题")

  3. 在添加界面中选择正确的应用，并且填入对应您第三方应用有效身份信息的用户名密码。比如我开发了应用叫做「微信改」，我在这里天蝎的就是我希望IDP身份管家能帮我管理，并实现单点登录的对应「微信改」账号。这个账号应该在您应用自己的系统中注册并可以使用。

    - 如果您在尝试使用IDPNativeApp这个Demo应用，请在运行IDPNativeApp后点击注册按钮，并将注册好的信息填写在本步骤中。
  4. 您可以为同一个应用添加多个需要管理的账号，IDP身份管家会在跳转前询问您需要使用哪一个

![输入图片说明](http://git.oschina.net/uploads/images/2016/1125/170034_1c57761b_938102.png "在这里输入图片标题")

我们从前到后添加进了IDPNativeAppSDK，配置好了URL Scheme，在IDP网页端创建好了应用对应了URL Scheme，在授权给目标群组之后，在用户界面给该用户自己添加了目标应用的账号信息。

到此，您的应用应该能够使用IDP身份管家来管理和登录您的应用了！

 

如果您有宝贵的意见请随时与我们联系info@idsmanager.com 。我们会在未来为IDP使用者和开发者提供更完备的SDK功能，敬请期待！

北京九州云腾团队
2015年11月

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)