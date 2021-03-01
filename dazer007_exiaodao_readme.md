#liuda-mgr

### 1. springMVC+Hibernate+JPA配置
> * [配置教程1](http://blog.csdn.net/h348592532/article/details/46698311)
> * [配置教程2](http://www.tuicool.com/articles/feqUJz)


### 2. 基础待学习知识 

- [x] spring
- [x] spring 注解
    >@Service用于标注业务层组件
    >@Controller用于标注控制层组件（如struts中的action）
    >@Repository用于标注数据访问组件，即DAO组件
    >@Component泛指组件，当组件不好归类的时候，我们可以使用这个注解进行标注。
- [x] spring 事物注解
    >1:Transactional:配置
     
    	 
    		
    >2:使用
    作用:类和方法
    使用类:当标于类前时, 标示类中所有方法都进行事物处理  http://www.cnblogs.com/caoyc/p/5632963.html
    都在service的实现类里面
    @Transactional(readOnly = false)
    @Transactional(readOnly = true, rollbackFor = Exception.class)
    @Transactional(rollbackFor = Exception.class)
    
- [x] springMVC
  >1:Transactional:配置
  [springmvc 实现http接口 接受json参数](http://blog.csdn.net/zhen340417593/article/details/51321710
  [11](http://blog.csdn.net/xingtianyiyun/article/details/8644265)
  >2:使用
  @ResponseBody:直接把返回的对象如(自定义实体,map等)自动转成json
  @RequestBody: 注解的含义就是读取请求body里面的值映射成参数(application/json;form表单都支持) http://www.jianshu.com/p/7e1432aad92f

- [ ] spring JPA
- [ ] hibernate
- [ ] [jackson](http://blog.csdn.net/mingyunduoshou/article/details/7550228)  java-json-xml-map 转换,**org.json.json**; **com.alibaba.fastjson**;


Emoji mysql乱码:字符编码改为utf8mb4

登录拦截器:j_spring_security_check  http://www.oschina.net/question/170070_43887

swagger 提交到后台的乱码解决:
1:彻底解决Spring MVC 中文乱码 问题(http://blog.csdn.net/kalision/article/details/46441081/)
【其实没用】
2:springMVC 配置CharacterEncodingFilter之后不起效果 
【正在解决办法]:
http://www.cnblogs.com/countguo/p/5303805.html
原因:tomcat配有配置编码格式--- 改成
 
    
    
    [Spring Data JPA 查询方法支持的关键字](http://www.cnblogs.com/BenWong/p/3890012.html)
    http://www.cnblogs.com/dreamroute/p/5173896.html
    
    https://www.ibm.com/developerworks/cn/opensource/os-cn-spring-jpa/ Spring Data JPA 让一切近乎完美
    http://blog.csdn.net/zsm653983/article/details/8114244  JPQL 查询
    
    jap命名:favoriteObjectID 在 jpa怎么写
    favoriteObjectID jpa里面怎么写  ????
    userId--->userId   createTime--->   favoriteObjectId---> findByUserIdAndFavoriteObjectIdAndTypeAndStatusNot 这是都可以的
    但是favorite_ObjectID ????,包含_
    public List  findByIdInAndStatusNot(Collection  id, Integer status);
    
    
    命名规范:entity类用大小写的驼峰,不要用_或-
    
    
    Map  filterParams =  WebUitl.getParametersStartingWith("{}", "search_");
    Map  filterParams =  WebUitl.getParametersStartingWith("{'search_EQ_clubId':'"+clubId+"'}", "search_");
    filterParams=WebUitl.getParametersStartingWith("{'search_EQ_clubId':'"+clubId+"','search_EQ_userId':'"+userId+"'}", "search_");
    
    filterParams.get("EQ_userId")
    Operator.IN 
    
    JPA:Java Persistence API 规范
    Hiberant JPA,Open JPA 都是jpa提供者
    JPQL:Java Persistence Query Language:面向对象,跨语言
    SQL:
    HQL:
    ???????????批量执行sql
    ???????????jdbcTemplate可以批量处理
    ?????自己写的sql怎么防止注入??? tb_xa_order_detail 插入订单明细; 用??就可以;?? 自己拼接不行?? 比如color:orange;size:100;  ('导致的注入,解决:1:禁止+,append拼接sql;2:拼接,每个字符串类型进行处理;3:使用?占位符,或者"name占位符)
      
    
    http://www.objectdb.com/java/jpa/query/jpql/order
    JPQL:
    	@Query("select ro.roleName from XaCmsUserRole ur,XaCmsRole ro where ur.userId = ?1 and ur.roleId=ro.roleId")
    	public List  findRoleNameByUserId(Long userId);
    	
    	@Query("from XaCmsUser xcu where xcu.userName=?1 and xcu.status=?2")
        public XaCmsUser findByUserName(String userName,int status);
        	
        
        @Query(" from Property p where p.modelId=?1")
        public List  findByModelId(Long modelId);
        
        @Query(value = "select t from XaCmsResource t where t.parentId is null and t.status=?1", countQuery = "select count(distinct t ) from XaCmsResource t where t.parentId is null and t.status=?1")
        public Page  myFind(int status, Pageable p);
        
        分页;排序:直接多加一个参数就行;
        
        limit:解决方法是讲@Query注解中的limit语句去掉，然后传一个Pageable pageable=new PageRequest(offset,limit)进去 (在JPA的@Query注解中使用limit条件)
        
     @Query学习:
    
    
    
请求错误码:
400:请求参数没有接收到
404:网页没有发现
405:不支持的请求方式
4xx都是app问题


排序;模板的时间;



微信支付:回调地址在哪里填写??  回调的时候需要注意什么?  公网?  内网?  

支付宝:配置回调地址 (授权回调地址)


hibernate映射配置 
http://www.cnblogs.com/ronnieStudy/archive/2012/12/22/2828779.html
1对1 http://blog.csdn.net/yyywyr/article/details/23619861  http://mianhuaman.iteye.com/blog/1568623
1对多  http://blog.csdn.net/ironrabbit/article/details/17137445   http://blog.sina.com.cn/s/blog_697b968901016s7f.html
多对多 http://blog.csdn.net/ironrabbit/article/details/17142305

现在基本是手工查询,太繁琐了


jsview(jsrender)使用 搜索 converters  http://www.jsviews.com/#viewobject
??????????  List 怎么搞? bool属性怎么判断??  自定义函数怎么搞(,分割,取首图)


yaml yml??? 如何使用????


jquery验证规则(第三方的):https://niceue.com/validator/


？？？？
1：hibernate 注释映射
2：框架里面json date object code封装起来
jsvali 怎么绑定
时间冒泡，事件被绑定，再次绑定


待研究功能，支付宝银联微信批量提现；退款；
侧边栏处理；资源管理搜索优化；拼音搜索；

事物处理??? 难点
临时表？？

钱数要具右边，带有千分位
原因：不超过15位； 长的字段要居中对齐；显示title；


数据库死锁：http://blog.csdn.net/xiaobei4929/article/details/25334885


todo:超级转转 限制当天次数；

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)