# 公告：easymybatis后期不再开发新功能，只做BUG修复。强烈推荐easymybatis的增强版本:[fastmybatis](https://gitee.com/durcframework/fastmybatis)，API更清晰，功能更丰富，代码更稳定。


## 简单介绍
easymybatis是一个mybatis增强类库，目的为简化mybatis的开发，让开发更高效。


easymybatis的特性如下：

- 无需编写xml文件即可完成CRUD操作。
- 支持多表查询、聚合查询、分页查询（支持多种数据库）。
- 支持批量添加，指定字段批量添加。
- 支持Dao层访问控制，如某个dao只有查询功能，某个dao有crud功能等。
- 支持自定义sql，sql语句可以写在配置文件中，同样支持mybatis标签。
- 支持mysql，sqlserver，oracle，postgresql,sqlite.其它数据库扩展方便（增加一个模板文件即可）。
- 使用方式不变，与Spring集成只改了一处配置。
- 支持与spring-boot集成。
- 轻量级，无侵入性，可与传统mybatis用法共存。
- 没有修改框架源码(无插件)，可同时使用官方提供的功能。

## 架构组成
easymybatis的架构如下：

![架构](https://git.oschina.net/uploads/images/2017/0905/135741_c7821a5b_332975.png "em_arc.png")

## 运行流程
easymybatis的运行流程图：

![运行流程](https://git.oschina.net/uploads/images/2017/0905/135821_508ba7cc_332975.png "em_flow.png")


1. 服务器启动的时候easymybatis负责扫描Dao.java。
2. 扫描完成后解析出Dao.class以及实体类Entity.class。
3. 代码生成组件根据Dao.class和Entity.class生成mapper文件内容，生成方式由velocity模板指定。
4. 把mapper文件内容转化成Resource对象设置到SqlSessionFactory中。

## 工程介绍

- easymybatis：框架代码
- easymybatis-demo：对应demo
- easymybatis-doc：开发文档离线版
- easymybatis-generator：代码生成工具
- easymybatis-starter：对应springboot-starter


## 意见交流
如果您在使用的过程中遇到问题的话可以加入** QQ群328419269 **进行提问。

## 完整测试用例

```

public class TUserDaoTest extends EasymybatisSpringbootApplicationTests {

	@Resource
	TUserDao dao;
	@Resource
	TransactionTemplate transactionTemplate;
	
	// 根据主键查询
	@Test
	public void testGet() {
		TUser user = dao.get(3);
		print(user);
	}
	
	// 根据字段查询一条记录
	@Test
	public void testGetByProperty() {
		TUser user = dao.getByProperty("username", "王五");
		print(user);
	}
	
	// 根据条件查询一条记录
	@Test
	public void testGetByExpression() {
		// 查询ID=3的用户
		Query query = Query.build().eq("id", 3);
		
		TUser user = dao.getByExpression(query);
		
		print(user);
	}
	
	// 条件查询
	// 查询username='张三'的用户
	@Test
	public void testFind() {
		Query query = new Query();
		// 添加查询条件
		query.eq("username", "张三");
		
		List  list = dao.find(query); // 获取结果集
		long count = dao.countTotal(query); // 获取总数
		print("count:" + count);
		for (TUser user : list) {
			System.out.println(user);
		}
	}
	
	// 分页查询
	/*MYSQL语句:
	 * 
	 * SELECT t.`id` , t.`username` , t.`state` , t.`isdel` , t.`remark` , t.`add_time` , t.`money` , t.`left_money` 
	 * FROM `t_user` t 
	 * ORDER BY id DESC 
	 * LIMIT ?,? 
	 * 
	 * Parameters: 2(Integer), 2(Integer)
	 */
	@Test
	public void testPage() {
		Query query = new Query();
		
		query.setPage(2, 2) // 设置pageIndex，pageSize
			.addSort("id", Sort.DESC); // 添加排序
		
		// 查询后的结果，包含总记录数，结果集，总页数等信息
		PageInfo  pageInfo = QueryUtils.query(dao, query);
		
		List  rows = pageInfo.getList();
		for (TUser user : rows) {
			System.out.println(user);
		}
	}
	
	// 自定义返回字段查询，只返回两个字段
	// SELECT t.id,t.username FROM `t_user` t LIMIT 0,10
	@Test
	public void testSelfColumns() {
		Query query = new Query();
		// 只返回id,username
		query.setColumns(Arrays.asList("t.id","t.username"));
		
		List  list = dao.find(query);
		
		for (TUser user : list) {
			System.out.println(user);
		}
	}
	
	// 多表查询,left join
	// 适用场景：获取两张表里面的字段信息返回给前端
	/* 
	 *  MYSQL生成如下sql:
		SELECT 
			t.`id` , t.`username` , t.`state` , t.`isdel` , t.`remark` , t.`add_time` , t.`money` , t.`left_money` 
			, t2.city , t2.address 
		FROM `t_user` t left join user_info t2 on t.id = t2.user_id 
		WHERE t2.id = ?
		ORDER BY id ASC 
		LIMIT ?,?
	 */
	@Test
	public void testJoin() {
		Query query = new Query();
		// 添加第二张表的字段,跟主表字段一起返回
		query.addOtherColumns(
					"t2.city"
					,"t2.address"
		);
		// 左连接查询,主表的alias默认为t
		query.join("left join user_info t2 on t.id = t2.user_id"); 
		//添加条件
		query.eq("t2.id", 2);
		
		query.addSort("t.id");
		
		List  list = dao.find(query);
		
		System.out.println("==============");
		for (TUser user : list) {
			System.out.println(
				user.getId() 
				+ " " + user.getUsername() 
				// 下面两个字段是第二张表里面的
				+ " " + user.getCity() 
				+ " " + user.getAddress()
			);
		}
		System.out.println("==============");
	}
	
	// 添加-保存所有字段
	@Test
	public void testInsert() {
		TUser user = new TUser();
		user.setAddTime(new Date());
		user.setIsdel(false);
		user.setLeftMoney(22.1F);
		user.setMoney(new BigDecimal(100.5));
		user.setRemark("备注");
		user.setState((byte)0);
		user.setUsername("张三");
		
		dao.save(user);
		
		print("添加后的主键:" + user.getId());
		print(user);
	}
	
	// 添加-保存非空字段
	@Test
	public void testInsertIgnoreNull() {
		TUser user = new TUser();
		user.setAddTime(new Date());
		user.setIsdel(true);
		user.setMoney(new BigDecimal(100.5));
		user.setState((byte)0);
		user.setUsername("张三notnull");
		user.setLeftMoney(null);
		user.setRemark(null);
		
		dao.saveIgnoreNull(user);
		
		print("添加后的主键:" + user.getId());
		print(user);
	}
	
	// 批量添加
	/*
	 * 支持mysql,sqlserver2008。如需支持其它数据库使用saveMulti方法
	 * INSERT INTO person (id, name, age)
		VALUES
    	(1, 'Kelvin', 22),
    	(2, 'ini_always', 23);
	 */
	@Test
	public void testInsertBatch() {
		List  users = new ArrayList<>();
		
		for (int i = 0; i   " + i);
	}
	
	// 更新所有字段
	@Test
	public void testUpdate() {
		TUser user = dao.get(3);
		user.setUsername("李四");
		user.setMoney(user.getMoney().add(new BigDecimal(0.1)));
		user.setIsdel(true);
		
		int i = dao.update(user);
		print("testUpdate --> " + i);
	}
	
	// 更新不为null的字段
	/*
	 *UPDATE [t_user] SET [username]=?, [isdel]=? WHERE [id] = ?  
	 */
	@Test
	public void updateIgnoreNull() {
		TUser user = new TUser();
		user.setId(3);
		user.setUsername("王五");
		user.setIsdel(false);
		int i = dao.updateIgnoreNull(user);
		print("updateNotNull --> " + i);
	}
	
	// 根据条件更新
	// UPDATE t_user SET remark = '批量修改备注' WHERE state = 0
	@Test
	public void testUpdateNotNullByExpression() {
		Query query = new Query();
		query.eq("state", 0);
		
		TUser user = new TUser();
		user.setRemark("批量修改备注");
		
		int i = dao.updateIgnoreNullByExpression(user, query);
		print("testUpdateNotNullByExpression --> " + i);
	}
	
	// 删除
	@Test
	public void testDel() {
		TUser user = new TUser();
		user.setId(14);
		int i = dao.del(user);
		print("del --> " + i);
	}
	
	// 根据条件删除
	// DELETE FROM `t_user` WHERE state = ? 
	@Test
	public void delByExpression() {
		Query query = new Query();
		query.eq("state", 3);
		int i = dao.delByExpression(query);
		print("delByExpression --> " + i);
	}
	
}
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)