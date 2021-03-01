# ApiStarter

#### 项目介绍
服务端基础通用框架提取,配以详细的说明文档,针对Restful风格API服务器,降低学习成本,提高开发效率.

#### 系统架构
本项目统一使用post请求访问接口,
使用AdapterController作为统一的api入口.
请求业务模块为service的类名,请求业务方法为service的方法名,
在AdapterController方法中,通过@PathVariable获取请求参数中的模块与业务方法,
通过ApplicationContext获取模块对象,使用反射method.invoke执行真正的调用方法.
在ResponseHandlerAspect与ApiRecordAspect两个切面中分别对请求结果包装以及请求访问日志记录,
使用JWT为登录用户颁发Token,在JwtTokenAspect切面中,对所有service中方法包含自定义注解@TokenValidate的方法进行Token验证.

在牺牲了一小部分反射带来的性能浪费的下,极大的简化了开发操作流程,使用户能够更快的进行服务端开发,专注业务实现.

![Image text](https://gitee.com/weixin54321a/ApiStarter/raw/master/resource/request.png)

#### 软件环境
    
技术|描述|
---|---|
SpringBoot|项目框架
JWT|Token管理工具
Mybatis|持久层框架
Druid|数据库连接池及监控
Mysql | 数据库 
Maven | 项目构建管理
logback | 日志管理

#### 相关插件
插件|描述|
---|---|
Lombok|简化getter/setter/logger等代码编写
Mybatis Generator|根据库表自动生成model,查询example,mapper,xml插件
Mybatis Generator plgins| 自定义Mybatis Generator插件,改变生成代码行为
PageHelper mybatis|分页插件

#### 目录结构描述

```shell
.
├── java java文件
    └── com
        └── framework
            ├── annotations 自定义注解
                └── TokenValidate.java Token验证注解,在service里需要登录才能访问的方法加上此标记
            ├── bean 数据封装
                ├── request 请求数据包装
                └── response 响应数据包装
            ├── conf 系统配置
                ├── aspect 切面配置
                    ├── ApiRecordAspect.java 请求日志切面,此处记录API请求响应以及相关数据
                    ├── JwtTokenAspect.java Token切面,此处对有TokenValidate标记的注解进行Token校验
                    └── ResponseHandlerAspect.java 响应处理切面,对系统api调用数据进行封装,异常解析包装处理
                ├── druid druid sql监控配置文件
                ├── filter 过滤器
                    └──  WebConfiguration.java web请求过滤器(*练习*)
                └── properties 配置文件
                    └── SystemProperties.java 系统自定义配置文件,在application*.yml配置
            ├── constant 系统常量
            ├── controller 控制器,程序请求统一入口
            ├── dao dao层
                └── mybatis mybatis相关
                    ├── generator mybatis generator 代码生成
                        ├── plugins mybatis generator 自定义插件,实现生成代码行为自定义
                        └── MybatisGenerator.java 根据数据库表生成java model与查询example的主类.
                    ├── mapper mybatis 生成的表对应的mapper类
                    └── model mybatis 生成的表对应的model
            ├── dto 数据封装简单对象
            ├── doc 自定义javaDoc插件,根据注释生成接口文档模板
            ├── exception 异常信息
                ├── handler 全局异常管理实现
                └── 其他自定义异常信息
            ├── linerunner 启动初始化业务相关操作,例如一些缓存,初始化管理员账号等,可在此操作
            ├── pay 支付相关
                ├── client 不同支付sdk client 统一单利初始化
                ├── controller 支付回调通知统一入口
                └── service 支付业务接口
                    └──impl 不同支付方式具体实现
            ├── serivce 业务接口 业务具体操作在此处进行
                └── impl 业务具体实现,对于需要Token验证的方法,加上自定义@TokenValidate注解
            ├── task 通过Scheduled注解实现cron表达式的定时任务   
            └── utils 工具类
                └── jwt Token具体实现
└── resources 配置文件资源
    ├── mybatis  mybatis相关配置
        ├── confug mybatis配置文件
        ├── generator generator代码生成策略,路径等相关配置文件
        ├── mapper generator生成mapper.xml文件
    ├── application.yml 各个环境相同配置文件
    ├── application-dev.yml 测试环境独有配置文件
    ├── application-prod.yml 生产环境独有配置文件
    └── logback-spring.xml logback日志配置文件,指定日志滚动策略,级别等.
```

#### 快速安装

1. 克隆项目到本地Ide
2. 安装数据库,更新application-dev/prod.yml数据源配置,导入sql文件
3. 配置Maven环境,拉取jar包
4. 执行Application类main函数,启动项目
5. 使用post请求接口,获得响应

#### 数据库监控访问后台

    ip:port/druid/index.html
    示例:
    
![Image text](https://gitee.com/weixin54321a/ApiStarter/raw/master/resource/druid.png)


#### 接口描述
    
    由于本项目是通过反射调用service实现restful风格的接口,而swagger是通过@ReqestMapping+swagger注解
    来定位接口的,所以集成swagger比较麻烦,还需要额外维护swagger,所以这里放弃使用了
    推荐一个使用免费的在线接口描述文档工具APIVIEW,官网地址https://www.apiview.com,基本满足小型项目的使用,
    另外也可以搭建confluence,搭建挺简单的,做好数据备份就可以了

#### 执行流程
##### 键入域名回车

##### 域名解析
    
    作用: DNS解析的作用是把域名解析成相应的IP地址，根据IP地址决定将报文发给谁。
	
	浏览器开始解析域名,即查找过程.
	浏览器自身DNS缓存(缓存一分钟,最大1000条左右)-->
	操作系统自身DNS缓存-->
	本机host文件映射-->
	Windows调用53端口发送UDP请求
	本地配置首选DNS服务器--> Root Server获取gTLD Server-->	
	gTLD Server获取Name Server-->
	Name Server获取子Name Server ... -->
	Name Server返回IP地址给本机 -->
	浏览器缓存结果 -->
	结束
	
##### 建立连接TCP/TP连接

	准备:服务器启动,监听9999端口
	客户端使用操作系统随机分配的端口号(1000~65535)与服务器的IP+端口号通过三次握手,建立连接(浏览器没有填写端口号默认为80)
	
	TCP标志位,有6种标示:
    SYN(synchronous建立联机)
    ACK(acknowledgement 确认)
    PSH(push传送)
    FIN(finish结束)
    RST(reset重置)
    URG(urgent紧急)
    Sequence number(顺序号码)
    Acknowledge number(确认号码)
	TCP状态标识:
	LISTEN - 侦听来自远方TCP端口的连接请求; 
    SYN-SENT -在发送连接请求后等待匹配的连接请求; 
    SYN-RECEIVED - 在收到和发送一个连接请求后等待对连接请求的确认; 
    ESTABLISHED- 代表一个打开的连接，数据可以传送给用户; 
    FIN-WAIT-1 - 等待远程TCP的连接中断请求，或先前的连接中断请求的确认;
    FIN-WAIT-2 - 从远程TCP等待连接中断请求; 
    CLOSE-WAIT - 等待从本地用户发来的连接中断请求; 
    CLOSING -等待远程TCP对连接中断的确认; 
    LAST-ACK - 等待原来发向远程TCP的连接中断请求的确认; 
    TIME-WAIT -等待足够的时间以确保远程TCP接收到连接中断请求的确认; 
    CLOSED - 没有任何连接状态;
	
	第一次握手：建立连接时，客户端发送syn包(syn=j ack=0 seq=x)到服务器，并进入SYN_SEND状态，等待服务器确认; 
	第二次握手：服务器收到syn包，必须确认客户的SYN(ack=j+1），同时自己也发送一个SYN包(syn=k），即SYN+ACK包，此时服务器进入SYN_RECV状态; 
	第三次握手：客户端收到服务器的SYN＋ACK包，向服务器发送确认包ACK(ack=k+1)，此包发送完毕，客户端和服务器进入ESTABLISHED状态，完成三次握手。
	至此浏览器随机端口与服务器端口的TCP/IP连接建立成功
	
	?:为何TCP建立连接需要三次握手,而不是两次,四次
	第一次握手： A给B打电话说，你可以听到我说话吗？
    第二次握手： B收到了A的信息，然后对A说： 我可以听得到你说话啊，你能听得到我说话吗？  
    第三次握手： A收到了B的信息，然后说可以的，我要给你发信息啦！ 
    在三次握手之后，A和B都能确定这么一件事： 我说的话，你能听到; 你说的话，我也能听到。 这样，就可以开始正常通信了。
    注意： HTTP是基于TCP协议的，所以每次都是客户端发送请求，服务器应答，但是TCP还可以给其他应用层提供服务，
    即可能A、B在建立链接之后，谁都可能先开始通信。
    如果两次，那么B无法确定B的信息A是否能收到，所以如果B先说话，可能后面的A都收不到，会出现问题 。
    如果四次，那么就造成了浪费，因为在三次结束之后，就已经可以保证A可以给B发信息，A可以收到B的信息; B可以给A发信息，B可以收到A的信息。
	
##### 浏览器发送数据

	浏览器按照Line,Header,data,的格式封装HTTP请求报文
	建立一个Socket对象
	把http请求报文转变成byet[]字节
	然后调用Socket.Sent()方法经TCP连接把这些数据打包发送到服务器
	
	HTTP协议格式如下:
	请求方法 URL 版本
	
	Headers(K-V类型)
	
	请求数据
	
	注:考虑请求数据包大小与实际网络带宽,延迟,网络传输丢包等对并发量影响.
		
##### 服务器接收数据

	数据经过TCP连接传输过来以后
	Coyote HTTP/1.1 Connector监听到请求,
	创建 Request 和 Response 对象分别用于和请求端交换数据，创建新线程并传递 Request 和 Response 对象此线程,调用HttpProcesser并分配此socket给HttpProcesser
	-->
	HttpProcesser执行run方法,调用process方法创建SocketIn/OutputStream对象,解析Http协议的Line,Header,data数据,包装request与response
	-->
	Connector把该请求交给它所在的Service的Engine来处理，并等待来自Engine的回应
	-->
	Engine匹配它所拥有的所有虚拟主机Host找到对应的Host
	-->
	Host匹配它所拥有的所有Context
	-->
	请求到达DispatcherServlet

##### 分发处理	

	DispatcherServlet收到请求后,作为统一访问点,委托给其他的解析器进行处理，进行全局的流程控制
	DispatcherServlet-->    通过getHandler方法,将请求包装为HandlerExecutionChain对象
	(包含一个Handler处理器对象、多个HandlerInterceptor拦截器对象）;
	DispatcherServlet-->    通过getHandlerAdapter方法，确定当前请求处理适配器。
	DispatcherServlet-->    通过HandlerExecutionChain.applyPreHandle(processedRequest, response)方法,对请求进行intercepter拦截器组的前置处理
	DispatcherServlet-->    HandlerAdapter.handle处理器功能处理方法的调用,并返回一个ModelAndView对象
	
	                        HandlerAdapter.handle-->    AbstractHandlerMethodAdapter.ModelAndView 
	                                                    --> RequestMappingHandlerAdapter.handleInternal-->
	                                                                                    .invokeHandlerMethod
	                                                                                    返回ModelAndView对象(包含模型数据、逻辑视图名)
	                                                    
	                                                    处理方法调用
	                                                    --> ServletInvocableHandlerMethod.invokeAndHandle
	                                                                                    .invokeForRequest
	                                                                                    .doInvoke
	                                                                                    最终getBridgedMethod().invoke(getBean(), args);完成方法调用.
	                                                                                    
	                                                        
	ModelAndView的逻辑视图名——> ViewResolver， ViewResolver将把逻辑视图名解析为具体的View，通过这种策略模式，很容易更换其他视图技术;
	View——>渲染，View会根据传进来的Model模型数据进行渲染，此处的Model实际是一个Map数据结构，因此很容易支持其他视图技术;
	DispatcherServlet-->    通过HandlerExecutionChain.applyPostHandle(processedRequest, response, mv);方法,对请求进行intercepter拦截器组的后置处理
	返回控制权给DispatcherServlet，由DispatcherServlet返回响应给用户
	

##### 二次分发
    
    在DispatcherServlet分发到AdapterController后,通过代理执行AdapterController.invokeApi方法,
    请求到达invokeApi方法,首先从请求路径中获取channel(请求渠道,用以初步验证请求),module(请求模块),method(请求方法),body(请求内容)映射为方法参数
    执行方法前会根据aspect包里面的配置切面,执行环绕通知的ResponseHandlerAspect,对请求结果进行渠道验证,异常包装.
    接着执行ApiRecordAspect,对请求进行记录并存入数据库,以便将来查看日志,记录数据包括,请求模块,方法,参数,时间,请求数据,响应数据等.
    
    经切面处理后,请求到达invokeApi方法体,在此方法中:
    根据module参数,通过ApplicationContext获取执行目标模块bean
    根据method参数,构造Method对象
    method.invoke(service, body)通过反射执行module对象的方法.

    请求到达service实现类具体方法,根据JwtTokenAspect定义的切点信息,对方法上带有@TokenValidate的方法调用进行Token验证

##### 业务处理
    
    如果业务方法包含@TokenValidate注解,请求经Token验证后到达service方法体,  
    如果业务方法不包含@TokenValidate注解,请求经过 method.invoke(service, body)直接到达service方法体,
    至此,请求开始执行业务逻辑.
    
##### mybatis缓存
    
    SESSION或STATEMENT作用域级别的缓存，默认是SESSION，BaseExecutor中根据MappedStatement的Id、SQL、
    参数值以及rowBound(边界)来构造CacheKey，并使用BaseExccutor中的localCache来维护此缓存。
    全局的二级缓存，通过CacheExecutor来实现，其委托TransactionalCacheManager来保存/获取缓存
    
    MyBatis自身提供了一个简易的数据源/连接池，在org.apache.ibatis.datasource下。主要实现类是PooledDataSource，包含了最大活动连接数、
    最大空闲连接数、最长取出时间(避免某个线程过度占用)、连接不够时的等待时间，虽然简单，却也体现了连接池的一般原理
    
    MyBatis对事务的处理相对简单，TransactionIsolationLevel中定义了几种隔离级别，并不支持内嵌事务这样较复杂的场景，
    同时由于其是持久层的缘故，所以真正在应用开发中会委托Spring来处理事务实现真正的与开发者隔离。

##### 数据持久化
    
    
##### 注入简述

	1. @Autowired
    @Autowired是spring自带的注解，通过‘AutowiredAnnotationBeanPostProcessor’ 类实现的依赖注入;
    @Autowired是根据类型进行自动装配的，如果需要按名称进行装配，则需要配合@Qualifier;
    @Autowired有个属性为required，可以配置为false，如果配置为false之后，当没有找到相应bean的时候，系统不会抛错;
    @Autowired可以作用在变量、setter方法、构造函数上。
    @Autowired可以对成员变量、方法以及构造函数进行注释，而 @Qualifier 的标注对象是成员变量、方法入参、构造函数入参。
    
    2. @Inject
    @Inject是JSR330 (Dependency Injection for Java)中的规范，需要导入javax.inject.Inject;实现注入。
    @Inject是根据类型进行自动装配的，如果需要按名称进行装配，则需要配合@Named;
    @Inject可以作用在变量、setter方法、构造函数上。
    @Named("XXX") 中的 XX是 Bean 的名称，所以 @Inject和 @Named结合使用时，自动注入的策略就从 byType 转变成 byName 了。
    
    3. @Resource
    @Resource是JSR250规范的实现，需要导入javax.annotation实现注入。
    @Resource是根据名称进行自动装配的，一般会指定一个name属性
    @Resource可以作用在变量、setter方法上。
    
    @Autowired是spring自带的，@Inject是JSR330规范实现的，@Resource是JSR250规范实现的，需要导入不同的包
    @Autowired、@Inject用法基本一样，不同的是@Autowired有一个request属性
    @Autowired、@Inject是默认按照类型匹配的，@Resource是按照名称匹配的
    @Autowired如果需要按照名称匹配需要和@Qualifier一起使用，@Inject和@Name一起使用
    
##### 类加载过程
	
	类加载:通过一个类的全限定名来获取描述此类的二进制字节流
	类加载器:实现类加载的代码模块儿.	
			Bootstrap ClassLoader根加载器(启动类加载器)	JAVA_HOME/lib中的jar
			-->扩展类加载器EXT ClassLoader	JAVA_HOME/lib\ext中的jar
			-->应用类加载器APP ClassLoader	classpath指定的类库
			-->自定义类加载器
	双亲委派模型:如果一个类加载器收到了加载类的请求,它首先不会自己去尝试加载这个类,而是把请求委派给父类去完成,
	每一个层次的类加载器都是如此,因此所有的类加载请求最终都应该传送到顶层的启动类加载器中,只有当父类加载器反馈自己无法完成这个加载请求时,
	子类加载器才会尝试自己去加载.
	
	加载:读取class文件字节流
	验证:验证魔数,版本号,元数据语义分析(例如类是否继承Object),字节验证(例如int参数在方法有没有按照Long来使用),
	    符号引用数据(例如符号引用的类是否是可以被继承的)
	准备:为类静态变量分配内存并设置类变量初始零值
	解析:符号引用转换为指针,句柄相对偏移量的直接引用
	初始化:赋初始值
	使用:调用构造方法第三次赋值
	卸载:虚拟机自行完成

##### 对象回收

	引用计数算法
	
	Java可达性分析算法-->强引用,软引用,弱引用,虚引用
		通过一系列GCRootS向下搜索,搜索路径称为引用链,当对象到任何GCRoots没有任何引用相连,即GCRoots到这个对象不可达,则证明这个对象是无用对象
	
	回收算法
		标记-清除算法:首先标记处需要回收的对象,标记完成后统一回收.
			问题:标记与清除过程效率不高,标记清除后产生大量不连续空间,导致分配大对象时找不到连续的可用空间导致提前触发一次垃圾回收

	复制算法:
		将内存分为大小相等的两部分，每次只使用其中的一部分，等这部分用完了，这时候就将这里面还能活下来的对象复制到另一部分内存中，然后把剩下部分全部清理掉。
		问题:只有一半能用--

	标记整理算法
		算法不直接对可回收对象进行清理，而是让所有可用的对象都向一端移动。然后直接清理掉边界意外的内存。
		问题:整理耗时

	分代收集算法


##### 线程同步原理

##### 虚拟机参数调优
    
    JVM命令支持广泛的选项，可分为以下类别：
    
    标准选项
    	-client -server(默认)
    
    非标准选项
    	-X 显示所有可用-X选项的帮助
    	
    高级运行时选项
    	-XX:ErrorFile=filename
    
    高级JIT编译器选项
    	-XX:+AggressiveOpts 允许jit性能优化
    
    高级服务性选项
    	-XX:+HeapDumpOnOutOfMemory堆栈信息
    	
    高级垃圾收集选项
    	-XX:+CMSClassUnloadingEnabled 使用CMS垃圾收集机制


##### 对象组成
    
    对象头（Header）
        Mark world
            用于存储对象自身的运行时数据，如哈希码、GC分代年龄、锁状态标志、线程持有的锁、偏向线程ID、偏向时间戳等，
            这部分数据的长度在32位和64位的虚拟机（未开启压缩指针）中分别为32bit和64bit
        class 指针
            对象头的另外一部分是klass类型指针，即对象指向它的类元数据的指针，虚拟机通过这个指针来确定这个对象是哪个类的实例.
        length(数组独有)
            如果对象是一个数组, 那在对象头中有一块数据用于记录数组长度.
    实例数据（Instance Data）
    对齐填充（Padding）
    
    Mark Word在32位JVM中的长度是32bit，在64位JVM中长度是64bit。在不同的锁状态下存储的内容不同，在32位JVM中如图所示：

   ![Image text](https://gitee.com/weixin54321a/ApiStarter/raw/master/resource/markworld.png)
    
    Mark World解释(说明: 此处摘自https://blog.csdn.net/lkforce/article/details/81128115 )

    Mark Word记录了对象和锁有关的信息，当这个对象被synchronized关键字当成同步锁时，围绕这个锁的一系列操作都和Mark Word有关。

    其中无锁和偏向锁的锁标志位都是01，只是在前面的1bit区分了这是无锁状态还是偏向锁状态。
    
    JDK1.6以后的版本在处理同步锁时存在锁升级的概念，JVM对于同步锁的处理是从偏向锁开始的，随着竞争越来越激烈，处理方式从偏向锁升级到轻量级锁，最终升级到重量级锁。
    
     
    
    JVM一般是这样使用锁和Mark Word的：
    
    1，当没有被当成锁时，这就是一个普通的对象，Mark Word记录对象的HashCode，锁标志位是01，是否偏向锁那一位是0。
    
    2，当对象被当做同步锁并有一个线程A抢到了锁时，锁标志位还是01，但是否偏向锁那一位改成1，前23bit记录抢到锁的线程id，表示进入偏向锁状态。
    
    3，当线程A再次试图来获得锁时，JVM发现同步锁对象的标志位是01，是否偏向锁是1，也就是偏向状态，Mark Word中记录的线程id就是线程A自己的id，表示线程A已经获得了这个偏向锁，可以执行同步锁的代码。
    
    4，当线程B试图获得这个锁时，JVM发现同步锁处于偏向状态，但是Mark Word中的线程id记录的不是B，那么线程B会先用CAS操作试图获得锁，这里的获得锁操作是有可能成功的，因为线程A一般不会自动释放偏向锁。
    如果抢锁成功，就把Mark Word里的线程id改为线程B的id，代表线程B获得了这个偏向锁，可以执行同步锁代码。如果抢锁失败，则继续执行步骤5。
    
    5，偏向锁状态抢锁失败，代表当前锁有一定的竞争，偏向锁将升级为轻量级锁。JVM会在当前线程的线程栈中开辟一块单独的空间，里面保存指向对象锁Mark Word的指针，
    同时在对象锁Mark Word中保存指向这片空间的指针。上述两个保存操作都是CAS操作，如果保存成功，代表线程抢到了同步锁，就把Mark Word中的锁标志位改成00，
    可以执行同步锁代码。如果保存失败，表示抢锁失败，竞争太激烈，继续执行步骤6。
    
    6，轻量级锁抢锁失败，JVM会使用自旋锁，自旋锁不是一个锁状态，只是代表不断的重试，尝试抢锁。从JDK1.7开始，自旋锁默认启用，自旋次数由JVM决定。如果抢锁成功则执行同步锁代码，如果失败则继续执行步骤7。
    
    7，自旋锁重试之后如果抢锁依然失败，同步锁会升级至重量级锁，锁标志位改为10。在这个状态下，未抢到锁的线程都会被阻塞。
        

##### JDBC

	加载驱动，建立连接 
	创建语句对象 
	执行SQL语句 
	处理结果集 
	关闭连接
	MySQL优化

##### 存储过程
    
    ?: 跨磁道存储对存储速度的影响.

##### 索引
    
    索引类型:
    B-Tree索引 平衡树
    哈希索引    哈希索引只包含哈希值和行指针，而不存储字段值。
                无法用于排序，不是按照索引值顺序存储的
                不支持部分索引列匹配查找,因为哈希索引是使用索引列的全部内容来计算哈希值得
                只支持等值比较查询，包括=、IN()、  不支持范围索引
    空间数据索引(RTree) 极端情况下会造成全部搜索 
    
    B+Tree
    度 节点横向扩展
    MYISAM 文件数据分开存储
    Innodb 聚集索叶子节点包含数据,普通索引需要查找聚集索引(主键索引)
    
    索引种类:
        普通索引：查找主键信息-->根据主键查找聚集索引-->拿到值
        全文索引：对文本的内容进行分词，进行搜索
        索引合并: 使用多个普通单列索引组合搜索
        组合索引：多列值组成一个索引，专门用于组合搜索，其效率大于索引合并
        覆盖索引: 搜索的值存在与索引中直接返回,不需要拿到主键信息进行再次查找
        主键索引：聚集索引
        通过聚集索引可以查到需要查找的数据， 而通过非聚集索引可以查到记录对应的主键值 ， 再使用主键的值通过聚集索引查找到需要的数据

    索引命中:
        1. 前导模糊查询不能利用索引(like '%XX'或者like '%XX%')
        2. 如果条件中的or包含非索引字段，即使其中有条件带索引也不会使用
        3. 如果估计使用全表扫描要比使用索引快,则不使用索引
        4. 如果需要把空值存入索引，方法有二：其一，把NULL值转为一个特定的值。其二，建立一个复合索引
    
##### class文件结构
    
    魔数          0xCAFEBABE
    主版本号
    次版本号
    常量池计数器  常量成员+1 0表示Object的父类索引不引用任何一个常量池项
    常量池
    访问标志
    父类索引
    接口计数器
    接口表
    方法计数器
    方法表
    属性计数器
    属性表
    
    
    
##### 断开TCP/IP连接

     TCP的连接的拆除需要发送四个包，因此称为四次挥手(four-way handshake)。客户端或服务器均可主动发起挥手动作，在socket编程中，任何一方执行close()操作即可产生挥手操作。
    
    (1）客户端A发送一个FIN，用来关闭客户A到服务器B的数据传送。 
    
    (2）服务器B收到这个FIN，它发回一个ACK，确认序号为收到的序号加1。和SYN一样，一个FIN将占用一个序号。 
    
    (3）服务器B关闭与客户端A的连接，发送一个FIN给客户端A。 
    
    (4）客户端A发回ACK报文确认，并将确认序号设置为收到序号加1。 


##### 浏览器解释数据

	浏览器接收到来自服务器的HTTP数据,解析line,header,body,按顺序解释HTML文本,所以js一般放在body的最后一行,防止Dom未加载完成时,js初始化对dom操作而报错

##### Tomcat

	单实例单应用 (一个tomcat 一个web应用)				缺点:浪费资源
	单实例多应用 (一个tomcat多个应用)					缺点:升级一个应用要挂掉整个Tomcat,维护麻烦
	多实例单应用 (多个tomcat都部署一个应用)			    缺点:某个应用升级失败会导致用户访问到不同的版本实例		nignx反向代理-->服务器安装OpenSSL模块实现Https协议
	多实例多应用 (多个tomcat部署多个不同的应用)		    

    本项目使用内置Tomcat,通过application.yml的server进行Tomcat相关配置
    
    配置名称                                        描述
    server.tomcat.internalProxies                   正则表达式匹配可信IP地址。
    server.tomcat.protocolHeader                    保持传入协议的报头，通常称为X-Forwarded-Proto
    server.tomcat.protocolHeaderHttpsValue          协议值,指明是否开启SSL支持
    server.tomcat.portHeader                        用于重写原始端口值的HTTP报头的名称X-Forwarded-Port
    server.tomcat.remoteIpHeader                    提取远程IP的HTTP报头的名称。例如，`X-FORWARDED-FOR`
    server.tomcat.basedir                           Tomcat的基本目录。如果未指定，则使用临时目录
    server.tomcat.backgroundProcessorDelay          
    server.tomcat.maxThreads                        最大工作线程数
    server.tomcat.minSpareThreads                   最小工作线程数
    server.tmocat.maxHttpHeaderSize                 HTTP消息报头的最大大小(以字节为单位）
    server.tomcat.redirectContextRoot               是否将请求context重定向到其他PATH
    server.tomcat.useRelativeRedirects              
    server.tomcat.uriEncoding                       用于解码URI的字符编码
    server.tomcat.maxConnections                    最大socket连接到tomcat的连接数
    server.tomcat.acceptCount                       当前连接数超过maxConnections的时候，还可接受的连接数，即tcp的完全连接队列(accept队列)的大小.
    
    TomcatWebServerFactoryCustomizer类实现了WebServerFactoryCustomizer-->实现了WebServerFactoryCustomizer
    在TomcatWebServerFactoryCustomizer中进行了一系列的application.yml中Tomcat属性配置到程序配置的转化过程
    
    
### SpringBoot配置文件加载顺序

    1. 开发者工具 `Devtools` 全局配置参数;
    2. 单元测试上的 `@TestPropertySource` 注解指定的参数;
    3. 单元测试上的 `@SpringBootTest` 注解指定的参数;
    4. 命令行指定的参数，如 `java -jar springboot.jar --name="Java"`;
    5. 命令行中的 `SPRING_APPLICATION_JSONJSON` 指定参数, 如 `java -Dspring.application.json='{"name":"Java"}' -jar springboot.jar`
    6. `ServletConfig` 初始化参数;
    7. `ServletContext` 初始化参数;
    8. JNDI参数(如 `java:comp/env/spring.application.json`)
    9. Java系统参数(来源：`System.getProperties()`)
    10. 操作系统环境变量参数;
    11. `RandomValuePropertySource` 随机数，仅匹配：`ramdom.*`;
    12. JAR包外面的配置文件参数(`application-{profile}.properties(YAML）`）
    13. JAR包里面的配置文件参数(`application-{profile}.properties(YAML）`）
    14. JAR包外面的配置文件参数(`application.properties(YAML）`）
    15. JAR包里面的配置文件参数(`application.properties(YAML）`）
    16. `@Configuration`配置文件上 `@PropertySource` 注解加载的参数;
    17. 默认参数(通过 `SpringApplication.setDefaultProperties` 指定)   
    数字小的优先级越高，即数字小的会覆盖数字大的参数值

### Jenkins自动部署
1. 目标: Git代码变更通知Jenkins,Jenkins拉取代码自动构建,执行部署脚并备份文件
2. 搭建步骤:服务器到期了,买了服务器再搭建一遍然后写搭建步骤...

### 版本信息
1. 版本: 0.1

### 开发者

推荐 : QQ群 : 546556883
1. 微信: weixin54321a
2. QQ: 735376047
如果您在使用过程中有疑问或建议,欢迎提出.

### 更新信息
    
    暂无

### 

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)