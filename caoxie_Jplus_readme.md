## Jplus框架使用说明 ##

# 声明 #
jplus 是一个java框架，web只是他的一个模块，他并非重复造轮子，初衷是希望把所有好的合适的框架集合到一起，能发挥出对开发者更大的作用。
框架思想主要参考@黄勇 的smart，推荐大家去看看，特别是AOP的部分；

# 关于Jplus #
1. 支持零配置，所有配置可由.properties或代码管理。
2. 提供可以媲美Spring的 IOC、AOP、MVC，及各种强大的第三方定制插件。
3. 快速开发，框架~200Kb,所有插件可插拔。

# 模块分类: #
- Com.jplus
	- framework  				-框架
		- Aop					-面向切面Aop实现，代理责任链,提供JDK/Cglib代理
		- Bean					-容器上下文，bean的生命周期维护
		- Core					-框架核心；类加载器、配置管理
		- Db						-dataSorce管理，事务管理。[支持多数据源]
		- Ioc					-自动依赖注入
		- Junit					-单元测试
		- Mvc					-webAction管理，路由分发，restful风格
		- Plugin					-插件管理
		- Util					-附属工具类
		- AppConstant			-系统变量区
		- InstanceFactory		-单例工厂，用于动态配置核心模块
	- Plugins				-插件包，
		- Activemq				-activemq 消息队列
		- C3p0					-c3p0 数据库连接池，Spring推荐
		- Druid					-druid 数据库连接池,阿里开源库
		- J2cache				-二级缓存框架，OSC开源框架
		- Mybatis				-可能是最好的数据库orm框架
		- Quartz					-定时调度框架，
		- Rpc					-Rpc远程过程调用框架，仿dubbo[支持三种通讯形式]
		- .......

*注：1. Framework框架包不依赖任何 plugins插件包中内容，插件全部可选装。*

