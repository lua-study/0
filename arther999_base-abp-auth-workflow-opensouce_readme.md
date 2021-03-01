# 基于ABP和Vue-Element-Admin的通用后台权限和工作流框架

实现目标通用的架构：
1. 前后端分离方案：基于 abp .net core 版后端 和 vue 前端
2. 使和数据库的交互标准化、简易方式：DDD领域驱动设计CodeFirst，实现基于vs插件的代码生成器 （生成代码包括vue前端、abp后端）
3. 权限设计：组织结构、RBAC的功能权限设计基于ABP、基于规则的数据权限（未实现）
4. 实现消息提醒：使用SignalR的Hub模式
5. 统一的登录中心OIDC: 改造Identity4Sever为时候abp的登录
6. 工作流：
 * 工作流包括流程引擎、流程设计器、表单设计器等，实现基于gooflow流程设计器、流程引擎、考虑使用者多为开发人员所以未实现表单设计器。实现过程参考OpenAuth.net 
 * 流程模型采用邻接表和逆邻接表表示顶点和顶点直接的关系、使用规则定义条件流转和节点权限
 * [工作流详细介绍](https://gitee.com/fq_chenzhen/MyWraper-Abpboliterplate/blob/master/%E5%B7%A5%E4%BD%9C%E6%B5%81.md)

7. 前端代码已开源

# 架构

## 后端 基于abp

* DDD区别与三层模式的核心有2点：
1. 层不同 DDD: core领域层、Application应用层、Dto层、Infrastrctrue基础设施层、UI层；
2. 依赖关系：所有层依赖于core领域层，数据的接口写在Core领域层，这样Application就不需要依赖Infrastrue层。进而通过IOC就可以达到真正的和数据库分离，也就是业务和具体技术的分离！

* 通用crud模板 封装

* 添加ETag缓存，默认缓存 /AbpUserConfiguration/GetAll、/api/services/app/Session/GetCurrentLoginInformations、/api/services/app/profile/GetProfilePicture，浏览器第二次访问时返回304，直接从浏览器本地取缓存数据。当修改用户的基本信息时情况服务端的ETag，返回最新数据给浏览器

* AutoMaper配置通过Profile统一处理

* Excel导出封装

* 集成第三方登录（Identity4Server、微信）

* 添加原生sql支持

* 数据库切换为 mysql (todo)

* docker 发布


## 前端 vue
使用 vue-element-admin 进行改造成适合abp的前端以及通用组件的封装、改动量比较大地方在于：
1. 登录后、语言切换、多租户页面刷新问题：vue实例化的时候主要时动态路由的生成, 用户登录后abp需要通过/app/Session/GetCurrentLog获取用户的配置信息、本地化、路由权限信息等。故需要刷新页面重新实例化vue
2. 权限设计的修改：原权限时基于角色的、abp基于permission更符合实际的应用场景

* 基于 vue-element-admin进一步封装适用abp的前端

* 修改路由基于permision的权限动态路由添加

* 集成abp的配置、abp通用一些消息提醒方法

* request.js 调整为abp的token，及后拦截

* 多语言、多租户切换

* 上传头像、修改密码、修改个人信息

* 导出 excel

* 通用组件封装

* curd模板

* 分页模板

* 通用保存对话框

* 可选择搜索对话框封装

* 集成第三方登录(Oidc)



# Identity4Sever 统一认证中心（OpenId Connect）

* [ABP集成IdentityServer4实现sso](https://gitee.com/fq_chenzhen/Abp-Template-IdentityServer4)

* 可以用于认证中心(OAuth) 和 内网的 sso

* 基于ef identity的用户中心

* 资源中心


# 功能点

* 登录、权限验证

* 上传头像、修改密码、修改个人信息

* 多语言

* 角色授权

* 用户角色分配

* 组织机构添加、用户分配

* 导出excel

* 基于SignalR实时消息提醒

* 审计功能（Application日志存储 和 EntityChange日志）

* 工作流流程设计、发布

  工作流模型：使用gooflow模型、node顶点、line边，即有向图模型。采用邻接表和逆邻接表表示顶点和顶点直接的关系、使用规则定义条件流转和节点权限

* 工作流流转

# vs2017插件开发 - DDD代码生成器：

* [ABP前后端代码生成器查看](https://gitee.com/fq_chenzhen/abp_code_generator)

### 界面截图

* 组织机构
![组织机构](../../raw/master/_screenshots/organize.gif)

* 审计日志
![审计日志](../../raw/master/_screenshots/audit.gif)

* signalR消息提醒
![signalR](../../raw/master/_screenshots/signalR.gif)

* role角色权限管理
![role角色权限管理](../../raw/master/_screenshots/role.gif)

* 用户管理
![用户管理](../../raw/master/_screenshots/user.gif)

* 租户管理
![租户管理](../../raw/master/_screenshots/teant.gif)

* Oidc登录
![oidc](https://gitee.com/fq_chenzhen/Abp-Template-IdentityServer4/raw/master/images/oidc.gif)

* 流程设计
![流程设计](../../raw/master/_screenshots/flowDesign.gif)

* 请假单申请
![请假单申请](../../raw/master/_screenshots/applyFlow.gif)

* 请假单审批
![请假单审批](../../raw/master/_screenshots/verificationFlow.gif)
![请假单审批1](../../raw/master/_screenshots/verificationFlow2.gif)

* 流程不同意/驳回
![流程不同意/驳回](../../raw/master/_screenshots/verificationFlow3.gif)

* 代码生成器
 生成效果
![代码生成器生成的效果](../../raw/master/_screenshots/codeGen.gif)
 后端生成
![后端生成](https://gitee.com/fq_chenzhen/abp_code_generator/raw/master/images/codebuild-back.gif)
 前端生成
![前端生成](https://gitee.com/fq_chenzhen/abp_code_generator/raw/master/images/codebuild-front.gif)

* 地图展示
![地图展示](../../raw/master/_screenshots/map.gif)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)