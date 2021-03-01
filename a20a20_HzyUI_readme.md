

开发环境：vs2013、asp.net mvc 4

交流群: _**534584927**_ 

前端：
BootStrap 3
Layer
Jquery 
后端：
三层+MVC4

传送门：
.Net Core 2.0 :https://gitee.com/hao-zhi-ying/HzyAdmin

H+:https://github.com/HaoZhiYing/HPlus


--集成通配权限管理

--ORM 大部分使用 拉姆达 表达式 操作

--ORM 举例：

            DBContext db=new DBContext();//默认sqlserver 数据库 链接字符串 需要 在 程序 启动 注入 到 DbFrameConfig 类中 ConnectionString 字段

            DBContext db=new DBContext(DataBaseType.MySql);///Mysql 数据库 默认链接字符串  ConnectionString 自动会去 app.config 查找
            DBContext db=new DBContext(DataBaseType.MySql,"链接字符串");
            
            //新增
            //新增
            var user = new TestT_Users();
            user.cUsers_Name = "123";
            user.cUsers_LoginPwd = "123";
            user.cUsers_LoginName = "123";
            user.cUsers_Email = "123";
            db.Add(user);
            user.uUsers_ID = db.Add(user, true).To_Guid();//第二个参数表示验证字段信息
            if (user.uUsers_ID == Guid.Empty) throw new Exception(db.ErrorMessge);

            db.Add(user, li);//获取 sql  默认存入 li 中
            db.Commit(li);//提交事务
            //插入单个字段
            db.Add(() => new TestT_Users()
            {
                cUsers_Name = "haha"
            });

            //修改
            user = new TestT_Users();
            user.cUsers_Name = "123";
            user.cUsers_LoginPwd = "123";
            user.cUsers_LoginName = "123";
            user.cUsers_Email = "123";
            db.Edit(user, w => w.uUsers_ID == Guid.Empty);//修改所有的字段
            db.Edit(() => new TestT_Users()
            {
                cUsers_Name = "哈哈"
            }, w => w.uUsers_ID == Guid.Empty);

            //删除
            db.Delete (w => w.uUsers_ID == Guid.Empty && w.cUsers_Name == null);

            db.Delete (w => w.uUsers_ID == Guid.Empty, li);
            db.Commit(li);

            //查询
            var dt = db.Find("select * from " + user.GetTabelName() + " where 1=1");//原始 sql 得到 DataTable

            var model = db.Find (w => w.uUsers_ID == Guid.Empty);//单表

            var name = "admin";
            var list = db.FindList (w => w.cUsers_LoginName.Like("%" + name + "%"), " dUsers_CreateTime desc ");//单表集合
            //多表查询
            var iquery =db.Find ()
                            .Query((a, b) => new { a.uUsers_ID, a.cUsers_Email, a.cUsers_LoginName, a.cUsers_Name, b.Member_Name, b.Member_Sex, b.Member_CreateTime, _ukid = a.uUsers_ID })
                            .LeftJoin((a, b) => a.uUsers_ID == b.Member_ID && a.cUsers_Email == "1231231", "b")
                            .Where((a, b) => a.uUsers_ID == Guid.Empty);

            var sql = iquery.ToSQL();//获取sql
            var list_db = iquery.ToList();//获取 字典集合 List >
            var dt1 = iquery.ToDataTable();//获取 DataTable

            //其他
            db.FindObject("select count(1) from " + user.GetTabelName() + " where 1=1 and a=b").To_Int();
            DataRow dr = null;//这里只是举例
            db.DataRowToModel (dr);//将 DataRow 转换为 实体 TestT_Users
            List > newLi = db.FindList("这里 是 sql");

            bool isok = db.CheckModel (user);//验证实体 的字段 是否 为空 等等。。。。
            if (!isok) throw new Exception(db.ErrorMessge);//db.ErrorMessge 可能存放 用户名不能为空.....

            var json = db.jss.Serialize(user);//序列化 为 json 串

            //db.dbhelper 原始 数据库访问

            ///  
            /// 查询
            ///  
            ///   
            ///   
            ///   
            ///   
            public PagingEntity GetDataSource(Hashtable query, int pageindex, int pagesize)
            {
                string where = "";
                where += string.IsNullOrEmpty(query["cUsers_Name"].To_String()) ? "" : " and cUsers_Name like '%" + query["cUsers_Name"].To_String() + "%' ";
                where += string.IsNullOrEmpty(query["cUsers_LoginName"].To_String()) ? "" : " and cUsers_LoginName like '%" + query["cUsers_LoginName"].To_String() + "%' ";

                var sql = db.Find ()
                            .Query((a, b) => new { a.uUsers_ID, a.cUsers_Email, a.cUsers_LoginName, a.cUsers_Name, b.Member_Name, b.Member_Sex, b.Member_CreateTime, _ukid = a.uUsers_ID })
                            .LeftJoin((a, b) => a.uUsers_ID == b.Member_ID && a.cUsers_Email == "1231231", "b")
                            .Where((a, b) => a.uUsers_ID == Guid.Empty)
                            .ToSQL();
                var pe = db.Find(sql, " dUsers_CreateTime ", false, pageindex, pagesize);
                return new ToJson().GetPagingEntity(pe, new List ()
                {
                    new T_Users(),
                    new T_Roles()
                });
            }




UI：
![输入图片说明](https://gitee.com/uploads/images/2018/0422/163845_6c1ef648_1242080.png "屏幕截图.png")
![输入图片说明](https://gitee.com/uploads/images/2018/0422/163945_6b4e00e0_1242080.png "屏幕截图.png")
![输入图片说明](https://gitee.com/uploads/images/2018/0422/164102_d2c61076_1242080.png "屏幕截图.png")
![输入图片说明](https://gitee.com/uploads/images/2018/0422/164213_bb6042da_1242080.png "屏幕截图.png")
![输入图片说明](https://gitee.com/uploads/images/2018/0425/232638_ca197ce4_1242080.png "27)(8TN(Q`2Z6DE}Z(%MM(E.png")
![输入图片说明](https://gitee.com/uploads/images/2018/0422/164259_5271dab6_1242080.png "屏幕截图.png")
=============手机版本==============
列表：
![输入图片说明](https://git.oschina.net/uploads/images/2017/0905/164919_82beaa78_1242080.png "屏幕截图.png")
添加/修改:
![输入图片说明](https://git.oschina.net/uploads/images/2017/0905/164949_99895558_1242080.png "屏幕截图.png")

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)