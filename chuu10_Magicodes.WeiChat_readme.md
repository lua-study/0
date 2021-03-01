# Magicodes.WeiChat

当前代码均为Magicodes.WeiCha微信快速开发框架源码，可以学习使用，亦可商用。关注公众号“magiccodes"获取最新资讯和教程。

**推荐框架（力推）**（.NET Core)：https://gitee.com/magicodes/Magicodes.Admin.Core

授权文档下载（和免费版的区别仅仅为支持售后）：

1. [Magicodes.WeiChat源码高级版授权合同](Magicodes.WeiChat源码高级版授权合同.doc)

# 开发使用文档

[Magicodes.WeiChat框架说明文档](./Documents/Magicodes.WeiChat框架说明文档.docx)

# 官方博客

http://www.cnblogs.com/codelove/

# 官方网址
http://xin-lai.com

# 其他开源库地址
https://github.com/xin-lai

# 相关QQ群

编程交流群 

产品交流群 

## 更新日志
具体代码提交修改记录见：https://gitee.com/xl_wenqiang/Magicodes.WeiChat/commits/develop

# V4.8 (2018.9.19)
1. 重构支付模块，独立支付模块
2. 发布小程序SDK
3. 重构支付回调模块，统一支付回调并且支持微信回调和支付宝回调逻辑的合并
4. 自定义菜单支持小程序菜单
5. 修复运行时版本冲突

# V4.7 (2018.4.17)
1. 修复JSSDK调用的一个错误
2. SDK更新到最新版本
3. 自定义菜单支持小程序配置

# V4.6 (2018.2.2)
1. 增加数据批量处理支持
2. 优化粉丝同步性能（仅对MS SQL）
3. 升级ko
4. 修复文章删除的一个Bug
5. 升级SDK
6. 修复ko组件引起的点击问题

# V4.5 (2017.12.20)
1. 事件简单封装，主要用于模板消息动态推送。
   1. 支持事件触发
   2. 支持事件侦听
   3. 支持侦听操作处理（目前仅支持模板消息处理）
   4. 支持事件参数（IEventData），其中WeChatEventDataBase为公众号事件参数基类（包含部分默认全局函数，以便表达式中调用）
   5. 目前已支持表达式编写，例如：Receivers="{{0}.WeChatUser.OpenId}"、Expression="{\"感谢关注：\"+{0}.GetWeChatUserByOpenId({0}.WeChatUser.OpenId).NickName}"。
   #### 具体使用见单元测试：EventTest。后续考虑设计界面，允许后台动态配置。

2. 配置页增加IP白名单提示。
3. 添加简单CMS，支持栏目和文章管理。
4. 上传素材接口如果达到限制，UEEditor将给出明确提示。
5. 重构图片上传，所有文章中，图片上传不占用素材资源。
6. 素材管理文件名显示添加处理，超出长度显示省略号。

# V4.4 (2017.11.24)
1. 支付设置在打开时自动更新后台回调地址
2. 修复菜单管理可能报错的Bug
3. 修复模板消息日志记录的一个Bug
4. 将JSSDK的版本更新到1.2.0
5. 更新JSSDK封装选择图片时，没清空上次选择的问题
6. 修复智能回复，文章图片因微信禁止外链而不显示的问题
7. 修复查看文章时无法显示图片的情形
8. 完善UEEditor图片上传的一个Bug
9. 公众号文章增加字符数验证（不能超过20000个字符）
10. 增加CRUD控制器
11. 增加处理时间格式化脚本
12. 无限滚动增加无数据的提示
13. 添加服务器事件消息转发配置+转发功能
14. 首页统计数据更新为使用WeChat SDK获取
15. 将.NET 版本修改为4.6.1
16. 将nuget包Magicodes.WeChat.SDK修改为Magicodes.WeChat.SDK.Core
17. 升级到最新的Magicodes.WeChat.SDK.Core包
18. 修改SDK注册逻辑

