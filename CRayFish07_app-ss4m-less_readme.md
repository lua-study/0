## app-ss4m-less 
#### 特性说明：
##### 1、总体说明：
- 基于SSM框架构建整合的后台基础版本。(简单封装)
- 其中Spring 采用4.2.9.RELEASE版本，mybatis采用3.2.8版本。

##### 2、MVC风格
- 支持传统的Spring MVC + JSP的配置
- 支持json格式的restful风格MVC（json日期格式转化已做全局处理）
- 支持jsonp请求（默认只处理@RestController注解的控制器)

##### 3、数据库特性：
- 支持主数据库、日志数据库分别配置和使用（两者数据库类型可以不一致）
- 支持容灾情况，主数据库自动切换到后备数据库

##### 4、分布式组件：
- 分布式缓存Redis集群支持2.8x+（Spring Data Redis）；（cache_config.properties）
- 分布式会话管理（Spring Session）支持；（涉及配置文件：web.xml--springSessionRepositoryFilter、spring-session.xml）

##### 5、数据处理
- 集成分页组件laypage、上传组件ajaxfileupload

##### 6、工具类
- 提供Spring bean工具类：SpringContextUtils
- 提供获取http 请求、响应、session的工具类：HttpRequestContextUtils
- 提供数据库操作Mybatis的工具类：DaoUtils
- 提供配置文件读取工具类：PropertiesUtils
- 提供哈希加密（MD5、SHA-1、SHA-256）算法工具类：HashUtil
- 提供FTP/SFTP上传下载工具类：FTPUtils

#### 数据源配置
##### 配置步骤1
以Tomcat为例：Content.xml配置数据源：jdbc/appdb、jdbc/reservedb、jdbc/logdb

##### 配置步骤2
修改param.properties相关参数。
		
#### demo sql:
##### 主数据库SQL
-- Create table
create table SYS_USER
(
  USER_ID                NUMBER(10) not null,
  USER_NAME              VARCHAR2(64),
  PASSWORD               VARCHAR2(64),
  EFF_DATE               DATE,
  EXP_DATE               DATE,
  STATUS_CD              VARCHAR2(8),
  STATUS_DATE            DATE,
  CREATE_DATE            DATE,
);
alter table SYS_USER add primary key (USER_ID);

##### 日志数据库SQL
-- Create table
create table SYS_OPER_LOG
(
  LOG_ID      NUMBER(30) not null,
  USER_ID     NUMBER(10),
  ACTION_TYPE VARCHAR2(4),
  ACTION_DESC VARCHAR2(256),
  RESULT_CODE VARCHAR2(10),
  RESULT_MSG  VARCHAR2(1000),
  CLIENT_IP   VARCHAR2(20),
  LOG_DATE    DATE
);
-- Create/Recreate primary, unique and foreign key constraints 
alter table SYS_OPER_LOG
  add constraint PK_SYS_OPER_LOG primary key (LOG_ID);

#### demo
里面包含了各类使用的demo。入口为index.html。
- Demo采取的是Controller、Service、DAO分层。
其中Controller建议只负责做简单的转发，Service做具体业务逻辑处理，DAO只负责简单的访问数据库。
- Demo可以根据需要修改或删除，请注意的是注意从相应的配置文件中移除相关配置。


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)