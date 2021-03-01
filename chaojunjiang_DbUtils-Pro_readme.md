(English instruction please see [README-ENGLISH.md](README-ENGLISH.md) )  
## DbUtils-Pro
开源协议: [Apache 2.0](http://www.apache.org/licenses/LICENSE-2.0) 

DbUtils-Pro是一个建立于DbUtils上，并对其添加了一些功能的JDBC持久层工具，主要特点有：  
1.改进DbUtils的异常处理，将SQLException转化为运行时导常抛出，无需再手工捕获异常，这点类似于Spring的JdbcTemplate。 
2.添加Inline风格SQL支持，Inline风格利用Threadlocal方式传递SQL参数，具有简单、易维护的优点。关于Inline风格的详细介绍请参见[发现一种简单的SQL包装方法](http://www.iteye.com/topic/1145415)一文。  
3.添加SQL模板支持，将一些长SQL写在模板中是一种比较好的实践。DbUtils-Pro开放式架构设计为可配置使用任意第三方模板(调用setSqlTemplateEngine方法)，并自带一个简易的模板实现。  
4.改进数据源管理，可轻易配置使用第三方事务管理服务，如Spring声明式事务，抛弃怪异的TransactionAwareDataSourceProxy代理方式。 
5.原有的DbUtils方法100%保留，这很明显，因为DbPro类的父类是QueryRunner，对于已经使用DbUtils的项目，只需要将QueryRunner换成DbPro,即可无缝升级。  

DbUtils-Pro是作为jSqlBox项目的内核而开发的，它是一个承上(包装JDBC，支持多种SQL写法)启下(作为ORM项目内核)的项目，但它本身也是一个独立的工具，可以单独使用，其运行环境为Java6或以上。  
作为ORM项目的内核，DbUtils-Pro仅关注于改进JDBC操作的易用性，它不考虑对象映射、关联映射、跨数据库、分页等高级功能，这些高级功能属于jSqlBox项目负责的范畴。jSqlBox的设计理念是尽量将每个功能点设计成独立的小项目，隔离它们的相互依赖性，每个小项目都可以单独使用，整合在一起就成了jSqlBox，这与Hibernate之类将所有功能都打包在一起提供的持久层工具是不同的。目前在这一理念下已经开发或正在开发的工具项目有：  
1)jDialects,这是一个支持70多种方言的SQL分页和DDL工具，用于解决利用JDBC工具进行跨数据库开发的问题。  
2)jTransactions，这是一个将声明式事务作为单独的项目提供的工具集，目前包含TinyTx和SpringTx两个实现，今后将不断扩充。  
3)jBeanBox,这是一个纯粹的IOC/AOP工具，与Spring内核功能类似，但是更小、更易用, 是TinyTx的最佳伴侣。  
4)DbUtils-Pro,这是一个JDBC工具，支持多种SQL风格，即可单独使用，也可以作为ORM内核存在，起承上启下作用。  
5)jSqlBox这是一个基于ActiveRecord模式的ORM工具，主要作用是实现POJO对象的CRUD和支持基本的关联映射。  

### 如何引入DbUtils-Pro到项目?   
方式一：手工下载commons-dbutils-1.7.jar和dbutils-pro-1.7.0.jar并放置于项目的类目录。  
方式二：在项目的pom.xml文件中加入如下行：  
```
      
       com.github.drinkjava2   
       dbutils-pro   
       1.7.0   
    
``` 
DbUtils-Pro仅依赖于DbUtils, 如果使用Maven将自动下载对应其主版本号的DbUtils包commons-dbutils-1.7.jar。   
如果需要使用事务支持，还需要在pom.xml中添加jTransactions的依赖：
```
     
       com.github.drinkjava2 
       jtransactions 
       1.0.0 
     
```	


### 使用   
一. 以下示例演示DbUtils-Pro在同一个方法里，混合使用五种不同的编程风格。在无事务配置情况下，使用默认的连接管理器，工作在自动提交模式。  
    query(Connection, String sql, Object... params):   传统DbUtils方法, 需手工关闭Connection和捕获SQLException  
    query(String sql, Object... params):   传统DbUtils方法, 需手工捕获SQLException  
    nQuery(String sql, Object... params):  方法名以n打头，与JdbcTemplate类似，无需手工捕获SQLException  
    iQuery(String... inlineSQLs):   方法名以i打头，In-line风格，参数利用ThreadLocal织入到SQL中  
    tQuery(String... sqlTemplate):  方法名以t打头，Template风格, 利用模板管理SQL  