# V4.3 (2017.3.23)
1. web.config增加移除WebDAV的Module和Handler，防止WebDAV阻止httpput请求
2. _LoginPartial.cshtml 增加租户为空判断以及配置为空判断
3. 修复群发消息时，无法发送到相应分组的问题
4. 修复/bundles/jqueryval的异常
5. 群发消息增加预览，允许输入微信账号或者选择当前账号绑定的OpenId进行预览
6. Magicodes.WeChat.SDK更新到1.0.6290.28984
7. 修复素材管理文件名过长时溢出的情形


# V4.2 (2017.2.21)
1. 修复菜单数据初始化的一个Bug
2. 修复消息推送界面右上角通知数值显示问题
3. 更新TypeScript版本
4. 修复菜单可能为空的情形导致菜单加载错误
5. MvcHelper增加TenantAction的重载，允许传入额外参数
6. 修改模板消息同步逻辑
7. 修复多图文管理的文章管理的Bug
8. 修复部分页面没权限的问题
9. 修复Controller为null的Bug

# V4.1 (2016.11.30)
## 本次更新内容比较大，请谨慎更新（尤其是权限部分代码，可能会影响您已扩展的业务逻辑，请根据自身业务考虑是否使用）
1. 重写自定义菜单处理
2. 重写左侧导航加载逻辑
3. 更新包Magicodes.Echarts、Magicodes.Mvc.AccessFilter、Magicodes.WeChat.SD
4. 修复菜单加载时不能加载父级菜单的问题
5. 添加访问筛选器，并编写了访问日志记录的Demo以及增加了后台权限控制部分逻辑
6. 添加Magicodes.Task和Magicodes.Notify的Nuget引用，以支持后台任务和站内即时通知，支持进度条报告进度
7. 添加SyncMessagesTemplatesTask处理消息模板信息同步逻辑
8. 添加SyncMKFTask处理多客服客服信息同步逻辑
9. 添加SyncWeChatUserGroupTask处理粉丝标签信息同步逻辑
10. 移除SyncHelper和TaskHelper
11. 添加SyncWeChatUsersTask，用于编写粉丝同步逻辑
12. 添加TaskManagerConfig配置，用于设置任务管理逻辑
13. mwc_business.js增加 initAllTrCheck，以初始化内容Checkbox
14. 暂时移除了公众号信息配置界面的相关同步项
15. 登陆页修改并增加每日一图

# V4.0 (2016.10.31)
1. 修复接口配置信息Token验证因为筛选器拦截无法验证正确的问题
2. 修复使用MySQL时，用户角色表的索引长度问题
3. 修复修改系统租户信息时，导致无法登陆租户后台的问题
4. 完善mwc_elements.js、mwc_business.js和wc.js
5. 完善多图文管理，以支持MySQL
6. 替换自定义菜单的创建接口为Magicodes.WeChat.SDK的实现，以修复添加媒体菜单时的问题

# V4.0 Beta (2016.10.06)
## 本次版本框架进行了大改，主要目的在于让开发者将更专注于微信业务代码的编写，而不需要太关心其他工具库的实现。也便于以后产品的升级。
1. 封装大量组件并开源（见开源库：https://github.com/xin-lai），并且支持Nuget包管理（请使用Nuget搜索“Magicodes”），目前主要封装了以下组件：
    1. Magicodes.Data【数据相关】（Magicodes.Data.Multitenant——ASP.NET Identity多租户支持）
    2. Magicodes.WeChat.SDK【微信SDK】（微信接口封装，支持多租户，简单轻量）
    3. Magicodes.Mvc.Filter【通用筛选器】（Magicodes.Mvc.AccessFilter——访问筛选器，Magicodes.Mvc.AuditFilter——审计筛选器，Magicodes.Mvc.RoleMenuFilter——角色菜单筛选器）
    4. Magicodes.Storage【通用存储支持】（Magicodes.Storage——核心库和接口，Magicodes.Storage.Local——本地存储支持，即将支持阿里云和Windows Azure）
    5. Magicodes.Logger【通用日志处理】（Magicodes.Logger——核心库，Magicodes.Logger.NLog——Nlog实现，Magicodes.Logger.DebugLogger——控制台日志实现，以支持单元测试或者调试日志输出）
    6. Magicodes.Sms【短信消息】（Magicodes.Sms——核心库，Magicodes.Sms.Alidayu——阿里大鱼短信接口实现）
    7. Magicodes.ECharts【Echart图表实现】（Magicodes.ECharts——Echart图表核心实现，Magicodes.ECharts.Mvc——Echart Mvc扩展）
