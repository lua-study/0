 >>>>>> 初始化

1. Fork 本仓库
2. 新建 Feat_xxx 分支
3. 提交代码
 
       com.h2database 
       h2 
       1.4.199 
     
```

引用H2依赖包后，使用默认的配置，即可使用H2数据库。

注意：如果数据库不存在的话，会新创建一个。

```java
    private static final String URL = "jdbc:h2:~/test1;MODE=MYSQL;DB_CLOSE_DELAY=-1";
    private static final String NAME = "sa";
    private static final String PASSWORD = "";
    
        try (Connection conn = DriverManager.getConnection(URL, NAME, PASSWORD)) {

            //3.通过数据库的连接操作数据库，实现增删改查
            Statement stmt = conn.createStatement();

            ResultSet rs = stmt.executeQuery("select * from user");//选择import java.sql.ResultSet;

            // 遍历每行记录
            while (rs.next()) {
                //如果结果集中有数据，就会循环打印出来
                System.out.println(rs.getString("name") + "," + rs.getInt("age"));
            }

        } catch (SQLException e) {
            e.printStackTrace();
        }
```

但这种试有个缺点，不方便维护，因为数据库只能本地连接，不能使用管理界面。

所以官方推荐另外两种方式连接数据库。

一种是使用外围的H2数据库。
```bash
java -jar h2*.jar
```

或使用服务器的命令行工具启动数据库：
```bash
java -cp h2*.jar org.h2.tools.Server
```

数据库连接字符串改为下面的：
```java
private static final String URL_TCP = "jdbc:h2:tcp://localhost/~/test1;MODE=MYSQL;DB_CLOSE_DELAY=-1";
```

另外一种是在Java EE Web应用程序里，使用监听器启动数据库，并设置允许TCP连接。

详细查看web.xml的源码。

获取连接时，改用下面的代码：
```java
Connection conn = (Connection) getServletContext().getAttribute("connection");
```

### 进阶
1、H2数据库也支持数据库连接池的，请自行查阅H2官方教程。
2、有关使用Jetty JNDI调用数据源，以及在Jetty中配置H2数据源的方法，请参考 开发环境文档。（重要）

### 作业
写一个servlet，当接受到请求时，创建一个学生成绩表，字段包括：学号，课程名，成绩。构造、插入三条记录，成功后，查询数据库，
把刚才插入的数据库记录返回给前端。要求利用数据源访问H2数据库。
>>>>>>> 初始化
=======
4. 新建 Pull Request
>>>>>>> 初始化


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)