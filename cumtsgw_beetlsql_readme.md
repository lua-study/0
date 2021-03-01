# Beetlsql

* 作者: 闲大赋,Gavin.King,Sue,Zhoupan，woate
* 开发时间:2015-07
* 论坛 http://ibeetl.com
* qq群 219324263
* 当前版本 2.7.0 (222K), 另外还需要beetl 包
* 文档地址: http://ibeetl.com/guide/beetlsql.html 或者 https://git.oschina.net/xiandafu/beetlsql/attach_files 下载pdf 
* 单元测试使用  https://github.com/javamonkey/xlsunit 

# beetlsql 特点



BeetSql是一个全功能DAO工具， 同时具有Hibernate 优点 & Mybatis优点功能，适用于承认以SQL为中心，同时又需求工具能自动能生成大量常用的SQL的应用

* 开发效率

1. 无需注解，自动使用大量内置SQL，轻易完成增删改查功能，节省50%的开发工作量
1. 数据模型支持Pojo，也支持Map/List这种快速模型，也支持混合模型
1. SQL 模板基于Beetl实现，更容易写和调试，以及扩展
可以针对单个表(或者视图）代码生成pojo类和sql模版，甚至是整个数据库。能减少代码编写工作量

* 维护性

1. SQL 以更简洁的方式，Markdown方式集中管理，同时方便程序开发和数据库SQL调试。
1. 可以自动将sql文件映射为dao接口类
1. 直观灵活的支持支持一对一，一对多，多对多关系映射而不引入复杂的OR Mapping概念和技术。
1. 具备Interceptor功能，可以调试，性能诊断SQL，以及扩展其他功能
	
* 其他

1. 内置支持主从数据库支持的开源工具
1. 支持跨数据库平台，开发者所需工作减少到最小，目前跨数据库支持mysql,postgres,oracle,sqlserver,h2,sqllite.





# Hibernate,MyBatis,MySQL 对比

http://ibeetl.com/community/?/article/63  提供了12项对比并给与评分。在犹豫使用BeetlSQL，可以参考这个全面的对比文章



# 开发人员帅照

 

 

 


 

 




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)