2. 支持多种数据库，目前已支持SqlServer和MySQL。关于MySQL的支持，请查看Web.config注释说明
3. 修复菜单折叠后，二级菜单不显示的问题
4. 修复关键字回复中，选择了接入客服后，在选择其他素材可能会抛出异常的情形
5. 移除模板消息日志和粉丝表的外键约束，以便不影响粉丝同步
6. 支付Api重新封装，具体使用和Demo稍后会逐步编写教程
7. 移除解决方案中大部分组件，并一一进行重构——图表重构为使用Magicodes.ECharts实现，日志替换为Magicodes.Logger,存储部分已更新为Magicodes.Storage，Data和SDK分别使用了Magicodes.Data.Multitenant，Magicodes.WeChat.SDK
8. 更新T4模板，修正部分生成逻辑
9. 修改后台字体以及主体样式，修改Echart主题
10. 重构部分数据模型，以便更易于阅读和理解
11. 增加审计日志、访问日志页面、以及角色菜单生成逻辑和配置，核心代码依赖Magicodes.Mvc.Filter实现
12. 移除批量处理封装，以支持MySQL等其他数据库类型

# V3.9 (2016.7.27)
1. 粉丝同步代码兼容VS2013
2. 更新T4基架模板
3. 修复智能回复时文本编辑和删除报错的Bug
4. 自定义菜单支持版本管理
5. 完善menu api
6. 添加knockout-sortable，并增加对自定义微信菜单的拖拽排序
7. 修复自定义菜单选择图片时无法正常显示图片的问题
8. 修改上传插件样式以及文件上传弹框大小，更换上传提示
9. 增加站点菜单管理，角色菜单管理并且自动初始化菜单数据
10. 增加图标选择组件
11. 修复删除媒体文件的一个BUG
12. 修复T4模板的一个问题
13. 修复mwc_business.js批量操作的一个BUG
14. 支持按角色加载菜单，支持用户角色设置，允许多角色
15. 模板消息编辑支持输入模板库编号来添加
16. 修复答不上来无法配置接入客服的BUG
17. 添加StopwatchAttribute，用来检测控制器性能
18. 添加WeiChatApiCallbackFuncArgInfo
19. 修复租户成员详情问题
20. 修复文章管理时编辑器编辑之后，公众号无法显示图片的问题
21. 封装SiteResourceHelper，并完善UEEditor上传处理代码以支持链接微信图片素材
22. 修复自定义菜单Url切换的一个bug
23. 添加JSONModelBinder，以支持对数据模型JSON格式的绑定
24. 添加 Url.TenantAction方法，以更便捷的生成租户链接
25. 添加设置管理器基础代码
26. 修改JSTree的Bundle配置，以解决Release模式下样式加载问题
27. mwc.message.prompt增加参数inputValue，以便设置文本框默认值
28. 修改mwc.restApi，以支持success、Success的状态判断
29. 添加SettingManager（设置管理器）
30. 修改mwc_business.js，增加initFormControls函数，以初始化数值、百分比、切换开关、日期、日期时间等控件
31. 完善关键字处理逻辑，增加相关逻辑判断
32. mwc.bs.postBatchOperation支持mwc.bs.batchOperationInitParams回调函数以设置全局默认参数，mwc.bs.batchOperation支持通过data-param传递参数方法，以动态传递参数
33. 修复粉丝添加到组的Bug
34. AppBase增加通用图片提示、消息提示界面，以便开发者调用并显示提示信息。同时App Demo中增加了异常（错误）提示界面、警告提示界面、信息提示界面的Demo
35. 在Debug模式下，将会启用ShowDetailExceptionFilter以输出详细错误信息。另外，ShowDetailExceptionFilter增加对DbEntityValidationException的异常内容输出支持
36. 增加微信异常提示界面，当微信页面出现异常时会显示默认的异常界面并提示友好信息。前提是控制器必须继承自AppBaseController
37. 将数据模型基础类主要拆分为WeiChat_AdminBase和WeiChat_WeChatBase，其中WeiChat_AdminBase主要作为后台模型的基类，WeiChat_WeChatBase作为微信模型的基类
38. 增加API性能计数器（ApiStopwatchAttribute）
39. 注册Api异常筛选器（WebApiExceptionFilter），以增加WEBAPI异常友好提示并记录异常具体信息
40. 增加AppApiController，作为微信业务WebAPI基类

