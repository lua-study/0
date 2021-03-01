## MiniJdbc - 介绍&使用说明 ##
sxjun @2016-01-15 

使用MiniJdbc的项目：[LarvaFrame](http://git.oschina.net/sxjun1904/LarvaFrame)(供参考)

该项目仍在持续完善中...

## 一、MiniJdbc介绍

**1、MiniJdbc：**针对spring jdbc的一些不方便的地方，做了一些封装，大小写不敏感，简化了日常的开发工作。
基于spring jdbc的RowMapper自动实现对象映射，大部分功能已经由spring jdbc实现了。

**2、数据类型的设计：**集成了JFinal和SBORM的优点,对字段的大小写不敏感，对强类型实体、弱类型实体和非实体的支持。

**3、统一的接口：**强类型、弱类型采用统一的数据库接口，例如：可以采用统一的insert方法报错强类型或弱类型数据。

**4、数据库的支持：**目前已经支持MySql、SqlServer、Oracle数据库，屏蔽了数据库的语法差异。

**5、强弱类型完美结合：**例如，在数据库插入一个用户：
```java
//强类型编程
User user = new User();//新建User对象，表名和主键在实体注解中定义
user.setName("admin").setPassword("000000");//设置数据
dao.insert(user);//保存用户

//弱类型编程
Record record = new Record("user","id");//新建记录对象，构造函数传表名和主键
record.set("name", "admin").set("password", "000000");//设置数据
dao.insert(record);//保存用户
```

**6、大小写不敏感：**弱类型编程中，对应表、字段的大小写不敏感。
```java
//设置name字段,可以小写
record.set("name", "admin");
//也可以大写
record.set("NAME", "admin");
//还可以随意写
record.set("NaMe", "admin");
```
##二、关于数据类型
MiniJdbc在设计时考虑到3种数据类型：强实体，弱实体，非实体。

**强、弱实体的区别**：强、弱实体都属于实体（BaseEntity），但强实体包含成员变量和正常的get/set方法，而弱实体则没有成员变量，且get/set方法与强实体也有区别。强实体继承StrongEntity类，弱实体继承WeakEntity类。

**弱实体和非实体区别**：非实体可以只能通过get("name")的方式获取值，而弱实体可以通过user.getName()的方式获取值。

***强实体***
```java
@Entity(table="users", id = { "id" },strategy=StrategyType.UUID)
public class User extends StrongEntity implements Serializable {
	@Column("id")
	private String id;
	@Column("name")
	private String name;

	public void setId (String id) {
		this.id = id;
	}
	public String getId () {
		return this.id;
	}
	public void setName (String name) {
		this.name = name;
	}
	public String getName () {
		return this.name;
	}
}
```

***弱实体***
```java
@Entity(table="users", id = { "id" },strategy=StrategyType.UUID)
public class User extends WeakEntity implements Serializable {
	public User setId (String id) {
		super.set("id", id);
		return this;
	}
	public String getId () {
		return super.get("id");
	}
	public User setName (String name) {
		super.set("name", name);
		return this;
	}
	public String getName () {
		return super.get("name");
	}
}
```
####实体注解说明####
**Entity**，配置对应的table和id值，以及策略，如果不配置需要在开发时手动设置；

***table***(String)：设置数据库表名（必填）;

***id***(String[])：设置数据库主键（必填）;

***strategy***(StrategyType)：主键的生成策略，目前支持如下策略;

    StrategyType.NULL 默认需要手动设置主键值
    
    StrategyType.AUTO 主键值自动增长
    
    StrategyType.UUID 自动生成system.uuid作为主键
    
***ignore_field***(String[])：插入、修改都要排除的数据库字段;

***ignore_insert_field***(String[])：插入时要排除的数据库字段;

***ignore_update_field***(String[])：更新时要排除的数据库字段;

***not_null_field***(String[])：不许为Null的字段.


##三、MiniDao全部接口
接口中强类型和弱类型都使用统一的DAO接口；
[Record.class(弱类型);BaseEntity.class(强类型基类)]
```java
//插入数据
public   int insert(T record);
//删除数据
public   int delete(T record);
//删除数据
public int deleteById(Class  clazz, Object primaryKey);
//更新数据
public   int update(T record);
//执行sql语句
public int execute(String sql, Object... paras);
//根据ID查找单个实体
public   T findById(Class  clazz, Object primaryKey);
//查找单条记录
public   T find(String sql, Class clazz, Object... args);
//查找一个list
public   List  findList(String sql, Class clazz, Object... args);
//分页查找一个list
public   List  paginate(String sql,int pageNumber, int pageSize, Class clazz, Object... args);
//获取分页Record数据
public   PageResult  paginateResult(String sql, int pageNumber, int pageSize, Class clazz, Object... args);
```

## 四、使用说明

###1、配置规范
**配置文件**
***datasource配置包括3部分***：扫描包、数据源、动态数据源，和普通的spring配置一致；  
(连接池使用看个人喜好): 
```java 
 
 

 
 
	     
	     
	     
	     
	     
	     
	     
	     
	     
	     
	     
	     
	     
	     
 

 
 
	  
	 
         
             
         
     
 
```

####动态数据源配置说明####
***defaultTargetDataSource***：配置默认数据源；  
***targetDataSources***：配置数据源，key为数据源名称（任意值），value-ref指向数据源；
***entityPackage***：配置实体所在的包，多个包用逗号分隔；

####配置扫描说明####
主要功能是初始化Entity的RowMapper，以及table、id等映射；  
```java
 
 
```
如下配置如果配置了则会在初始化的时候将实体信息加载到内存，如果不配置则会动态加载到内存（为提高程序启动的效率，建议开发阶段不要配置）
```java
 
 
	 
 
```

##五、例子（参考代码中的example包，可以使用user.sql创建测试数据库及表结构）

**增删改的代码示例：**
```java
/**
 * 测试插入强类型实例User
 */
public static int testInsert() {
    User user = new User();
    user.setCreateTime(new Date()) .setName("username") .setType(new Random().nextInt(5));
    return dao.insert(user);
}

/**
 * 测试插入强类型实例Record
 */
public static int testInsert2() {
    Record record = new Record("users","id");
    record.set("id", new Random().nextInt(100)) .set("name", "username") 
    .set("type", new Random().nextInt(5)).set("password", "000000");
    return dao.insert(record);
}

/**
 * 更新强类型实例
 * @return
 */
public static int testUpdate() {
    User user = new User();
    user.setName("hello_update");
    return dao.update(user);
}

/**
 * 更新弱类型记录
 * @return
 */
public static int testUpdateRecord() {
    Record record = new Record();
    record.setTableName("users");
    record.setPrimaryKeys("id");
    record.set("id", "8").set("name", "record_update");
    return dao.update(record);
}

/**
 * 删除强类型实体
 * @return
 */
public static int testDelete() {
    User user = new User();
    user.setId("1");
    return dao.delete(user);
}

/**
 * 删除弱类型记录
 * @return
 */
public static int testDeleteRecord() {
    Record record = new Record();
    record.setTableName("users");
    record.setPrimaryKeys("id");
    record.set("id", "8");
    return dao.delete(record);
}
```
**查询分页代码示例：**
```java
/**
 * 无参强类型分页
 */
public static List  testGetPage() {
    String sql = "select * from users where id   users = dao.paginate(sql, 2, 2, User.class);
    return users;
}

/**
 * 有参强类型分页
 */
public static List  testGetPage2() {
    String sql = "select * from users where id   users = dao.paginate(sql, 2, 2, User.class, 18);
    return users;
}

/**
 * 无参弱类型分页
 */
public static List  testGetPage3() {
    String sql = "select id,name from users where id   testGetPage4() {
    String sql = "select id,name from users where id < ? order by id desc";
    return dao.paginate(sql, 2, 2, Record.class, 88);
}
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)