CodeGenerator
====
这是一个使用 Freemarker 和 Velocity 模板来生代码的工具。

本生成器只是将数据库中的表结构数据提取出来，然后将这份结构模型提交给模板引擎, 根据你自定义的模板生成你需要的代码。

##配置文件
```xml
     
     
         
             
             lib/mysql-connector-java-5.1.36-bin.jar 
         
         
         D:\temp 
         
         org.joy 
         
         test 
         
             
             
                 
                 ./entity.ftl 
                 
                 ${tagertProject}\src\${basePackage}\${moduleName}\entity\ 
                 
                 ${table.className}.java 
                 
                 UTF-8 
             
         
     
```

##模板中可用的变量和方法
    String       tagertProject       目标工程路径(代码保存的基准路径)
    String       basePackage         基准包
    String       moduleName          模块名
### table 对象
####属性
    String       tableName           表名

    String       tableType           表类型

    String       tableAlias          表别名

    String       remarks             表注释

    String       remarksUnicode      表注释转Unicode后的字符串

    String       className           实体类名

    String       javaProperty        实体类作为属性时的名字 == ${table.className?uncap_first}

    List  primaryKeys         主键集

    List  baseColumns         基本字段集

    List  columns             所有字段  == primaryKeys + baseColumns

    List     importedKeys        所有 importedKeys

    List     exportedKeys        所有 exportedKeys

    boolean      hasDateColumn       是否有日期类型字段

    boolean      hasBigDecimalColumn 是否有 BigDecimal 字段

    boolean      hasNotNullColumn    是否有非空的基本类型字段

    boolean      hasNotBlankColumn   是否有非空的 String 字段


### Column
####属性
    String  columnName        字段名

    boolean primaryKey        是否为主键

    boolean foreignKey        是否为外键

    int     size              字段长度

    int     decimalDigits     小数位长度

    boolean nullable          是否可空

    boolean autoincrement     是否自增

    boolean unique            是否唯一值

    boolean indexed           是否有索引

    String  defaultValue      默认值

    String  remarks           注释

    String  remarksUnicode    数字转Unicode后的字符串

    int     jdbcType          对应 java.sql.Types

    String  jdbcTypeName      对应jdbcType的名称

    String  javaProperty      属性名

    String  javaType          java类型，比如String、Long、Integer

    String  javaPrimitiveType java基本类型，如果不是基本类型时等同于 javaType

    String  fullJavaType      完整的Java类型，比如 java.lang.String

    String  getterMethodName  Get方法名

    String  setterMethodName  Set方法名

    boolean display           是否显示

    boolean searchable        是否可搜索

    String  dict              数据字典名


####方法
    boolean isString()        是否是字符串

    boolean isFloatNumber()   是否是浮点型，含Float、Double、BigDecimal

    boolean isIntegerNumber() 是否是整型，含Byte、Short、Integer、Long

    boolean isBigDecimal()    是否是BigDecimal类型

    boolean isBoolean()       是否是布尔类型

    boolean isDate()          是否有日期类型，含Date、Timestamp、Time

    boolean isBLOB()          是否有 BLOB、CLOB、LONGVARCHAR、LONGVARBINARY或VARBINARY

    boolean isPrimitiveType() 是否是基本类型

    boolean hasDict()         是否使用了数据字典

### Key
    String  pkTableName       PKTABLE_NAME

    String  pkColumnName      PKCOLUMN_NAME

    String  fkTableName       FKTABLE_NAME

    String  fkColumnName      FKCOLUMN_NAME

    Integer seq               KEY_SEQ


##作者
ptma@163.com


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)