# V3.8（2016.05.29）
1. 增加图文消息接口
2. 完善缓存管理，增加过期时间以及租户缓存清理函数
3. 增加EF批量操作扩展以及性能优化，批量操作性能提升90%（目前只支持批量插入，批量删除以及批量修改因兼容性问题还需要调整，具体请以单元测试结果为准）
4. 重写并优化粉丝同步逻辑，以便支持大量（百万级别）粉丝同步（任务并发请求+异常容错并重试机制+AccessToken过期处理+EF批量插入处理与优化+泛型集合处理优化）。百万级别粉丝同步性能从6小时优化到几分钟完成。
5. 接口增加AccessToken过期自动刷新机制(仅支持框架SDK接口)
6. 修复标签删除出现的Bug（涉及EF批量扩展兼容性问题）
7. 首页增加性能判断，以防止粉丝量特别大的租户打开首页时，消耗大量SQL计算性能。
8. 解决用户关注多个租户的多个公众号时粉丝信息不准确的问题，框架已经支持粉丝关注同一域名下多租户多个公众号情况下获取正确的粉丝信息。
9. 提供了以下微信页面Demo，相关说明请阅读开发文档或官方博客：
    * 微相册（图片轮询、照片上传、照片预览、瀑布流、图片延迟加载、通过WebAPI获取数据、页面元素绑定）
    * 产品版本（TimeLine）
    * 会员中心（WeChatOAuth）

# V3.7(2016.05.06)
1. 增加模板消息同步方法
2. 修改SyncHelper，使用租户筛选器
3. TemplateMessageApi增加AddTemplate和Get方法
4. 修改和完善同步逻辑
5. WeiChat_MessagesTemplate增加字段ShortNo（模板库中模板的编号）
6. 修改模板消息添加逻辑。只需要输入ShortNo（模板库中模板的编号）即可
7. TemplateMessageApi增加Delete方法
8. 修复租户成员删除报错的Bug以及跳转问题
9. 修复存在多个系统租户成员时删除系统租户成员仍报错的Bug
10. 添加在线客服入口链接
11. 修复租户成员绑定微信管理员可能绑定到系统成员的Bug
12. 修复租户成员未按租户过滤显示的Bug
13. 修复租户成员管理问题
14. 添加角色以及角色成员管理
15. 修复关键字回复编辑在某些浏览器无法加载的问题
16. 移除部分无关目录
17. 添加后台通用业务处理脚本mwc_business.js，具体介绍请关注我的博客
18. 添加AntiXssAttribute筛选器，可以有效防御XSS跨域脚本攻击
19. 修复wc_weichat.js（JSSSDK封装）的uploads函数（多文件上传）的一个Bug
20. 增加位置统计，以记录用户位置
21. 完善WeChatOAuth，并且修改ASP.NET Indentity的默认Cookie名称
22. 取消关注事件会更新粉丝的订阅状态
23. 添加配置信息时同步相关项的选择
24. 添加公众号类型配置（认证订阅号、认证服务号、测试号、企业号）
25. 添加TenantBaseApiController ，以支持WebAPI的多租户筛选支持
26. 微信服务器事件支持返回NULL相应请求，以不出现错误提示
27. 添加并完善tag-list组件，优化操作体验，增加删除功能，并且全部应用于素材管理
28. 暂时移除对Thumb的支持
29. 添加API状态码：测试号不支持此接口 = 40102
30. 移除对托管代码的异常日志记录
31. 添加ITenant接口
32. 关键字回复添加类型CustomerService，支持触发客服回复
33. 增加IdentityExtension类，并添加GetTenantInfo
34. 添加LoadingButton脚本
35. 修改content-choice.js，以支持CustomService类型
36. 顶部添加租户名称、公众号微信号等信息的显示
37. mwc_business.js支持loadingButton
38. 模板消息界面添加全量同步功能
39. 添加并完善TenantBaseApiController、WebApiControllerBase
40. 修改mwc_element.js，支持409（数据冲突）状态码的判断
41. 修改mwc.js以及mwc_element.js，添加mwc.message.prompt函数，以支持弹出输入框
42. 关键字回复支持菜单事件触发
43. 移除消息推送部分废弃代码和视图
44. 修复部分页面因维修屏蔽外链导致图片不显示的情形