``` 
	@Test
	public void executeTest() {
		DbPro dbPro = new DbPro((DataSource) BeanBox.getBean(DataSourceBox.class));
		dbPro.setAllowShowSQL(true);
		User user = new User();
		user.setName("Sam");
		user.setAddress("Canada");

		System.out.println("风格1: 继承了旧的DbUtils风格，需手工关闭Connection和捕获SQLException");
		Connection conn = null;
		try {
			conn = dbPro.prepareConnection();
			dbPro.execute(conn, "insert into users (name,address) values(?,?)", "Sam", "Canada");
			dbPro.execute(conn, "update users set name=?, address=?", "Sam", "Canada");
			Assert.assertEquals(1L, dbPro.queryForObject(conn, "select count(*) from users where name=? and address=?",
					"Sam", "Canada"));
			dbPro.execute(conn, "delete from users where name=? or address=?", "Sam", "Canada");
		} catch (SQLException e) {
			e.printStackTrace();
		} finally {
			try {
				dbPro.close(conn);
			} catch (SQLException e) {
				e.printStackTrace();
			}
		}

		System.out.println("风格2: 继承了旧的DbUtils风格, 需手工捕获SQLException");
		try {
			dbPro.execute("insert into users (name,address) values(?,?)", "Sam", "Canada");
			dbPro.execute("update users set name=?, address=?", "Sam", "Canada");
			Assert.assertEquals(1L,
					dbPro.queryForObject("select count(*) from users where name=? and address=?", "Sam", "Canada"));
			dbPro.execute("delete from users where name=? or address=?", "Sam", "Canada");
		} catch (SQLException e) {
			e.printStackTrace();
		}

		System.out.println("风格3: nXxxx方法，无需捕获SQLException");
		dbPro.nExecute("insert into users (name,address) values(?,?)", "Sam", "Canada");
		dbPro.nExecute("update users set name=?, address=?", "Sam", "Canada");
		Assert.assertEquals(1L,
				dbPro.nQueryForObject("select count(*) from users where name=? and address=?", "Sam", "Canada"));
		dbPro.nExecute("delete from users where name=? or address=?", "Sam", "Canada");

		System.out.println("风格4: iXxxx方法，In-Inlne风格，可以将参数织入到SQL中");
		dbPro.iExecute("insert into users (", //
				" name ,", param0("Sam"), //
				" address ", param("Canada"), //
				") ", valuesQuesions());
		param0("Sam", "Canada");
		dbPro.iExecute("update users set name=?,address=?");
		Assert.assertEquals(1L, dbPro.iQueryForObject("select count(*) from users where name=" + question0("Sam")));
		dbPro.iExecute("delete from users where name=", question0("Sam"), " and address=", question("Canada"));

		System.out.println("风格5: In-Line风格的引申，半自动的ORM，POJO属性可以织入到SQL任意位置");
		dbPro.iExecute("insert into users (", inline0(user, "", ", ") + ") ", valuesQuesions());
		dbPro.iExecute("update users set ", inline0(user, "=?", ", "));
		Assert.assertEquals(1L,
				dbPro.iQueryForObject("select count(*) from users where ", inline0(user, "=?", " and ")));
		dbPro.iExecute(param0(), "delete from users where ", inline(user, "=?", " or "));

		System.out.println("风格6: tXxxx方法，模板风格支持");
		put0("user", user);
		dbPro.tExecute("insert into users (name, address) values(#{user.name},#{user.address})");
		put0("name", "Sam");
		put("addr", "Canada");
		dbPro.tExecute("update users set name=#{name}, address=#{addr}");
		Assert.assertEquals(1L,
				dbPro.tQueryForObject("select count(*) from users where ${col}=#{name} and address=#{addr}",
						put0("name", "Sam"), put("addr", "Canada"), replace("col", "name")));
		dbPro.tExecute("delete from users where name=#{name} or address=#{addr}", put0("name", "Sam"),
				put("addr", "Canada"));
	}
```		
 
二. 声明式事务演示
DbUtils-Pro本身并无事务功能，以下示例演示DbUtils-Pro与jTransactions整合进行事务操作。jTransactions项目是一个独立的事务工具，目前包含两个实现: TinyTx和SpringTx，TinyTx是一个只有四个类组成的微型声明式事务服务,适用于小型项目。SpringTx则是对Spring事务的简单包装。  
下面的示例包含了TinyTx声明式事务的配置、建表、插入数据、事务回滚的演示。此示例如需改成使用Spring事务，只需将1、2行和3、4行的注释互换，并在pom.xml中加入Spring的库依赖即可。
没有用到XML,只有一个注解@AopAround, 从这个例子可以看出jBeanBox与jTransactions的配置是多么的简单。
```
public class TxDemo {
	private static Class  tx = TinyTx.class;
	private static ConnectionManager cm = TinyTxConnectionManager.instance();
	// private static Class  tx = SpringTx.class;
	// private static ConnectionManager cm = SpringTxConnectionManager.instance();

	public static class TxBox extends BeanBox {
		{this.setConstructor(tx, BeanBox.getBean(DataSourceBox.class), Connection.TRANSACTION_READ_COMMITTED);
		}
	}

	DbPro dbpro = new DbPro((DataSource) BeanBox.getBean(DataSourceBox.class), cm);

	@AopAround(TxBox.class)
	public void tx_Insert1() {
		dbpro.nExecute("insert into users (id) values(?)", 123);
		Assert.assertEquals(1L, dbpro.nQueryForObject("select count(*) from users"));
	}

	@AopAround(TxBox.class)
	public void tx_Insert2() {
		dbpro.nExecute("insert into users (id) values(?)", 456);
		Assert.assertEquals(2L, dbpro.nQueryForObject("select count(*) from users")); 
		System.out.println(1 / 0);
	}

	@Test
	public void doTest() {
		System.out.println("============Testing: TxDemo============");
		TxDemo tester = BeanBox.getBean(TxDemo.class);
		try {
			dbpro.nExecute("drop table users");
		} catch (Exception e) {
		}
		dbpro.nExecute("create table users (id varchar(40))engine=InnoDB");
		Assert.assertEquals(0L, dbpro.nQueryForObject("select count(*) from users"));
		try {
			tester.tx_Insert1();// this one inserted 1 record
			tester.tx_Insert2();// this one did not insert, roll back
		} catch (Exception e) {
			System.out.println("div/0 exception found, tx_Insert2 should roll back");
		}
		Assert.assertEquals(1L, dbpro.nQueryForObject("select count(*) from users"));
		BeanBox.defaultContext.close();// Release DataSource Pool
	}
}
```

以上即为DbUtils-Pro全部文档，如有疑问，请下载并运行单元测试示例或查看源码(核心代码只有9个类)。

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)