# JSite 后台管理系统·快速开发框架

### 官网
官网、在线演示 http://jsite.org.cn

在线文档地址 http://doc.jsite.org.cn

#### 如果你喜欢这个项目，那就点击一下右上方的【Star】以及【Fork】，支持一下我们吧！
### 演示系统账号密码
1. 演示系统账号1：jsite 密码：admin
2. 演示系统账号2：dept 密码：123456
3. 演示系统账号3：jsitehr 密码：123456
4. 说明：上面3个账号角色分别为系统管理员、部门经理、HR。
5. 请假流程发起后，流程下一步自动流转到“部门经理”角色账号下，部门经理审批后自动流转到“hr角色账号下”。测试时，需要登录不同角色账号，在代办任务中查看流程代办任务。

### 平台介绍
1. 本框架是在 jeesite1.x 项目基础上，进行了框架重构，改造升级而来，在此特别感谢原作者的贡献！！
2. 框架基于Maven构建，拆分成多个子模块，层次结构清晰。可用于所有Web应用，如企业后台管理系统、OA系统、CMS、CRM等。
3. 框架本身集成了最新的 **Flowable工作流引擎** https://www.flowable.org/ ，内置了流程流程设计器moduler，有完整的流程管理模块，可以轻松实现流程的在线设计、部署，流程发起、流程流转跟踪等一系列OA办公业务。
4. 框架主模块包含：系统管理、流程管理、在线办公、文件管理、代码生成。系统管理子模块--用户管理、机构管理、区域管理、菜单管理、角色管理、字典管理、日志查询、连接池监视，实现权限精细控制，支持跨部门、跨公司数据权限授权。
5. 框架支持前后端基础代码自动生成，免去重复劳动。

### 软件架构·技术选型
#### 环境要求
1. JDK 8
2. Tomcat 8
3. Apache Maven 3.x
#### 基础框架
1. Spring Boot 2.0.4
2. Apache Shiro 1.4
3. Spring Framework 5.0.8
4. Jackson 2.9.5
5. Flowable 6.4.0 (工作流引擎)
6. Redis 2.9.0
#### 持久层
1. Alibaba Druid 1.0.18
2. Apache MyBatis 3.4.6
3. Hibernate Validation 6.0
#### 视图层
1. Beetl 2.8.6
2. CSS框架：Bootstrap 4  CoreUI
3. 其他组件：jquery 3  jquery-zTree 3.5  jquery-toastr  jquery-validation1.19.0  layer 3.1 webuploader  select2.4.0 cropper3.1.3

### 使用说明
1. 建议使用 IntelliJ IDEA 开发
2. 初始化数据库脚本在 jsite-web 的 resources/db/ 目录下，详细步骤请查阅 [JSite Docs](http://doc.jsite.org.cn)
3. 数据库字符集：utf8   排序规则：utf8_bin
4. 初次运行项目，需要修改jsite-web模块下config/jsite-web.properties配置文件中的数据库连接配置！
### 系统展示
登录
![image](https://gitee.com/baseweb/JSite/raw/master/img/%E7%99%BB%E5%BD%95.png)
主页
![image](https://gitee.com/baseweb/JSite/raw/master/img/%E4%B8%BB%E9%A1%B5.png)
Bootstrap-table 表格界面
![image](https://gitee.com/baseweb/JSite/raw/master/img/%E5%88%97%E8%A1%A8%E7%95%8C%E9%9D%A2.png)
流程设计器
![image](https://gitee.com/baseweb/JSite/raw/master/img/%E6%B5%81%E7%A8%8B-%E6%B5%81%E7%A8%8B%E8%AE%BE%E8%AE%A1%E5%99%A8.png)


### 参与贡献

1. Fork 本项目
2. 新建 Feat_xxx 分支
3. 提交代码
4. 新建 Pull Request

### 授权协议声明
1. 已开源的代码，授权协议采用 AGPL v3 + Apache Licence v2 进行发行。
2. 您可以免费使用、修改和衍生代码，但不允许修改后和衍生的代码做为闭源软件发布。
3. 修改后和衍生的代码必须也按照AGPL协议进行流通，对修改后和衍生的代码必须向社会公开。
4. 如果您修改了代码，需要在被修改的文件中进行说明，并遵守代码格式规范，帮助他人更好的理解您的用意。
5. 在延伸的代码中（修改和有源代码衍生的代码中）需要带有原来代码中的协议、版权声明和其他原作者规定需要包含的说明（请尊重原作者的著作权，不要删除或修改文件中的@author信息）。
6. 您可以应用于商业软件，但必须遵循以上条款原则（请协助改进本作品）。

### 获得支持

QQ群：881252801


![image](https://gitee.com/baseweb/JSite/raw/master/img/jsite-qrcode.png)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)