# V3.6（2016.04.05）
1. 支持输入“客服”关键字将消息转接多客服
2. 添加wc.js，封装UI常用操作。后续文档和博客会具体介绍。
3. 添加tenanturl-input组件，支持在url控件自动添加租户参数。后续将支持更多功能。
4. 移除WXFramework.js、WXWebApp.Core.js
5. 修复关键字回复和关注时回复可能浏览器不兼容的问题
6. 添加WebApi Demo，具体代码内容可以查看Src/Magicodes.WeiChat/Controllers/WebApi/DemoController.cs
7. 修复文章内部图片前缀问题
8. 修复标签初始化逻辑导致素材管理可能报错的情形
9. 添加Roadmap文件，具体内容可以查看"Magicodes.WeiChat\Documents\RoadMap.xlsx"
10. 全面修复a标签嵌套在bttuon标签内引起的浏览器兼容性问题
11. 添加答不上来配置
12. 修复关键字回复逻辑问题导致租户间的数据未隔离
13. 修复关键字创建时因唯一索引导致不同租户不能添加相同关键字的问题
14. 添加TenantManager，用于启用多租户筛选器
15. 修改MessageHandler，重构租户支持部分
16. 添加AppDemoController，提供相关Demo。
17. 添加WeChatOAuthTestDemo，用于演示通过授权页面获取用户信息。具体介绍见博客（http://www.cnblogs.com/codelove/p/5355514.html）
18. 添加_JWeixinConfig.cshtml部分页，封装JSSDK配置逻辑（具体介绍见后续文档）
19. 添加wc_weichat.js，封装JSSDK常用操作（具体介绍见后续文档）
20. 添加_GetLocation.cshtml，封装百度API获取坐标以及详细位置信息（具体介绍见后续文档）


# V3.5（2016.03.22）
1. 修复Nuget包问题
2. 修改同步逻辑
3. 修正部署后部分用户KnockoutJs脚本问题
4. 修复多客服账号管理Bug
5. 完善多客服账号管理接口，并添加单元测试
6. 增加MD5加密处理扩展方法
7. 增加关注时更新用户信息
8. 移除WeChatOAuth特性中用户新增逻辑
9. 关注、关键字回复日志中增加微信OpenId、公众号原始Id、消息Id、事件Key等字段的记录
10. 系统租户界面增加更多权限控制
11. 在系统租户的公众号管理界面上增加系统界面的入口
12. 关键字、关注日志按最新排序显示
13. 修复多客服Bug
14. BaseController增加HasConfigWeiChat字段（是否已配置微信信息）
15. 优化公众号管理首页如果没有配置公众号信息的跳转逻辑
16. 修复content-choice.js加载类型可能会无法加载的问题

# V3.4
1. 修复系统管理员退出问题
2. 完善系统租户操作其他租户功能
3. 缓存管理增加按租户缓存的方法
4. 完善租户Id的获取机制
5. 完善模板消息的日志记录
6. 完善系统租户管理验证机制
7. 将AppSecret设置为密码框，增加安全性
8. 增加JSSDK页面配置
9. 修改Logo
10. 修复因调整目录结构引起的引用缺失问题

