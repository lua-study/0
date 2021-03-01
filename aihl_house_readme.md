### 代码生成器
### mybatis-plus代码生成器
CodeGenerator 
* mybatis-plus代码生成器: https://mp.baomidou.com/guide/generator.html 
### mybatis-plus多数据源
* mybatis-plus多数据源 ：https://mp.baomidou.com/guide/dynamic-datasource.html
* mybatis-plus多数据源集成druid ： https://gitee.com/baomidou/dynamic-datasource-spring-boot-starter/wikis/pages?sort_id=1030570&doc_id=147063
### LocalDateTime与mysql日期类型的交互（基于mybatis）
+ 添加依赖
`  
           
               org.mybatis 
               mybatis-typehandlers-jsr310 
               1.0.1 
           `
+ mybatis-plus使用jdk8的LocalDateTime 查询时报错
`org.springframework.dao.InvalidDataAccessApiUsageException: Error attempting to get column 'update_time' from result set.  Cause: java.sql.SQLFeatureNotSupportedException
; null; nested exception is java.sql.SQLFeatureNotSupportedException`
  根本问题 MybatisPlus 或 mybatis-spring-boot-starter 的版本引用的是mybatis3.5.1  降为3.5.0或以下

### swagger2 接口文档
* swagger2 : https://swagger.io


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)