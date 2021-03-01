### 简介
---------------
jfinal-xsql-plugin是jfinal的一个动态SQL插件，用来简化Jfinal的ActiveRecord开发，统一管理SQL语句。遇到复杂SQL时也可以让你迎刃有余，该框架写法类似mybatis/ibatis，其实却完全不同，XSQL不是ORM框架，他是个根据规则条件动态生成SQL语句与对应预编译参数的利器，使用该框架也极度简单，框架本身只实现了foreach,isempty，isnotempty,isequal,isnoequal四类常用的规则，但他不仅仅如此，他允许外部注册任意规则。
之前有开发过另外一个jfinal动态SQL插件[http://git.oschina.net/h5lib/jsql](http://git.oschina.net/h5lib/jsql) 。这框架使用的是js语法，引用了rhino的js引擎，整体会比较大，渲染速度10000次在10秒左右，新插件渲染速度10000次在1秒左右，另外[http://www.jfinal.com/share/75](http://www.jfinal.com/share/75) 在这文章有人表示无法接受这种写法，顾重新搞了一个类似ibatis 通过XML标签来控制规则的插件。

###MAVEN导入
```
 
	 cn.fsdev 
	 jfinal-xsql-plugin 
	 2.2 
 
```

### 示例
-------------
#### 1、SqlConfig主配置文件：

```
 
	 
		 
	 
	  
	  
	  
 
```

配置文件中仅有statement 和 sqlmap 节点，其中statements节点用来配置自定义规则，sqlmap用来引入sqlmap文件。

#### 2、SqlMap配置文件

```
 
	 
	 
		select * from user t where
		 
			 
				#{id}
			 
		 
		 
			1 = 0
		 
		 
			1 = 2
		 
	 
	 
	 
		select * from a where a.id = ${id} and a.name = ${name}
	 
 
```
sqlmap文件中包括sqlmap节点，sql节点与sql的规则节点，sqlmap中namespace用来规定命名空间，sql节点用来管理具体sql,通过namespace+"."+id 来确定唯一一条SQL语句。
SQL语句文本中可用#{var} 和 ${var},两种形式引用变量，#{}为预编译,${}为SQL拼接。



#### 3、JfinalConfig中启用插件
>me.add(new XsqlPlugin("sql-config.xml",true));


#### 4、调用动态SQL
返回值为SqlArgs，SqlArgs中存放着sql语句，与参数列表。

> Map  map = new HashMap ();
map.put("ids", Arrays.asList(1,2,3));
SqlArgs sqlArgs = XsqlKit.getSqlArgs("a.sql1", map);

之后可以在ActiveRecord中无缝的使用下面方式执行SQL

>Db.find(sqlArgs.sql, sqlArgs.args);

#### 5、单独使用
有时我们需要通过JDBC单独使用可以参考 com.jfplugin.xsql.Test1 下的测试代码。

#### 6、详细文档

详细文档请关注官方网站：[http://www.fsdev.cn/](http://www.fsdev.cn/)

### 使用环境
-------------
虚拟机环境：JDK1.6+
Jfinal版本：基于2.2编译，理论可支持2.0+

官方网站：[http://www.fsdev.cn/](http://www.fsdev.cn/)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)