# Young V3.0
## 平台简介
　　Young V3.0基于Springboot2.x，采用前后端分离架构，集成了单点登录，统一权限，文件管理，代码生成，监控运维等模块，可支持Mysql，Oracle，PostgreSql等数据库，提供了单体和cloud两套解决方案。希望通过科学合理的基础平台设计，使代码开发更快速，更优雅，更易扩展，更易维护。

　　最新内容请关注：[WangJY's Blog](http://www.imrookie.cn/ "WangJY's Blog")

### 技术选型
- 主框架：SpringBoot2.x，Mybatis
- 数据库：Mysql，Oracle，PostgreSql
- 连接池：Druid
- 缓存：Ehcache3.5，redis
- 工具组件：slf4j，log4j2，jackson，poi
- 前端组件：Bootstrap3.3.7，echarts，jquery，jo，layer，zTree，UEditor
- 云架构：eureka，feign，zuul，hystrix

### 部分功能清单
- 用户管理
- 组织机构管理：单位之间数据隔离
- 资源管理：菜单，按钮，页面资源，逻辑资源
- 角色管理：管理范围（数据权限），角色共享，授权
- 权限：含用户，机构，角色等数据权限和各类资源权限
- 单点登录：SSO，安全认证，验证码，数据加密，黑名单限制，防暴力破解，自动冻结
- 会话管理：支持踢人下线
- 登录日志：纪录了IP，设备，时间，是否成功等信息
- 代码生成：易操作的代码配置界面，从前端（视图，表单）到后端（controller，service，mapper，动态sql）再到数据库文档一条龙；后端支持CRUD，导入，导出，动态sql；前端细粒度到字段级别，支持显示控制，查询条件设置，控件选择（文本/时间/联想输入/下拉框/动态下拉框等），表单验证（可支持自定义正则），只读控制，默认值设置，输入提示等。
- 监控运维：支持在线查看实时日志打印和历史日志，日志文件下载
- 分布式链路追踪：支持自定义日志收集器，打通从前端发起请求到服务端返回的整条链路，可根据traceId查询结构化的链路信息，提供可视化的链路耗时分布
- 方法级监控：方法级别的监控，提供可视化性能监控，可用率监控，分钟级的调用量监控
- 实时JVM：堆栈信息，垃圾回收情况，线程信息
- 连接池：内嵌Druid连接池监控，帮助开发者进行sql调优
- 文件服务：上传，下载，预览等
- Swagger支持：在线的API文档描述
- DAL统一数据服务层，统一缓存服务等开放式接口

### 代码结构
- young-interfaces：接口模块，包含各个服务对外提供的接口和实体类；属于最底层的模块，各个服务都依赖此包。
- young-common：公共模块，包含工具类，mvc配置，dal（数据服务），客户端包（例如日志收集器，ums客户端等），核心pom依赖等，属于一些公共能力的聚合，作为基础包被上层服务依赖。
- young-static：静态资源模块，html/js/css/图片等前端资源。
- young-fs：文件服务，提供上传下载等和文件相关的服务。
- young-ums：统一用户，包含组织机构，用户，登录，权限等。
- young-cms：内容管理，目前提供代码生成，数据库文档生成，表结构迁移等服务。后续规划处理在线视图/表单/门户等动态资源构建和下发。
- young-monitor：监控服务，包含分布式链路追踪，方法性能监控，jvm监控，统一日志查询等功能。
- young-weixin：微信公众号模块，负责微信公众号的服务对接，目前处于规划阶段。
- young-app：应用层，单体应用可以直接在此模块进行开发（或者自行创建项目），根据项目实际情况引入上面的模块（部分或全部），开发完成后直接打包发布。
- young-cloud：微服务层，对上面的核心模块微服务化，提供基于spring cloud的微服务解决方案。（作者力荐）

### 功能截图

 ~ | ~ |
 ----- | ---- |
![登录](https://gitee.com/I_M_ROOKIE/mypic/raw/master/pic/登录.png "登录") | ![用户管理](https://gitee.com/I_M_ROOKIE/mypic/raw/master/pic/用户.png "用户管理")
![资源编辑](https://gitee.com/I_M_ROOKIE/mypic/raw/master/pic/资源编辑.png "资源编辑") | ![按钮管理](https://gitee.com/I_M_ROOKIE/mypic/raw/master/pic/按钮.png "按钮管理")
![登录日志](https://gitee.com/I_M_ROOKIE/mypic/raw/master/pic/登录日志.png "登录日志") | ![代码生成](https://gitee.com/I_M_ROOKIE/mypic/raw/master/pic/代码生成.png "代码生成")
![链路追踪](https://gitee.com/I_M_ROOKIE/mypic/raw/master/pic/链路.png "链路追踪") | ![方法执行详情](https://gitee.com/I_M_ROOKIE/mypic/raw/master/pic/方法详情.png "方法执行详情")
![链路图](https://gitee.com/I_M_ROOKIE/mypic/raw/master/pic/链路图.png "链路图") | ![方法性能监控](https://gitee.com/I_M_ROOKIE/mypic/raw/master/pic/方法性能监控.png "方法性能监控")
![实时日志](https://gitee.com/I_M_ROOKIE/mypic/raw/master/pic/实时日志.png "实时日志") | ![历史日志](https://gitee.com/I_M_ROOKIE/mypic/raw/master/pic/历史日志.png "历史日志")
![JVM监控](https://gitee.com/I_M_ROOKIE/mypic/raw/master/pic/jvm.png "JVM监控") | ![文件管理](https://gitee.com/I_M_ROOKIE/mypic/raw/master/pic/文件.png "文件管理")

## 系统设计
### 统一用户UMS
### 登录流程
1. 用户请求资源若未登录则跳转登录页;
2. 进入登录页后会发起第一次请求: 安全认证;
3. 服务端下发安全认证信息(会话ID,时间戳,密钥等);
4. 客户端拿到安全认证后, 发起第二次请求: 获取验证码;
5. 服务端下发验证码;
6. 用户输入账号/密码/验证码,点击登录,发起第三次请求: 登录认证;
7. 服务端校验验证码和账号密码, 校验通过则登录成功;
8. 登录成功后重定向到资源页;



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)