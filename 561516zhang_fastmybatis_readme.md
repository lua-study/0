# fastmybatis

fastmybatis是一个mybatis开发框架，目的为简化mybatis的开发，让开发更高效。

- 零配置快速上手
- 无需编写xml文件即可完成CRUD操作
- 支持mysql，sqlserver，oracle，postgresql,sqlite
- 支持自定义sql，sql语句可以写在配置文件中，同样支持mybatis标签
- 支持与spring-boot集成
- 轻量级，无侵入性，可与传统mybatis用法共存

[fastmybatis与MyBatis generator对比](https://gitee.com/durcframework/fastmybatis/wikis/pages?title=fastmybatis%E4%B8%8EMyBatis%20generator%E5%AF%B9%E6%AF%94&parent=)

# 快速开始（springboot）

- 新建一个springboot项目
- pom.xml添加fastmybatis-spring-boot-starter

```
 
     net.oschina.durcframework 
     fastmybatis-spring-boot-starter 
     1.0.2 
 
```
- 假设数据库有张`t_user`表，添加对应的实体类`TUser.java`和Mapper`TUserMapper.java`
- 在`application.propertis`中配置数据库连接
- 编写测试用例

```
@Autowired
TUserMapper mapper;
    
// 根据主键查询
@Test
public void testGetById() {
    TUser user = mapper.getById(3);
    System.out.println(user);
}
```

# Mapper方法列表

```
/**
 * 根据对象查询,可以传主键值,也可以传整个对象
 * 
 * @param id
 * @return 返回实体对象，没有返回null
 */
Entity getById(ID id);

/**
 * 根据条件查找单条记录
 * @param query 查询条件
 * @return 返回实体对象，没有返回null
 */
Entity getByQuery(@Param("query")Query query);

/**
 * 根据字段查询一条记录
 * @param column 数据库字段名
 * @param value 字段值
 * @return 返回实体对象，没有返回null
 */
Entity getByColumn(@Param("column")String column,@Param("value")Object value);

/**
 * 查询总记录数
 * 
 * @param query 查询条件
 * @return 返回总记录数
 */
long getCount(@Param("query")Query query);  

/**
 * 根据字段查询集合
 * @param column 数据库字段名
 * @param value 字段值
 * @return 返回实体对象集合，没有返回空集合
 */
List  listByColumn(@Param("column")String column,@Param("value")Object value);

/**
 * 条件查询
 * 
 * @param query 查询条件
 * @return 返回实体对象集合，没有返回空集合
 */
List  list(@Param("query")Query query);

/**
 * 查询指定字段结果
 * @param columns 返回的字段
 * @param query 查询条件
 * @return 返回结果集
 */
List > listMap(@Param("columns")List  columns, @Param("query")Query query);

/**
 * 新增,新增所有字段
 * 
 * @param entity
 * @return 受影响行数
 */
int save(Entity entity);

/**
 * 新增（忽略null数据）
 * @param entity
 * @return 受影响行数
 */
int saveIgnoreNull(Entity entity);

/**
 * 批量添加,只支持mysql,sqlserver2008及以上数据库. 
 *  若要兼容其它版本数据库,请使用saveMulti()方法 
 * @param entitys
 * @return
 */
int saveBatch(@Param("entitys")List  entitys);

/**
 * 批量添加,兼容更多的数据库版本. 
 * 此方式采用union all的方式批量insert,如果是mysql或sqlserver2008及以上推荐saveBatch()方法.
 * @param entitys
 * @return
 */
int saveMulti(@Param("entitys")List  entitys);

/**
 * 修改,修改所有字段
 * 
 * @param entity
 * @return 受影响行数
 */
int update(Entity entity);

/**
 * 根据主键更新不为null的字段
 * 
 * @param entity
 * @return 受影响行数
 */
int updateIgnoreNull(Entity entity);

/**
 * 根据条件批量更新
 * 
 * @param entity 待更新的数据，可以是实体类，也可以是Map{@literal }
 * @param query 更新条件
 * @return 受影响行数
 */
int updateByQuery(@Param("entity") Object entity, @Param("query") Query query);

/**
 * 删除
 * 
 * @param entity
 * @return 受影响行数
 */
int delete(Entity entity);

/**
 * 根据id删除
 * 
 * @param id 主键id
 * @return 受影响行数
 */
int deleteById(ID id);

/**
 * 根据条件删除
 * 
 * @param query
 * @return 受影响行数
 */
int deleteByQuery(@Param("query")Query query);
```

# Query查询对象

```
查询姓名为张三，并且年龄为22岁的用户：
Query query = new Query().eq("username","张三").eq("age",22);
List  users = mapper.list(query);

查询年龄为10,20,30的用户：
Query query = new Query().in("age",Arrays.asList(10,20,30));
List  users = mapper.list(query);

查询注册日期大于2017-11-11的用户：
Date regDate = ...
Query query = new Query().gt("reg_date",regDate);
List  users = mapper.list(query);

查询性别为男的，年龄大于等于20岁的用户，按年龄降序：
Query query = new Query().eq("gender",1).ge("age",20).orderby("age",Sort.DESC);
List  users = mapper.list(query);

分页查询：
Query query = new Query().eq("age",10).page(1,10); // 第一页，每页10条数据
List  users = mapper.list(query);

查询总记录数：
Query query = new Query().eq("age",10).page(1,10); // 第一页，每页10条数据
long total = mapper.getCount(query); // 该条件下总记录数
```

- 完整的测试用例，[点击前往](https://gitee.com/durcframework/fastmybatis/wikis/pages?title=%E5%AE%8C%E6%95%B4%E6%B5%8B%E8%AF%95%E7%94%A8%E4%BE%8B&parent=)

# 工程介绍

- [fastmybatis-core](https://gitee.com/durcframework/fastmybatis/tree/master/fastmybatis-core)：框架源代码
- [fastmybatis-demo](https://gitee.com/durcframework/fastmybatis/tree/master/fastmybatis-demo)：对应demo
- [fastmybatis-generator](https://gitee.com/durcframework/fastmybatis/tree/master/fastmybatis-generator)：代码生成工具，方便生成实体类和Mapper（可生成lombok风格实体类）
- [fastmybatis-spring-boot-autoconfigure](https://gitee.com/durcframework/fastmybatis/tree/master/fastmybatis-spring-boot-autoconfigure)和[fastmybatis-spring-boot-starter](https://gitee.com/durcframework/fastmybatis/tree/master/fastmybatis-spring-boot-starter)：springboot对应的的starter

# 实战项目

[easydoc](https://gitee.com/durcframework/easydoc) : 一个文档管理项目，采用markdown方式写作。

# 意见交流

Q群328419269

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)