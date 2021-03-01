# mybatis_jpa_jack

#### 项目介绍
Mybatis JPA 是mybatis的jpa插件，实现了JPA标准协议的CURD 包含一对一以及一对多的查询功能，不需要写一行sql，

本项目已经在自己公司实践过，不敢说没有bug，还是比较稳定的。本项目只适用于Mysql。

2019-02-22 更新 Mybatis JPA 现在支持了Mybatis plus的注解，可以支持和mybatis plus一起使用。


#### 软件架构
软件架构说明


本项目基于https://github.com/svili365/mybatis-jpa  开发  感谢 svili，此项目是svili项目的一个分支，和svili的jpa项目在同一个qq群提供支持 。


#### SpringBoot 集成

```
@Configuration
public class MybatisConfig {

    @Autowired
    private SqlSessionFactory sqlSessionFactory;

    @Bean
    public PersistentEnhancerScaner getPersistentEnhancerScaner(){
        PersistentEnhancerScaner scanner = new PersistentEnhancerScaner();
        scanner.setEntityPackage("com.ylm.**.bean");
        scanner.setMapperPackage("com.ylm.**.dao");
        scanner.setSqlSessionFactory(sqlSessionFactory);
        return scanner;
    }

}



```
#### SpringMVC 集成

```

	 
	 
		 
		 
		 
	 
```
#### 注解说明
 1  实体类注解
    注意：插件会默认使用驼峰来找java 属性对应DB表的字段，比如你java字段名是 userName db是user_name 不配置Column 注解也是可以的。
```     
//声明我是一个DO
@Entity
// 声明我的表是哪个
@Table(name="t_ucenter_front_user")
public class FrontUser extends SuperBean 
{
	private static final long serialVersionUID = 1L;
	/**
	 * 用户Id
	 */
	//声明我是主键
	@Id 
        //声明我的列是什么
	@Column(name = "user_id", nullable = false, length = 32)
	private String userId;

	/**
	 * 昵称
	 */
        
	@Column(name = "nick_name", nullable = true, length = 32)
        //声明我查询的时候传入此字 当做过滤条件的时候  段默认用like 来查询而不是 == 
	@Like
	private String nickName;

        //一对多注解
        @OneToMany(mappedBy="user_id")
	private List  roles;
}
 ```     
2  DAO/Mapper注解
   以下是一个demo，也是项目中默认提供的test包中的示例
   
```
 @Repository
//配置对应的实体类是哪个 默认的排序规则是什么 
@MapperDefinition(domainClass = User.class,orderBy=" user_id desc")
public interface UserMapper extends MybatisBaseMapper  {
	String resultMap = ResultMapConstants.DEFAULT_NAMESPACE + ".User";

        //根据用户名删除 这个是=的哦
	@StatementDefinition
	int deleteByUserName(String userName);

        //根据用户名更新
	@StatementDefinition
	int updateByUserName(User user);

        //根据用户名去更新，如果你某些字段传了null将不会更新这些字段
	@StatementDefinition
	int updateSelectiveByUserName(User user);

	@StatementDefinition
	List  selectByUserName(String userName);

	/* Like 的通配符需要自行添加 */
	@StatementDefinition
	List  selectByUserNameLike(String userName);

	@StatementDefinition
	List  selectByUserIdLessThan(Integer userId);

	@StatementDefinition
	List  selectByUserIdIsNull();

	/*more condition or complex SQL,need yourself build*/

	/**注意,此方法的resultMap是jpa自动生成的UserResultMap*/
	@Select("select * from ybg_test_user where user_name = #{userName} and dept_id = #{deptId}")
	@ResultMap(resultMap)
	List  selectComplex(Map  args);

	List  selectComplex2(Map  args);

}
```    
#### 如何和自己的Mapper/dao 结合起来使用呢？又提供了哪些默认的方法呢？
写一个Mapper 接口继承下面这个接口即可(就和上面提供的demo一样)
注意：批量删除功能并未提供，这些包含不到的您依然可以通过 mapper.xml 去扩展你的mapper/dao中的方法(sql)

