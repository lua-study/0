#fand(方道基础平台)


1、主体基于spring、 spring jdbc、spring mvc的极简式封装。
 
2、持久层在 spring jdbc的基础上封装为支持通过sql标识自动获取到动态sql、sql存储到文件中方便后期维护、按业务规则自动路由到不同的数据源(读写分离、垂直和水平切分)、多数据库类型混用。
 
3、封装开发企业级应用所需的基础构件：数据字典管理、多语言管理、权限管理、缓存管理、流程管理、用户管理、部门管理、模板管理等等。
 
4、安全的持续改进:禁止跨站点提交、防止sql注入、防止com/css/c.js注入、核心业务加密存储...。
 
5、功能的持续改进:同域名或跨域名的单点登录支持、excel导入及导出、加密数据的搜索、对群集的支持(文件上传到到文件服务器、ftp服务器或记录服务ip地址，方便文件的下载)、定时服务的监控及重试、遵循AMD规范解决前端JS依赖、集成工作流引擎Activiti，支持在线编辑流程图并开发通用任何工作流引擎的配置管理及历史记录管理、...。
 
6、性能的持续改进:对群集的支持(避免同时在多个服务上同时执行同一个定时服务、调用短信接口及其它外部接口)、模板解析二级缓存、用内存数据库支持复杂权限的查询、前端使用阿里的seajs按需加载js及css、...。
 
7、为演示这些基础构件的使用，在examples中将基于这个基础开发平台开发：办公自动化系统(oa)、内容管理系统(cms)、人力资源管理系统(hrm)、...。
 
8、完善的文档支持，后期将提供基于PowerDesigner的全套文档(需求、概念、物理、流程、...)及必要的开发手册(pdf、html、chm)。
 
8、代码生成支持，生成po、dto、vo、dao、service、validator、controller这几层的实用代码，开发时只需写具体的业务规则。
  
 
	注意
 
1、源代码使用lombok精简了代码，导入源代码项目之前请确认也配置好lombox。官网地址为：http://projectlombok.org/ 
2、最新源代码在分支dev-yaoHT中。多人开发时，开发完成后，多个dev-*合并到分支test中集中测试，测试通过后才合并到主分支master中。 
3、历史版本在tags中。
  
 
	需求文档
 
https://git.oschina.net/fand/fand/blob/master/docs/fand.rqm
  
 
	概念数据模型
 
https://git.oschina.net/fand/fand/blob/master/docs/fand.cdm
  
 
	物理数据模型
 
https://git.oschina.net/fand/fand/blob/master/docs/fand.pdm
  
 
	Oracle 建表脚本
 
http://git.oschina.net/fand/fand/tree/demo/fand-web/src/main/resources/sql/Oracle/create.sql
  
 
	数据持久层
 
https://git.oschina.net/fand/fand/tree/master/modules/fand-persistent
  
 
	基本功能实现
 
https://git.oschina.net/fand/fand/tree/master/apps/fand-platform-webapp
  
 系统启动初始化数据(数据字典、导航菜单、全局变量...) 
https://git.oschina.net/fand/fand/blob/master/apps/fand-platform-webapp/src/main/resources/common/applicationContext-InitData.xml
  
 
	致立于复杂问题简化，提供最佳解决方案
 
1、持久层动态sql是基于freemarker表达式，比mybatis的ognl表达式更加强大，在这个基础上可以在sql中使用自定义标签或直接使用静态方法。可以做到在sql上控制业务数据权限和字段内容显示权限等。做到sql片断复用、缓存等(freemarker本身就支持，不需另外封装)。 
 
2、持久层sql文件是做为freemarker模板文件存放，这种模式为多种数据库混用提供了便利性。在spring中配置时，可以给templateLoaderPaths属性配置多个路径，比如：classpath:/sql/Oracle,classpath:/sql/MySQL，在持久层通过sql相对路径调用时，先从/sql/Oracle目录开始找，找不到时自动去/sql/MySQL目录找。 
 
3、数据源路由配置，在配置有多个数据源（可以是不同类型mysql、oracle等）后，支持配置路由，通过持久层调用的sql文件路径，自动路由到不同的数据源中。路由规则配置有多种配置方式，可支持读写分离、一主多从，多主多从、数据库群集分组等模式。不存在数据持久层工作量的增加，当调用不需传参数的sql时，只需指定sql相对路径就行。 
 
4、动态切换数据源，在配置有数据源规则时。可结合定时任务做到数据源计划性切换；可结合数据服务器监控做到数据源故障性切换；可结束业务规则做到区域性切换（比如用户登录后，对应用户的组织有独立的数据库，对应当前登录者的访问自动切换到对应的数据源）。 
  
 
	多数据源配置案例
 
https://git.oschina.net/fand/fand/blob/master/apps/fand-platform-webapp/src/main/resources/applicationContext-DataSource.xml
  
 
	多数据源路由案例
 
https://git.oschina.net/fand/fand/blob/master/apps/fand-platform-webapp/src/main/resources/applicationContext-Router.xml
  
 
	持久层使用案例
 
https://git.oschina.net/fand/fand/blob/master/apps/fand-platform-configuration/src/main/java/com/fand/platform/configuration/dao/DictionaryJdbcDao.java
  
https://git.oschina.net/fand/fand/tree/master/apps/fand-platform-webapp/src/main/resources/sql/oracle/configuration/dictionary

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)