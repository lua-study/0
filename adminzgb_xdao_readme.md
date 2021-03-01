#简介
这是一款小巧的DAO库，提供便捷的SQL执行方式。

额，其实我是看不惯Mybatis，由于我经常要写一些小项目，每次都要动用XML觉得好不爽，所以造了这个轮子。

特点：
  * 轻便，不管你在用哪种数据库管理工具，Hibernate、Mybatis等等，都能使用这个DAO库
  * 性能，底层非常薄的封装
  * 不支持事务，不支持大对象字段

#用法
初始化很简单：
```Java
XDAO.DataSource ds  = new XDAO.DataSource() {
    @Override
    public Connection getConnection() {
        // 这里返回一个Connection即可，建议换成你项目的连接池
        try {
            //示例是连接H2数据库
            Class.forName("org.h2.Driver");
            return DriverManager.getConnection("jdbc:h2:mem:play;MODE=MYSQL", "sa", "");
        } catch (Exception e) {
            e.printStackTrace();
        }
        return null;
    }
};

//设置数据源到XDAO
XDAO.setDataSource(ds);
```
比如项目里面有一个Model：
```Java
import javax.persistence.Column;
import javax.persistence.Table;

@Table(name="person") //可选，这个主要是用来解决Java类名和数据库表名不一致的问题
public class Person {

	public String id;

	@Column(name="name")
	public String name;

	@Column(name="create_time") //可选，这个主要是用来解决Java变量名和数据库列名不一致的问题
	public String createTime;
}

```

在项目里面新建一个PersonDAO接口：
```Java
@DAO //标记@DAO说明该接口是DAO接口，必须标记
public interface PersonDAO {

	@SQL("create table person(id varchar(255) not null, name varchar(255), create_time bigint(20) not null default 0)") //书写SQL语句，必须标记
	void createPersonTable();

	@SQL("insert into person(id, name, create_time) values(@1, @2, #now)") //@表示参数，会被替换成PreparedStatement的?
	void insertPerson(String id, String name);

	@SQL("insert into person(id, name, create_time) values(@1.id, @1.name, #now)") //@1.id 表示参数数值为方法的第一个参数的id属性
    void insertPersonObject(Person person);

	@SQL("select * from person where id=@1")
	Person findById(String id);

	@SQL("select * from person where id=@id and name=@name") //可以通过@SQLParam修改SQL语句的变量名
	Person findByIdAndName(@SQLParam("id")String id, @SQLParam("name")String name);

	@SQL("select * from person") //当方法返回类型为List，同时有标明泛型，DAO工具则会自动组装查询结果返回
	List  findAll();

	@SQL("select count(*) from person") //如果方法返回类型为Long或者Integer，DAO工具则会视为count查询
	long countAll();

    @SQL("insert into person(id, name) values(@1.id, @1.name)") //当SQL语句为更新、插入或者删除语句，且仅有一个List类型的参数，DAO工具则视为批量操作
    int[] batchInsert(List  persons);

    @SQL("select * from $1 where name = @2") //$表示宏，会完整替换SQL里面的语句
    Person findByTableAndName(String tableName, String name);

}
```

PersonDAO的调用：
```Java
//通过XDAO创建DAO实例
PersonDAO dao = XDAO.get(PersonDAO.class);
//可以直接调用接口的方法
dao.createPersonTable();
dao.insertPerson("abc", "steven");
Person person = dao.findById("abc");
List  persons = dao.findAll();
```

#修改日志输出
默认使用的是System.out和System.err，如果项目有自己的日志系统，则可以使用以下的代码：
```Java
XDAO.log = new XDAO.Logger(){
    //TODO 这里实现Logger的几个方法即可
};
```

#依赖
```xml
 
     commons-lang 
     commons-lang 
     2.5 
 
 
     javax.persistence 
     persistence-api 
     1.0.2 
 
```

#编译
```bash
mvn package
```
生成的jar在target目录中。

#More

* 有任何疑问，可以联系我 steven0lisa AT 163.com
* 有任何Bug以及需求，请提issue

_本项目尚未提交到Maven中央仓库，在不久后将会提交_

_Cheers_

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)