# 初始化流程： #
![](http://static.oschina.net/uploads/space/2016/0826/115119_dfmK_224195.png)


> 项目启动：CoreLoader -->BeanHandle -->ActionHandle -->PluginHandle -->AopHandle -->IocHandle

关于Bean管理
> 项目启动后CoreLoader 加载 BeanHandle,同时BeanHandle 初始化ConfigHandle，
> 获取一系列相应的用户配置信息。
> 然后扫描 ${app.scan.pkg} 包中所有带@Component注解的class,

*Ps:在项目中运行时获取 bean 对象可以使用：BeanHandle.getBean(Class  cls);*
# 关于MVC： #
> Demo : com.demo.web.action.WebAction

### 关于请求： ###

    @Controller								申明：标示当前类为Action，必须
    @Request.All("/test")						[type]action 前缀，非必须
    
    @Request.Get("/blog/list/{page}")			[get]获取博客列表，第{page}页
    @Request.Get("/blog/{id}")					[get]获取博客，id为{id}
    @Request.Post("/blog") 						[post]新增博客
    @Request.Put("/blog")						[put]修改博客	 
    @Request.Delete("/blog/{id}")				[Delete]删除博客，id为{id}

### 关于入参： ###
> 1. 支持下标取参[仅用于resful]
> 1. 支持注解@Param取参[支持resful,reqeust] 

Demo：

    /**
     * 入参测试 
     * 入参是无序的。
     * @param req 获取http对象，可以支持4种类型
     * @param xb 默认取值restful下标入参
     * @param xx 按名称取值，可取restful、request入参
     */
    @Request.Get("/param/{xx}")
    public Result param(HttpServletRequest req, String xb, @Param("xx") String xx) {
    	System.err.println("req:" + req.getParameter("xx"));
    	System.err.println("下标:" + xb);
    	System.err.println("注解:" + xx);
    	/**
    	 * 结论：xb==xx的，如果request和restful均有同名入参，优先以reqeust为准。
    	 * 
    	 * restful下标取值说明：
    	 * 方法入参支持类型[9种],4种http+5种基本数据类型，除去4种http,
    	 * 剩下无@Param注解的基本数据类型入参，按restful中{xx}占位顺序依次取值，注入。
    	 * 
    	 */
    	return new Result(true);
    }


> 注：方法入参注入支持5种基本数据类型：
> int/Integer、long/Long、double/Double、BigDecimal、String
> 支持4种http对象类型：
> HttpServletRequest,HttpServletResponse,ServletContext,HttpSession

### 关于返回: ###
> Action默认支持以下返回类型：
> 
> 1. View		返回视图
> 2. Result	返回json对象
> 3. 自定义	返回自定义类型的json对象
> 4. void  	通过WebUtil自定义返回输出

# 关于AOP: #
> **使用jdk，Cglib动态代理技术实现，采用责任链模式，递归代理。**

默认AOP提供三种代理：

1.AspectProxy切面代理，提供6种切点方式：
    	
    //开始
    public void begin() 
    //拦截
    public boolean intercept(Class  cls, Method method, Object[] params)  
    //前
    public void before(Class  cls, Method method, Object[] params) throws Throwable 
    //后
    public void after(Class  cls, Method method, Object[] params, Object result)  
    //异常
    public void error(Class  cls, Method method, Object[] params, Throwable e) 
    //结束
    public void end() 
    

使用方式：

> 对自定义切面类继承AspectProxy抽象类，并重写目标方法，
> 然后对该类添加@Aspect注解。
> 
> @Aspect注解说明：
> Pkg：想要被代理类所在的包名。
> Cls：想要被代理的具体类，和pkg二选一。
> Annotation：想要被代理的类是有指定注解的类。


2.TransactionProxy事务代理：
使用方式：
> 在想要被事务代理的类、或类的方法上添加注解：`@Transaction`即可。

3.PluginProxy 插件代理：
> 这个插件代理就比较灵活了。他是对于上诉两种代理的补充，可以用于扩展任意规则、任意场景代理实现。
> 该类仅有一个获取代理链方法：
> `public abstract List getTargetClassList()`
> 具体代理被执行时，会执行实现了Proxy接口的doProxy()方法.
> 使用方式：请参考：`com.jplus.plugins.j2cache.proxy.J2CachePluginProxy`

# 关于IOC: #
> 框架中，ioc初始化位于项目启动最后阶段。
> 之前的MVC，AOP，Plugin 已经是创建了所有项目中所需的bean对象，
> 在最后要做的就是把这些 对象 互相关联起来，建立原本的依赖关系。

### 使用方法： ###
1.`private @Autowired ITestServer server1;// 通过接口注入`
>  通过接口注入，框架会找到容器中的第一个接口实现类进行注入，实现类必须>=1，否则异常

2.`private @Autowired("Server2") ITestServer server2;// 通过指定接口实现注入`
> 通过指定接口实现注入，实现类上必须标明当前名称`@Service("Server2")`才能注入成功

3.`private @Autowired TestServer2Impl server3;// 通过指定对象注入`
> 这个没什么好说的，直接注入目标类即可

4.`private @Value("rpc.registry.address") String registryAddress;// 注入配置文件`

5.`private @Autowired DruidPlugin druid;// 插件注入`
> 说明.只要是bean容器管理了的对象，都可通过`@Autowired` 注入。

6.其实还可以自定义注解注入；只要自定义注解实现了`@Component`注解即可;
比如： 

    private @RpcConsumer ITestServer server;// RPC客户端代理注入

# 关于Junit： #

### 使用说明： ###

> 基本类添加两个注解：`@RunWith`、`@ContextConfiguration` 即可：
> 说一下配置文件配置： 
> 加载配置文件,多个文件以;分割 
> 
> "file:/db.properties;classpath:app.properties"	//过个配置文件，一个文件目录，一个classpath目录
> "file:/app.properties"						//系统根目录
> "app.properties"								//项目根目录
> "/app.properties"								//项目WEB-INF下
> "classpath:app.properties"					//项目ClassPath下

**Demo:**

    @RunWith(JplusJunit4Runner.class)
    @ContextConfiguration(locations = "classpath:app.properties")
    public class _Test_RPC {
    
    	private @RpcConsumer(serviceType = ServiceType.Scoket) ITestServer rpcClient1;
    	private @RpcConsumer(serviceType = ServiceType.Netty) ITestServer rpcClient2;
    
    	@Test
    	public void test() {
    		System.out.println(rpcClient1.getMsg());
    		System.err.println(rpcClient2.getMsg());
    	}
    
    }

#  关于Plugin: #
> 加载plugins是在IOC前一步，会扫描配置文件中${plugin.allClass} 所配置的插件类列表，以分号 ; 分割。
> 加载顺序会按照配置顺序类，并且所有的插件类都必须实现：Plugin接口。
> 
> 目前插件有：c3p0,druid,activemq,mybatis,j2cache,rpc,quartz...



未完待续。。。。

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)