# V3.3
1. 增加绑定微信管理员功能
2. 重构二维码生成，并且增加二维码用途
3. 优化restApi.post
4. 优化WeiChatConfigManager
5. 增加QRCodeApiTest
6. 结构重构，并且对目录进行了梳理
7. 粉丝管理增加CSV导出功能
8. 添加CsvFileResult用于导出Csv，添加CsvHelper用于Csv读取和写入。具体见博客：http://www.cnblogs.com/codelove/p/5253634.html
9. 添加项目Magicodes.WieChat.ComponentModel，用于定义相关通用特性
10. 修改List.cs.T4，修改查看按钮的HTML
11. 删除素材时也会删除相关文件
12. 修复关键字回复日志的查看功能。移除创建按钮。
13. 首页增加判断，如果没有配置公众号信息会跳转到配置页面。
14. 增加部分常用扩展方法
15. 增加关注时回复功能
16. 增加content-choice-button组件，用于选择内容类型
17. 关键字回复编辑时增加预览功能，依赖content-choice-button组件
18. Framwork重新封装自定义菜单获取接口，具体见博客：http://www.cnblogs.com/codelove/p/5236488.html

# V3.2
1. 修复mwc_element.js中，mwc.restApi.post提交数据的Bug
2. 修复登录页样式问题
3. Magicodes.WeiChat.Framework增加MenuApi，并实现了Get方法。详情请关注博客以及文档更新。

# V3.1
1. 紧急修复一个因删除Magicodes.WeiChat项目下的Unity目录引起的问题

# V3.0（多租户）
1. 添加项目Magicodes.WeiChat.Data.Multitenant，全面支持多租户（基于EF已经ASP.NET Identity）
2. 增加租户管理、租户成员管理、修改密码、公众号配置等功能
3. 增加关键字回复功能，支持回复图片、文字、语音、视频、多图文等。并支持图片、语音、视频放大查看。
4. 添加TenantBaseController（多租户控制器基类），以便于自动注册租户筛选器以及设置相关配置。
5. 添加IDeleted接口，以便于后续封装软删除。
6. 添加EnumHelper，通过GetDisplayName可以获取枚举值的显示值（DisplayAttribute）。
7. 添加EntityFramework.DynamicFilters：https://github.com/jcachat/EntityFramework.DynamicFilters，添加多租户数据过滤器AppEntryFilter，添加软删除过滤器IsDeleted
8. 完善微信配置管理器，并增加函数注入功能。移除Magicodes.WeIChat.FrameWork对Magicodes.WeIChat.Data的引用，并且移除模板消息接口对数据库的访问，采用函数注入的方式。
9. 增加粉丝管理、用户组管理、模板消息的多租户支持
10. 添加关键字处理日志
11. 增加对微信服务器事件转发多租户支持。并且当微信服务器转发事件验证错误时，会在错误日志中提示。完善微信配置的保存。
12. 增加自动回复的日志记录。
13. 返回JSON日期时间格式化。
14. HMTLHelperExtensions增加IsSelectesUrl，以更好的匹配路径。
15. 增加站点资源管理，管理站内和公众号的语音、视频、图片、文章、多图文等素材。
16. 完善restApi的success判断。
17. 完善mwc.restApi.delete请求时，含JSON数据报错的情形。
18. 站点资源管理增加删除功能。
19. 当关键字未匹配时，支持返回关键字列表。并且优化关键字回复。
20. 重构消息推送，并且增加视频推送。
21. 优化mwc.js中的弹窗函数，使其在多层弹窗时，窗口大小更友好。
22. 增加media-choice，支持多种资源选择。
23. 自定义菜单重构。media-choice支持编辑、禁用、传递类型。并且完善自定义菜单高度。
24. 修复粉丝管理因为性别改为枚举类型报错的问题。
25. 修复素材管理——图文消息管理点击添加按钮添加多图文报错。
27. 修复模板消息查看报错。
28. 修复全量同步粉丝时同步BUG。
29. 定义ApiArgumentException异常类，用于传入参数不正确时抛出。
30. 粉丝批量获取信息接口增加不得超过100的限制。
31. 增加XmlModelBinder，便于MVC模型绑定。
32. 修复多租户二维码支持。
33. 重写多客服账号同步。
34. 修复菜单数据为空时的Bug。
35. 增加显示详细错误筛选器，以便于调测。
36. 模板消息如果未录入模板数据时，抛出提示异常。
37. 增加百度地图获取经纬度模块。
38. 修复多图文搜索问题。
39. 修改分页样式，解决部分浏览器有时候点击无效的问题。
40. 移除网站下的Unity目录

