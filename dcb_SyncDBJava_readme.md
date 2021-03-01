  这一篇通过JAVA读取Excel，将Excel表结构同步到数据库中，并生成java实体类。与上一篇类似，这里只介绍类说明，具体实现，可查看源码。 
 
流程： 
1：初始化数据库--&gt;创建目标库--&gt;创建元数据表 
2：读取Excel--&gt;封装为JavaBean--&gt;添加不存在的表--&gt;修改变动的表--&gt;添加不存在的字段--&gt;修改变动的字段 
3：读取Excel--&gt;封装为JavaBean--&gt;生成相对应的java实体 
 
  同样，先介绍类结构:   
  
Column.java和Table.java：列和表的实体 
ConConfig.java：连接类的实体，包含用户名，密码和数据库地址 
 
ConnectionHelper.java：数据库连接操作工具类，包括测试连接、打开、关闭连接 
ExcelHelper.java：excel表操作工具类，用于将Excel表封装成javabean 
MssqlDBHelper.java：对应sqlserver底层操作类，包括建库、建表、同步表及将数据库中tableMate和columnMate封装成javabean 
 
SyncDbBiz.java 业务层，包括同步数据库和生成sql. 
MainWindow.java 操作界面. 
 
JavaCodeHelper.java：Java类操作的工具类，包括创建类、添加字段、添加方法、保存成.java文件等操作。 
TypeMapping.java：数据库类型与Java数据类型映射工具类 
EntityBuilderBiz.java：java实体生成业层,主要生成java类 
 
 Excel数据结构:  
  
 
 界面：  
  
 如果择选文件慢，在jvm中添加-Djxl.nogc=true.  
 
 生成的数据库结构：  
  
 
 
 生成的JAVA代码：  
  
 
 

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)