#1、Ado使用例子
 
	string connectionString = "Data Source=.;Initial Catalog=testdb;User ID=sa;Password=bouyei;";

	IAdoProvider adoProvider = AdoProvider.CreateProvider(connectionString);

	var rt = adoProvider.Query(new Parameter()
	{
		CommandText = "select * from MemUser"
	});

	//删除
	var del= adoProvider.Delete (x => x.name == "hello");

	//插入
	  var insert = adoProvider.Insert (new user() {
                 name="bouyei",
                 age=30
            });

	//查询
	var users = adoProvider.Query (x => 1 == 1);

	foreach (DataRow dr in rt.Result.Rows)
	{
		Console.WriteLine(string.Join(",", dr.ItemArray));
	}

#基于EF的ORM需要再配置文件加相应实体映射dll路径，详细看demo代码例子

	IOrmProvider ormProvider = OrmProvider.CreateProvider(ProviderType.SqlServer, connectionString);

	var items= ormProvider.Query ("select * from MemUser").ToList();

	foreach(var item in items)
	{
		Console.WriteLine(item.uName);
	}
	Console.ReadKey();

#sql表达式生成例子
			//生成简单查询脚本
            ISqlProvider sqlProvider = SqlProvider.CreateProvider();

            //查询
           var sql= sqlProvider.Select ()
                .From ().Where (x => x.Id == 1).SqlString;

            //修改
            sql = sqlProvider.Update ()
                .Set (new User() { Name = "bouyei", UserName = "hkj" })
                .Where (x => x.Id == 1).SqlString;

            //删除
            sql = sqlProvider.Delete()
                .From ().Where (x => x.Name == "bouyei").SqlString;

            //插入
            sql = sqlProvider.Insert ()
                .Values (new User[] {
                new User() { Name ="hello", UserName="aileenyin.com" }
                ,new User() { Name="bouyei",UserName="jiang"} }).SqlString;

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)