# V2.5
1. 移除部分C#5.0语法支持，以及部分废弃代码
2. 更新Senparc.Weixin为最新版本，并且修复其自定义菜单接口不支持media_id和SingleViewLimited的问题

# V2.4
1. 增加缓存管理，详见开发文档
2. 增加容错处理，详见开发文档
3. 首页统计增加了缓存和容错处理
4. 若干接口封装
5. 修复菜单管理中，菜单数目过多时，显示不友好的问题
6. 添加对接口的相关单元测试
7. 添加查看成员按钮与链接
8. 添加粉丝管理表格视图，支持修改粉丝分组、设置备注
9. 修改菜单
10. 接口结果集基类添加GetFriendlyMessage方法以获取友好消息文本
11. 粉丝分组删除判断
12. 添加Unity层，添加WebRequestHelper以及WeChatApiWebRequestHelper，重写ApiBase中的GET、POST等方法的封装
13. 移除MenusApi中的MenuLink
14. 将SafeReturnHelper和ThreadSafeLazyBaseSingleleton移动到Magicodes.WeiChat.Unity
15. 修复因特性Serializable引起的WebApi序列化问题，具体见见：http://stackoverflow.com/questions/12334382/net-webapi-serialization-k-backingfield-nastiness
16. 重写MenusApiController，修复mwc.restApi.put提交问题。
17. 重新菜单自定义界面，使用mwc.restApi对象替换之前的旧代码
18. 修复AjaxResponse 特性Serializable的问题,见：http://stackoverflow.com/questions/12334382/net-webapi-serialization-k-backingfield-nastiness
19. 修改NewsApiController中的 Get(int pageIndex = 1, int pageSize = 6)函数，支持分页处理
20. 修改MenusApiController中的Get函数，增加更多容错处理
21. 修改news-choice.js组件，将Ajax请求替换为mwc.restApi
22. 移除WeiXinHelper的AccessToken属性，统一使用WeiChatConfigManager.Current.AccessToken
23. 将GetJSSDKConfigInfo移动至WeiChatConfigManager
24. 将DateTimeExtend移动至Magicodes.WeiChat.Unity.WeChat
25. 修改SyncUsers方法，将单个获取修改为批量获取，大幅度提升性能，将SDK接口更新为WeiChatApisContext.Current.UserApi.Get，WeiChatApisContext.Current.UserApi.GetOpenIdList
26. 添加和修改客户信息时出现的错误提示语字体加颜色
27. 增加WeiChatFilesManager，移除Magicodes.WeiChat.Framework对Magicodes.WeiChat.Infrastructure的引用，并且部分类重构
28. 添加SUI-Mobile，以便加速微信页面开发（后续开发文档会介绍）
29. 移除WeixinTasks，将所有配置移至WeiChatConfigManager
30. 添加类库：Magicodes.WeiChat.WeChatHelper，用于封装微信复杂业务和辅助业务
31. 添加TaskManager，用于任务管理，目前已将相关同步任务移动到此，后续会继续深化封装

# V2.3
1. 后台提供了模板消息的管理界面，同时FrameWork中封装了批量发送模板消息接口以及发送日志记录，具体请查看文档
2. 添加Bootstrap Colorpicker、X-editable、Select2插件，并且修复Select2对X-editable的支持
3. 开始逐步对配置管理进行重构，并增加对多租户的支持
4. 开始着手封装微信前端UI框架
5. 后端Js框架增加对窗口的支持，详见mwc.window

# V2.2
1. 将文档修改为Word，更易于查看与阅读，具体请查看源码包中的《Magicodes.WeiChat框架说明文档.docx》
2. 修复WeChatOAuthAttribute在链接分享出去时可能获取用户信息失败的问题
3. 日志输出增加Identify字段

# V2.1
1. 修改AppUser，添加显示描述
2. BaseController增加UserId，UserName，以便更加方便的获取用户信息
3. 通知提示图标重叠问题
4. JSON.NET组件引用报错问题
5. 暂时移除关键字回复管理，进入重构状态，以支持更多功能

# V2.0

