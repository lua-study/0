### AppSoft2.0.IO不仅仅一个通用系统框架，更是你编程生涯的伴侣，可以让你编程效率有着事半功倍效果！

*****

> AppSoft2.0.IO 摒弃了Entity Framework，采用[SqlSugar](https://github.com/sunkaixuan/SqlSugar)框架，[SqlSugar](https://github.com/sunkaixuan/SqlSugar)是众多.NET ORM框架中性能最接近ADO.NET，并且开发效率超越Entity Framework的ORM框架！

*****

### AppSoft2.0 IO 开发者信息

*****

* 系统名称：`AppSoft2.0.IO .NET通用开发系统`
* 系统作者：`新生帝`
* 作者Q Q：`8020292`
* QQ交流群：`18863883`，加群请注明：`AppSoft2.0.IO`
* 开发日期：`2016年02月09日`
* 版权所有：`中山赢友网络科技有限公司`
* 企业官网：[http://www.winu.net](http://www.winu.net)
* 开源协议：`GPL v2 License`
* 系统描述：`一切从简，只为了更懒！`

*****

### AppSoft2.0.IO 视频教程（采用屏幕录像机录制，直接下载exe即可）（持续更新）：

*****

* [1.0 AppSoft2.0.IO 视频教程——项目初始化](http://pan.baidu.com/s/1nunjwJR)

*****

* [2.0 AppSoft2.0.IO 视频教程——T4模板生成所有相关文件](http://pan.baidu.com/s/1nunjwJR)

*****

* [3.0 AppSoft2.0.IO 视频教程——项目实战CURD操作](http://pan.baidu.com/s/1nunjwJR)

*****

* [4.0 AppSoft2.0.IO 视频教程——插件开发教程](http://pan.baidu.com/s/1nunjwJR)

*****

* [5.0 AppSoft2.0.IO 视频教程——RESTful API跨平台开发](http://pan.baidu.com/s/1nunjwJR)

*****

### AppSoft2.0 IO 主要特点：

*****

后续更新！

*****

### AppSoft2.0 IO 项目进度

*****

* **目前项目未完成，只搭建好基本骨架！**
* 内置功能会持续开发并更新中，欢迎关注！

*****

### AppSoft2.0 IO 系统设计及技术框架（持续更新）：

*****

#### 后端

* N层架构（抽象工厂，自动工厂，OOP，AOP）
* **ASP.NET MVC 5/Web API2.1**
* **.NET Framework 4.6.1**
* **MVC 插件式开发，支持热拔插**
* [Autofac](https://github.com/autofac/Autofac) | [文档说明](http://docs.autofac.org/en/latest/)
* [SqlSugar](https://github.com/sunkaixuan/SqlSugar) | [文档说明](http://www.cnblogs.com/sunkaixuan/p/4649904.html)
* [Redis](https://github.com/MSOpenTech/redis) | [文档说明](http://www.cnblogs.com/yangecnu/p/Introduct-Redis-in-DotNET.html)
* [Log4Net](https://logging.apache.org/log4net/)
* [Quartz.Net](http://www.quartz-scheduler.net/)
* [Lucence.NET](http://lucence.net/)
* [NPOI](http://npoi.codeplex.com/)
* [SuperWebSocket](https://github.com/kerryjiang/SuperWebSocket)
* [Senparc.Weixin.MP](https://github.com/JeffreySu/WeiXinMPSDK) | [系列教程](http://www.cnblogs.com/szw/archive/2013/05/14/weixin-course-index.html)
* [AutoMapper](https://github.com/AutoMapper/AutoMapper)
* [CraigsUtilityLibrary](https://github.com/JaCraig/Craig-s-Utility-Library) | [官网说明](http://jacraig.github.io/Craig-s-Utility-Library/)
* i18n
* E-RBAC
* WorkFlow
* [RazorEngine](https://github.com/Antaris/RazorEngine) | [文档说明](http://www.cnblogs.com/huangxincheng/p/3644313.html)
* [FluentValidation](https://github.com/JeremySkinner/FluentValidation) | [文档教程1](http://www.cnblogs.com/asxinyu/p/dotnet_Opensource_project_FluentValidation_1.html) | [文档教程2](http://www.cnblogs.com/asxinyu/p/dotnet_Opensource_project_FluentValidation_2.html)
* SQL Server 2005 + 

*****

#### 前端

整理中...

*****

### AppSoft2.0.IO 系统架构设计图：

*****

![输入图片说明](http://git.oschina.net/uploads/images/2016/0212/023235_1173f9d3_526496.jpeg "在这里输入图片标题")

*****

### AppSoft2.0.IO 目录结构（待完善，持续更新）

*****

```
AppSoft2.0.IO  解决方案目录
├─App.Document    项目说明文档，数据库初始化文件等等
├─App.Entity    数据表对应实体模型
├─App.Filter    全局过滤器（AOP）
├─App.IRepository    数据表对应仓储接口
├─App.IServices    数据表对应服务接口
├─App.Library    常用公共类库
├─App.ORM    ORM框架类库，如EF，SqlSugar
├─App.App.PluginFactory    插件管理器，实现插件机制
├─App.Repository    数据表对应仓储实例类
├─App.RESTful API    RESTful API接口项目
├─App.Services    数据表对应服务实例类
├─App.Site    网站项目
├─App.TestPlugin    测试插件示例
├─App.Vector    第三方提供DLL或者操作帮助类
├─App.WeiXin API	微信平台开发API接口
├─README.md	README文件
├─LICENSE.txt	授权说明文件

```

*****

### AppSoft2.0.IO 最终完成版目标包含以下子系统或功能，可以以插件形式自由添加子系统或功能：

*****

* CMS 内容管理系统（可以管理多个子站）
* 通用权限管理系统
* 企业OA系统（包含工作流，自定义表单）
* 微型CRM系统
* 即时通讯
* 工单系统
* 任务管理系统
* 微信平台管理系统
* 微型论坛社区系统
* 电商系统（产品，订单）
* 开放平台RESTfull API接口

*****

### AppSoft2.0.IO 应用场景（持续更新）：

*****

* Web软件系统开发
* 企业/门户网站开发
* 管理系统开发
* 电商平台开发
* 微信平台开发
* 论坛社区开发
* 移动端RESTful API开发
* ...
* ...

*****

### AppSoft2.0.IO 界面截图（持续更新）：

*****

![输入图片说明](http://git.oschina.net/uploads/images/2016/0227/012728_405f7dbc_526496.jpeg "在这里输入图片标题")

*****

### 其他附件图：

*****

* MVC请求机制简图

![输入图片说明](http://git.oschina.net/uploads/images/2016/0215/122618_acffb4e2_526496.png "在这里输入图片标题")

*****

* MVC整体请求流程图

![输入图片说明](http://git.oschina.net/uploads/images/2016/0215/122652_ebf12c84_526496.png "在这里输入图片标题")

*****

* 工厂创建类和视图引擎类的作用介绍（插件实现原理）

![输入图片说明](http://git.oschina.net/uploads/images/2016/0215/122731_a4241ebf_526496.png "在这里输入图片标题")

*****

### AppSoft2.0.IO 欢迎捐赠

*****

如果你觉得 AppSoft2.0.IO 对你有价值，并且愿意让她继续成长下去，你可以资助这个项目的开发，为作者加油打气。

![欢迎捐赠AppSoft2.0.IO](http://git.oschina.net/uploads/images/2016/0207/160936_8f2d5f2e_526496.png "欢迎捐赠AppSoft2.0.IO")

*****

如果你喜欢AppSoft2.0.IO，可以点击右上角的`star`，想实时关注进度，可以点击右上角的`watch`。

最后，感谢每一个提建议和使用或者捐赠的朋友！因为你们，我们才能坚持！也是因为你们，未来才会更美好！

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)