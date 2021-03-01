easy4net是一个轻量级orm框架，灵活在于可以自己编写复杂的SQL语句查询，简单在于几分钟内便能上手使用，并支持mysql, mssql, oracle, access数据库. easy4net技术QQ 群：162695864

**分页查询：**
* 1. 命名参数， ParamMap传参方式：
* 2. **注意**：对于Access这类使用OldDb，或者使用Odbc方式连接数据库的情况，没有命名参数，只有位置参数，所以参数添加的顺序必须跟参数在sql语句中出现的顺序一致
* 3. 支持多层嵌套查询自动分页功能。

***

```c#

int pageIndex = 1;
int pageSize = 3;
string strSql = "SELECT e.*, c.company_name FROM employee e INNER JOIN company c ON e.company_id = c.id WHERE e.name = @name";

ParamMap param = ParamMap.newMap();
param.setPageParamters(page, limit);
//分页时使用的排序字段，必填，请带上SQL表名的别名，如employee的为: e
param.setOrderFields("e.id", true);
param.setParameter("name", "LiYang");

DBHelper dbHelper = DBHelper.getInstance();
List  emList = dbHelper.Find (strSql, param);

```

**分页查询：**
* 1. 命名参数， ParamMap传参方式：
* 2. 返回总条数和数据集合的对象PageResult

***

```c#
public PageResult  findByPage(int page, int limit)
{
    DBHelper db = DBHelper.getInstance();

    String sql = "select * from store";

    ParamMap param = ParamMap.newMap();
    param.setPageParamters(page, limit);
    param.setOrderFields("id", true);

    PageResult  pageResult = db.FindPage (sql, param);

    return pageResult;
}


public class PageResult 
{
    ///  
    /// 分页查询中总记录数
    ///  
    public int Total {get; set;}

    ///  
    /// 分页查询中结果集合
    ///  
    public List  DataList {get; set;}
}
```


**查询单条记录：**
***

```c#

string strSql = "SELECT e.*, c.company_name FROM employee e INNER JOIN company c ON e.company_id = c.id WHERE e.name = @name";
ParamMap param = ParamMap.newMap();
param.setParameter("name", "LiYang");

Employee em = dbHelper.FindOne (strSql, param);

```

**普通查询：**
***
```c#

string strSql = "SELECT e.*, c.company_name FROM employee e INNER JOIN company c ON e.company_id = c.id";

List  emList = dbHelper.Find (strSql);

```


**新增：**
* 1. 新增后返回新增记录的主键id值
* 2. 主键id值已经自动填充到新增的对象entity中

***

```c#

//创建公司
Company company = new Company();
company.CompanyName = txtName.Text.Trim();
company.Industry = txtIndustry.Text.Trim();
company.Address = txtAddress.Text.Trim();

DBHelper dbHelper = DBHelper.getInstance();
dbHelper.Save (company);

if (company.Id > 0) {
    MessageBox.Show("创建公司成功！");
}


//新增员工
Company company = m_CompanyList[cbCompany.SelectedIndex]; 
Employee employee = new Employee();
employee.Name = txtName.Text.Trim();
mployee.Age = Convert.ToInt32(txtAge.Text.Trim());
employee.Address = txtAddress.Text.Trim();
employee.Created = DateTime.Now;
employee.CompanyId = company.Id;

DBHelper dbHelper = DBHelper.getInstance();
dbHelper.Save (employee);
if (employee.Id > 0)
{
    MessageBox.Show("新增员工成功！");
}

```


**批量新增：**
* 1. 主键id值已经自动填充到新增的对象entity中
* 2. 批量新增方法比手动循环多个对象然后调用新增性能高。

***

```c#

List  companyList = ...;
dbHelper.Save(companyList);
```


**修改：**

***

```c#
Company entity = new Company();
entity.Id = 1;
entity.Name = "百度";
dbHelper.Update(entity);
```


**批量修改：**
* 1. 批量修改方法比手动循环多个对象然后调用修改性能高。

***

```c#
DBHelper db = DBHelper.getInstance();
List  companyList = ...;
dbHelper.Update(companyList);
```


**删除：**
* 1. 按对象方式删除数据
* 2. 按主键id方式删除数据

***

```c#
Company company = m_companyList[i];
//remove a object
dbHelper.Delete(company);

//remove by id
dbHelper.Delete(company.Id);
```

**批量删除：**
* 1. 按对象方式删除数据
* 2. 按主键id方式删除数据
* 3. 批量删除比手动循环调用删除性能要高

***

```c#

//remove by object
List  companyList = ...;
dbHelper.Delete(companyList);

//remove by id
object[] ids = new object[]{1,2,3,4,5};
dbHelper.Delete(ids);
```



**数据库与C#对象映射关系配置：**

***

```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;  
 
namespace Easy4net.Entity  
{  
     [Table(Name = "company")] 
	 public class Company
	 { 
		[Id(Name = "id", Strategy = GenerationType.INDENTITY)]
		public int? Id{ get; set; } 

		[Column(Name = "company_name")]
		public String CompanyName{ get; set; }

        [Column(Name = "industry")]
        public String Industry { get; set; }

        [Column(Name = "address")]
        public String Address { get; set; } 

	 } 
}  


using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Text;  
namespace Easy4net.Entity  
{  
     [Table(Name = "employee")] 
	 public class Employee
	 { 
		[Id(Name = "id", Strategy = GenerationType.INDENTITY)]
		public int? Id{ get; set; } 

		[Column(Name = "name")]
		public String Name{ get; set; } 

		[Column(Name = "age")]
		public int? Age{ get; set; } 

		[Column(Name = "address")]
		public String Address{ get; set; } 

		[Column(Name = "created")]
		public DateTime? Created{ get; set; } 

		[Column(Name = "company_id")]
		public int? CompanyId{ get; set; }

        [Column(Name = "company_name", IsInsert = false, IsUpdate = false)]
        public String CompanyName { get; set; } 

	 } 
}   

```

**数据库连接配置 web.config中：**
* dbType中配置sqlserver, mysql, oracle来支持不同的数据库

***

```xml
 
 
   
     
     -->

     
     -->

     
     -->

     
     
     
     
     
     
     -->

     
     
     
     
     
     
     
     

   
    
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)