```
	/**
	 * 做判空处理的insert
	 * @param entity do
	 * @return 受影响的行数
	 */
	@StatementDefinition
	int insertSelective(T entity);

	/**
	 * 插入
	 * @param entity
	 * @return int 受影响的行数
	 * @since  1.0.0
	*/
	@StatementDefinition
	int insertJap(T entity);

	/**
	 * 批量插入
	 * @param list 需要插入的集合
	 * @return 受影响的行数
	 * @since  1.0.0
	*/
	@StatementDefinition
	int batchInsert(@Param("list")List  list);

	/**
     * 批量插入.
     *
     * @param list 需要插入的集合
     * @param flag 分表标志
     * @return 受影响的行数
     * @since 1.0.0
     */
    @StatementDefinition
    int batchInsertCatTable(@Param("list")List  list,@Param("flag")String flag);

	/**
	 * 根据id删除数据
	 * @param primaryValue id
	 * @return 受影响行数
	 * @since  1.0.0
	*/
	@StatementDefinition
	int deleteByIdJpa(Object primaryValue);

	/**
     * 根据id删除数据
     * @param primaryValue id
     * @param flag 分表标志
     * @return 受影响行数
     * @since  1.0.0
    */
    @StatementDefinition
    int deleteByIdCatTable(@Param("param")Object primaryValue,@Param("flag")String flag);

	/**
	 * 根据id更新
	 * @param entity 待更新数据
	 * @return   受影响行数
	 * @since  1.0.0
	*/
	@StatementDefinition
	int updateByIdJpa(T entity);

	/**
	 * 根据id跟新 -- 判空
	 * @param 待更新数据
     * @return   受影响行数
	 * @since  1.0.0
	*/
	@StatementDefinition
	int updateSelectiveById(T entity);

	

	/**
	 * 根据id、查询
	 * @param primaryValue id
	 * @return   model
	 * @since  1.0.0
	*/
	@StatementDefinition
	T selectByIdJpa(Object primaryValue);


	/**
	 *  级联查询 支持one2one one2x
	 * @param entity  过滤条件
	 * @param pageStart 分页开始
	 * @param pageSize 分页行数
	 * @return 级联查询结果
	 */
	@NestedSelect
	@StatementDefinition
	List  selectNested(@Param("entity")T entity,@Param("pageStart")long pageStart,@Param("pageSize")long pageSize);

	/**
	 *  级联查询 支持one2one one2x
	 * @param entity  过滤条件
	 * @param pageStart 分页开始
	 * @param pageSize 分页行数
	 * @param orderBy 排序参数
	 * @return 级联查询结果
	 */
	@NestedSelect
	@StatementDefinition
	List  selectNestedForOrder(@Param("entity")T entity,@Param("pageStart")long pageStart,@Param("pageSize")long pageSize,@Param("orderBy")String orderBy);

	/**
     * 根据id、查询
     * @param primaryValue id
     * @return   model
     * @since  1.0.0
    */
    @StatementDefinition
    T selectByIdCatTable(@Param("param")Object primaryValue,@Param("flag")String flag);


	/**
	 * 根据分页参数返回结果
	 * 如果不需要分页 pageStart或者pageSize传-1即可
	 * @param entity 用来做过滤的参数
	 * @param pageStart 开始number
	 * @param pageSize 一页多少行数据
	 * @return 符合条件的数据
	 */
	@StatementDefinition
	List  selectPageJpa(@Param("entity")T entity,@Param("pageStart")long pageStart,@Param("pageSize")long pageSize);

	/**
	 * 根据分页参数返回结果
	 * 如果不需要分页 pageStart或者pageSize传-1即可
	 * @param entity 用来做过滤的参数
	 * @param pageStart 开始number
	 * @param pageSize 一页多少行数据
	 * @param orderBy  排序字段
	 * @return 符合条件的数据
	 */
	@StatementDefinition
	List  selectPageForOrder(@Param("entity")T entity,@Param("pageStart")long pageStart,@Param("pageSize")long pageSize,@Param("orderBy")String orderBy);


	/**
	 * 根据参数查询总数
	 * 如果不需要分页 pageStart或者pageSize传0即可
	 * @param entity 用来做过滤的参数
	 * @return 符合条件的数据条数
	 */
	@StatementDefinition
	long selectCountJpa(T entity);

	/**
     * 根据条件查询bean对象
     * @param entity 用来做过滤的参数
     * @return 符合条件的数据
     */
    @StatementDefinition
    T selectBean(T entity);

	/**
	 * select(这里用一句话描述这个方法的作用)
	 * (这里描述这个方法适用条件 – 可选)
	 * @return 查询所有
	 * @since  1.0.0
	*/
	@StatementDefinition
	List  select();

	/**
	 * 给定参数进行删除 操作
	 * @param entity 参数
	 * @return 影响行数
	 */
	@StatementDefinition
	int deleteBean(T entity);

```
#### maven dependency 怎么写？
本项目没有上传jar包到中央仓库，需要把代码down 下来，自己编译。
     




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)