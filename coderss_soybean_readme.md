#soybean是一个非常简单易用的orm库
##1、初步使用
  ```java
    Connection conn = ....;//获取Connection对象
    QueryEngine engine = new QueryEngine();
    String sql = "select * from xxx where id = ?";
    Map map = engine.toMap(conn, sql, 1);
  ```
  把结果集转换成Map对象
##2、详细介绍
  
  ```java
    /*基于java bean 映射配置*/
    @Table("user")//配置映射表，如果表名与 类名(转小写)相同，可以省略
    public class User{
        @Id//指定主键
        @Column("user_id")//指定列名，如果列名与属性名相同可以省略
        private int id;
        private String username;
      }
  ```
  ```java
    /*普通用法*/
    
    Connection conn = ....;//获取Connection对象
    QueryEngine engine = new QueryEngine();
    String sql1 = "select * from user where user_id = ?";
    Map map = engine.toMap(conn, sql1, 1);//把结果集转换成Map
    User user = engine.toBean(conn,sql,User.class, 1);//把结果集转化成java bean
    
    String sql2 = "select * from user";
    engine.toMapList(conn, sql2);//把多行结果转换成List 格式
    engine.toBeanList(conn, sql, User.class);//把多行结果转化成List 格式
    
    String sql3 = "update user set username = ? where user_id = ?";
    engine.update(conn, sql3, "codelee", 1);//更新数据（删除数据，插入数据也使用这个方法）
    
    String sql4 = "select count(*) from user";
    long count = engine.count(conn, sql4);//统计
  ```
  ```java
    /* orm用法 */
    Connection conn = ....;//获取Connection对象
    OOQueryEngine engine = new OOQueryEngine();//基于ORM的处理对象
    
    List  user = engine.listAll(conn, User.class);//查找所有
    
    User user = engine.get(conn, User.class, 1);//根据主键查询
    
    engine.save(conn , user);//插入数据
    
    engine.update(conn, user);//更新数据
    
    engine.saveOrUpdate(conn, user);//根据主键的值判断插入或者跟新数据
    
    engine.remove(conn, user);//删除对象
    
    
  ```
  ```java
    /*事物处理*/
    Connection conn = ...;//获取Connection对象
    QueryEngine engine = new QueryEngine();
    OOQueryEngine ooEngine = new OOQueryEngine();
    Trans.execute(conn, new TransProccessor() {
        @Override
        public void execute(Connection conn, AbstractEngine... engines) throws Throwable {
          QueryEngine engine = (QueryEngine)engines[0];
          OOQueryEngine ooEngine = (OOQueryEngine)engines[1];
          engine.update(...);
          ooEngine.save(conn,user);
          .....
        }
    },engine,ooEngine);
  ```
  
  


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)