1. 已构建后台前端框架（具体介绍等开发文档更新）
2. 重构自定义菜单模块，支持10种菜单类型，具体介绍见：http://www.cnblogs.com/codelove/p/4838766.html
3. 修复.woff .woff2文件在服务器加载失败的问题
4. 修复Bundle Release模式下某些JS加载失败的问题
5. 增加云日志功能，具体介绍请见查看《Magicodes.WeiChat——利用纷纭打造云日志频道》：http://www.cnblogs.com/codelove/p/4858771.html
6. 增加AjaxResponse
7. 完善代码基架——（支持创建、删除、查看、编辑、分页、搜索、删除提示、批量操作、批量删除、支持日期控件、支持多个主键）等代码生成，详见：http://www.cnblogs.com/codelove/p/4877491.html
8. 移除部分历史遗留代码和文件
9. 重构分页，并且添加分页view【_BootStrapPager】
10. 记录一切异常，方面代码问题追踪
11. 重构粉丝管理，界面更美观，而且能够显示粉丝头像
12. 左侧导航支持多控制器判断，详见HMTLHelperExtensions.IsSelectesControllers
13. 支持配置Token
14. 二维码管理（场景二维码）
15. 关键字文本回复管理

# V1.8

1. 对Magicodes.WeiChat.Infrastructure进行了若干修改
2. 增加若干筛选器，如DenyInternalRequestAttribute、WeChatOAuthAttribute，具体见Magicodes.WeiChat.Infrastructure.MvcExtension
3. 增加WeiChatApplicationContext，以便于获取微信相关信息，具体见Magicodes.WeiChat.Infrastructure.WeiChatApplicationContext
4. 完善Identity配置，具体见Magicodes.WeiChat.Infrastructure.Identity


# V1.7
1. 增加通过OAuth获取微信用户信息的实例与通用处理机制，具体请查看开发文档中的【通过OAuth获取微信用户信息】
2. 增加对AccessToken的缓存处理
3. 添加对微信JS接口的支持，后续更新会对其进行进一步的封装
4. 将登录错误的英文提示修改为中文

# V1.6
1. 多图文添加界面增加富文本编辑器
2. 使用JSON.NET替代ASP.NET MVC中的JavaScriptSerializer，详见JsonNetResult
3. 解决多图文展示时因为下载图片被占用而无法显示的问题

# V1.5
1. 只有在发布版本为DEBUG模式下，才会输出会话日志
2. 重构Magicodes.WeiChat.Data为数据层，据此做了大量的优化
3. 增加关键字处理数据表
4. 增加对关键字自动应答的文本答复
5. 支持对Visual Studio 2015的支持

# V1.4
1. 修复了客户工号修改密码的问题
2. Error页（Release模式）添加异常信息提示
3. 图片素材管理上传移除上传按钮，即拖拽自动上传
4. 优化图片素材管理上传体验
5. 图片素材增加删除功能
6. 图文消息增加删除功能
7. 优化图文消息图片选择体验与上传体验
8. 优化了语音消息的上传体验以及展示形式
9. 增加资源上传的超时时间（延长到2分钟）
10. 优化语音消息的推送体验
11. 修改消息推送完成状态提示，使其更加友好
12. 优化消息等推送体验和提示
13. 启用Nuget包自动还原

# V1.3

1. 增加消息处理机制（文本消息、 图片消息 、 语音消息 、 视频消息 、 小视频消息 、 地理位置消息 、 链接消息）
2. 增加模板消息示例
3. 增加事件处理机制（关注/取消关注事件、扫描带参数二维码事件、上报地理位置事件、 自定义菜单事件）
4. 增加错误日志工具，管理员可以访问/ServerErrors来查看错误日志
5. 增加日志组件（Nlog）
6. 增加404（/NotFoundError）和500（/Error）错误处理。**仅在Release模式下启用。**

# V1.2

1. 自定义菜单保存增加状态信息，并且优化操作体验
2. 增加【粉丝管理】

# V1.1

1. 新增“请配置web.config中的AppId、AppSecret！”异常
2. 修复无数据时，打开首页报错问题

# V1.0

1. 微信SDK
2. 微信快速开发框架
3. 首页报表
4. 自定义菜单
5. 素材管理（图片、音频、多图文）
6. 消息推送（图片、音频、多图文）
7. 客服管理
8. 管理员管理

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)