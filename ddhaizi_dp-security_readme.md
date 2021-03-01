# dp-LTE
基于SSM框架的轻量级开发框架，已经完成基于角色的操作权限管理，对前后端进行封装，可快速实现CRUD的开发。项目采用Maven多模块构建，方便按需求进行模块化扩展。
### 传送门
- dp-LTE：[http://git.oschina.net/zhocuhenglin/dp-security/](http://git.oschina.net/zhocuhenglin/dp-security/)
- dp-PRO：[http://git.oschina.net/zhocuhenglin/dp-pro](http://git.oschina.net/zhocuhenglin/dp-pro)
- dp-GEN：[http://git.oschina.net/zhocuhenglin/dp-generator](http://git.oschina.net/zhocuhenglin/dp-generator)
- 项目文档：[http://dp-dev.mydoc.io/](http://dp-dev.mydoc.io/)
- 最新进展详情，请关注 dp-PRO 项目
###  :fa-thumbs-o-up: 更新说明

1. 加强数据参数校验，删除时含有子节点数据不可删除进行合法性检查（已更新）
2. 基于机构管理的数据权限（机构管理、数据权限）（完成待更新）
3. 行政区域管理，数据来自国家统计局2017-03-10发布最新行政区域代码数据（已更新）
4. 修复左侧菜单超出高度隐藏bug，更新为超出高度出现滚动条（已更新）
5. 新增定时任务模块（已更新）
6. 基于此项目结构的代码生成器，生成java、html、js文件（开发中）
7. 项目文档：[http://dp-dev.mydoc.io/](http://dp-dev.mydoc.io/)

### 项目介绍
- 一个轻量级的Java快速开发框架，能快速开发项目并交付（规划后期不定时发布更新）
- 友好的代码结构及注释，便于阅读及二次开发，命名规范和工程分层规约参考阿里巴巴JAVA开发规范
- 前后端开发封装，快速实现CRUD开发（规划通过velocity模板生成部分代码）
- 基于角色的权限管理，细分到按钮权限（规划将支持数据权限）
- 基于Maven模块化开发，可快速扩展个性化业务模块
### 技术方案
- 核心框架：Spring
- WEB框架：SpringMVC
- ORM框架：Mybatis
- 安全框架：Shiro
- 模板框架：velocity（支持freemarker、jsp等其他自定义视图）
- 主页框架：adminLTE(Bootstrap)
- JS框架：vue.js
- 表格插件：bootstrap-table
- 树形表格：tree-grid(基于bootstrap扩展)
- 树形插件：ztree
- 弹窗组件：layer
- 表单校验：validator
### 项目结构
- dp-security：父级（聚合）模块
- dp-common：公共通用模块
- dp-shiro：权限模块（操作权限）
- dp-orm：数据持久模块
- dp-quartz：定时任务模块
- dp-web：前端界面
- dp-base：基础模块，目前包含行政区域、通用字典和系统日志功能模块
### 交流反馈
- os-china仓库：[http://git.oschina.net/zhocuhenglin/dp-security/](http://git.oschina.net/zhocuhenglin/dp-security/)
- 项目文档：[http://dp-dev.mydoc.io/](http://dp-dev.mydoc.io/)
- 作者主页：[http://www.chenlintech.com/](http://www.chenlintech.com/)
- 交流QQ群：553461392
- 如果对项目感兴趣，请Watch、Star项目，后期会不定时发布更新
### 命名规范（参考阿里巴巴Java开发手册）
-  获取单个对象的方法用 get 做前缀
-  获取多个对象的方法用 list 做前缀
-  获取统计值的方法用 count 做前缀
-  插入的方法用 save(推荐) 或 insert 做前缀
-  删除的方法用 remove(推荐) 或 delete 做前缀
-  修改的方法用 update 做前缀
### 应用分层（参考阿里巴巴Java开发手册）
![image](http://chenlintech.com:8080/statics/common/0.png)
### 项目演示
- 演示地址：[http://dp.chenlintech.com](http://dp.chenlintech.com)
- 账号密码：admin / 1
### 运行效果
![image](http://chenlintech.com:8080/statics/lte/1.png)
![image](http://chenlintech.com:8080/statics/lte/2.png)
![image](http://chenlintech.com:8080/statics/lte/3.png)
![image](http://chenlintech.com:8080/statics/lte/4.png)
![image](http://chenlintech.com:8080/statics/lte/5.png)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)