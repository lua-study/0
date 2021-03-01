#mybatis-mapper
Mapper继承CrudMapper后，无需编写mapper.xml文件，即可获得CRUD功能

### MyBatis的sql默认加载规则
MyBatis通过xml、SqlProvider两种方式获取sql，xml的优先级高于SqlProvider，且xml、SqlProvider中的sql不允许出现同名

### mapper调整后的sql加载规则
1. sql的优先级：xml > SqlProvider > crudsql
2. xml、SqlProvider、crudsql允许出现同名的sql，优先级高的有效

### 约定规则
1. 实体类类名驼峰转下划线即为数据库表名，如类User、UserGroups对应的数据库表名为user、user_groups
2. 实体类属性名默认与数据库表字段名一一对应，忽略transient修饰的属性
3. 实体类属性id(Long、long、Integer、int类型)默认对应数据库表主键；如果使用了其他的属性名或主键策略，可以使用注解@PK进行标识
4. 既没采用默认id作为主键，也没使用@PK标识主键，则认为数据库表没有单一主键；根据主键操作的删除、修改、查找方法不会被注入

### 测试用例
	public class UserMapperTest {
		public static void main(String[] args) {
			String resource = "mybatis.xml";
			InputStream in = UserMapperTest.class.getClassLoader().getResourceAsStream(resource);
	
			// 此处采用MybatisSessionFactoryBuilder构建SqlSessionFactory，目的是引入CrudMapper功能
			SqlSessionFactory sessionFactory = new MybatisSessionFactoryBuilder().build(in);
			SqlSession session = sessionFactory.openSession();
			UserMapper userMapper = session.getMapper(UserMapper.class);
	
			// 此处的selectByPK被UserMapper.xml中的selectByPK覆盖了
			User user = userMapper.selectByPK(2);
			System.out.println(user);
	
			user.setName("update_" + user.getName());
			// updateByPK是从CrudMapper中继承而来的，UserMapper.xml中并没有申明该sql
			userMapper.updateByPK(user);
	
			// 此处的selectByPK被UserMapper.xml中的selectByPK覆盖了
			user = userMapper.selectByPK(user.getPk());
			System.out.println(user);
	
			session.commit();
		}
	}

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)