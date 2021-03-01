# Dubonnet
A .NET Core v2.x ORM that runs on Dapper.

[![NuGet Downloads](https://img.shields.io/nuget/dt/Dubonnet.svg)](https://www.nuget.org/packages/Dubonnet/)


下载 [NuGet](https://www.nuget.org/packages/Dubonnet):

Thanks to 

 * https://github.com/getson/Dapper.Nona
 * https://github.com/henkmollema/Dommel
 * https://github.com/sqlkata/querybuilder

## Example

1. 安装 .NET Core v2.x 版本

2. 在命令行下以 webapi 为模板创建新项目
```bash
dotnet new webapi -n MyDubon -lang C#
cd MyDubon
#dotnet run #访问 https://localhost:5001/api/values/ 查看效果
```
并安装相关的依赖库
```bash
dotnet add package MySqlConnector --version 0.56.0
dotnet add package MySqlConnector.Logging.Serilog --version 0.38.0
dotnet add package Dapper --version 1.60.6
dotnet add package Dubonnet --version 2.2.0
```
3. 创建 MySQL 数据库，修改配置文件 appsettings.json 增加数据库连接

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Warning"
    }
  },
  "ConnectionStrings": {
    "DefaultConnection": "server=127.0.0.1;user id=dba;password=pass;port=3306;database=db_mobile;SslMode=none"
  },
  "AllowedHosts": "*"
}
```

4. 增加 Models 文件夹和两个文件 AppDbContext.cs 和 Mobile.cs
```bash
#复制 Dubonnet/src/Example/Models/ 下的这两个文件复制过来，
#并将 namespace 从 Dubonnet.Example 改为 MyDubon
#在 AppDbContext.cs 中 namespace 上面增加代码 using Dubonnet;
```
修改 Startup.cs 中 ConfigureServices() 增加依赖注入
```csharp
	using MyDubon.Models;
	// 其他代码 ...
	
    public class Startup
    {
    // 其他代码 ...
    
		public void ConfigureServices(IServiceCollection services)
		{
			var dsnMySql = Configuration.GetConnectionString("DefaultConnection");
			services.AddSingleton(new AppDbContext(dsnMySql));
			services.AddMvc().SetCompatibilityVersion(CompatibilityVersion.Version_2_1);
		}
	
	// 其他代码 ...
	}
```
（可选）对 Program.cs 作如下修改，自定义网址
```csharp
// 其他代码 ...
	
    public class Program
    {
    // 其他代码 ...
    
        public static IWebHostBuilder CreateWebHostBuilder(string[] args) =>
            WebHost.CreateDefaultBuilder(args)
                .UseUrls("http://127.0.0.1:5001")
                .UseStartup ();
```

5. 对 Controllers/ValuesController.cs 作如下修改
```csharp
	using MyDubon.Models;
    // 其他代码 ...
    
    [Route("api/[controller]")]
    [ApiController]
    public class ValuesController : ControllerBase
    {
        private readonly AppDbContext db;
        		
        public ValuesController(AppDbContext db)
        {
            this.db = db;
        }
        
        // GET api/values
        [HttpGet]
        public ActionResult > Get()
        {
            var area = db.Areas.Where("areacode", "0755").Get();
            return new string[] { area.province, area.city };
            //return new string[] { "value1", "value2" };
        }

        // 其他代码 ...
    }
```


 

## Base API

#### Retrieving entities by id
```csharp
var product = db.Products.Get(1);
```

#### Retrieving all entities in a table
```csharp
var products = db.Products.All().ToList();
```

#### Selecting some entities
```csharp
var products = db.Products.WhereIn("id", new int[]{3,4,5}).All();
// 和下面的查询等价：
var same_products = db.Products.WhereRaw("id IN (?,?,?)",3,4,5).All();
```

#### Inserting entities
```csharp
var product = new Product { Name = "Awesome bike", InStock = 4 };
int id = db.Products.Insert(product);
```
```csharp
var products = new List 
{
    new Product { Name = "Awesome bike", InStock = 4 },
    new Product { Name = "Awesome bike 2", InStock = 5 }
};

int count = db.Products.Insert(products);
```
#### Updating entities
```csharp
var product = db.Products.Get(1);
product.LastUpdate = DateTime.Now;
db.Products.Update(product);
```
```csharp
var products = db.Products.WhereIn("id", new int[]{1,2}).All().ToList();
products[0].LastUpdate = DateTime.Now;
products[1].LastUpdate = DateTime.Now;
db.Products.Update(products);
```
#### Removing entities
```csharp
var product = db.Products.Get(1);
db.Products.Delete(product);
```
```csharp
var products = db.Products.WhereIn("id", new int[]{1,2}).All();
db.Products.Delete(products);
```

#### Sharding
```csharp
using System;

// 分库分表，假设产品按年分库，按月分表
// 当前2019年6月表名为`db_product_y2019`.`t_product_m201906`

int pageNo = 1, pageSize = 10;
DateTime someDay = DateTime.Now.AddMonths(-3);
var referName = products.CurrentName + someDay.ToString("yyyyMM");
var products = db.Products.Where("created_at", ">=", someDay.ToString("yyyy-MM-dd"));
// 找出类似db_product_y2019等数据库，并倒序排列数据库和表名
products.DbNameMatch = "db_product_y%";
products.IsTableNameDesc = true;
// 数据表名称限制为 t_products_m201906
products.tableFilter = (table, db) => table.CompareTo(referName) >= 0;
var count = unchecked((int)products.CountSharding());
// Console.WriteLine("Count={0} PageNo={1}", count, pageNo);
var rows = products.PaginateSharding(pageNo, pageSize);
```

 

## Extensibility

#### `ITableNameResolver`
```csharp
// 根据 Model 类名对应表名，比如 Area 的表名为 t_areas
public class CustomTableNameResolver : ITableNameResolver
{
    public string Resolve(Type type)
    {
        var lower = type.Name.ToLower();
        return $"t_{lower}s";
    }
}
```

Register the custom implementation:
```csharp
db.NameResolver = new CustomTableNameResolver();
```

#### `IColumnNameResolver`
```csharp
// 根据 Model 成员名找出表中字段名称，比如 AreaCode 的段名为 area_code
public class CustomColumnNameResolver : IColumnNameResolver
{
    public string Resolve(DubonProperty info)
    {
        var re = new Regex(@"([A-Z])([A-Z][a-z])|([a-z0-9])([A-Z])");
        return re.Replace(info.Name, @"$1$3_$2$4").ToLower();
    }
}
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)