#20151005
	alibaba Dubbo 项目本地测试，初始化，并完成简单的功能测试点，快速完成简单的功能点测试，服务提供者/服务消费者功能，完成 Hello World的结果输出；
	
#20151007
	引入了 maven-assembly-plugin 插件， 在打包过程中将部分依赖文件(lib)，添加到jar包中；	配置文件需要打进 jar 包；需要指定 main 入口类； 所依赖的第三方库也要打进 jar 包；
		pom.xml 文件中增加   标签段，	
	这样，针对 Dubbo-provider 项目 执行  mvn assembly:assembly ， 就能够将 依赖的jar文件和配置文件打包进jar包中；在target文件夹中生成  Dubbo-provider-0.0.1-RELEASE.jar
	cmd命令行中执行 ：   java -cp Dubbo-provider-0.0.1-RELEASE.jar com.Dubbo.provider.demo.main.DemoProviderMain
				 java -jar Dubbo-provider-0.0.1-RELEASE.jar
		这样，服务提供方的功能已经启动，只需要在 Dubbo-customer 模块中 执行 服务消费者 即可；
	
	单元测试已经通过；
	
#20151008
	上下文信息：
		http://dubbo.io/User+Guide-zh.htm#UserGuide-zh-%E4%B8%8A%E4%B8%8B%E6%96%87%E4%BF%A1%E6%81%AF
		服务消费者、服务提供者： 	上写文信息 传递；
			上下文中存放的是当前调用过程中所需的环境信息。
			RpcContext是一个ThreadLocal的临时状态记录器，当接收到RPC请求，或发起RPC请求时，RpcContext的状态都会变化。比如：A调B，B再调C，则B机器上，在B调C之前，RpcContext记录的是A调B的信息，在B调C之后，RpcContext记录的是B调C的信息。
			
		隐式传参：
		可使用 	RpcContext.getContext().setAttachment("index", "1");(消费方) 	RpcContext.getContext().getAttachment("index");(提供方)
		在 服务消费方 服务提供方 之间 进行数据传递
	
	异步调用：
		基于NIO的非阻塞实现并行调用，客户端不需要启动多线程即可完成并行调用多个远程服务，相对多线程开销较小；	如果有多个serivce层需要调用的话，使用这种方式，调用时间仅仅为最长的那个时间；
		客户端配置声明：	customer.xml
			 
			       
			 
		客户端调用代码：
			fooService.findFoo(fooId); // 此调用会立即返回null
			Future  fooFuture = RpcContext.getContext().getFuture(); // 拿到调用的Future引用，当结果返回后，会被通知和设置到此Future。
			Foo foo = fooFuture.get(); // 如果foo已返回，直接拿到返回值，否则线程wait住，等待foo返回后，线程会被notify唤醒。
		
		  sent部分用来设置是否等待消息发出： true等待消息发出，发送失败则抛出异常；false不等待消息发出；
		如果只是简单的单纯异步调用，完全忽略返回值的话，则可以配置 return="false" 部分，减少Future对象的创建和管理成本；
		
	参数回调：
		查看Dubbo-api Dubbo-customer Dubbo-provider 三個模塊的callback包下的方法；
		参数回调方式与调用本地callback或listener相同，只需要在Spring的配置文件中声明哪个参数是callback类型即可，Dubbo将基于长连接生成反向代理，这样就可以从服务器端调用客户端逻辑。
			Callback包下的例子，可以在服務端獲取到客戶端傳遞過來的key參數，並且封裝數據類型返回給客戶端；
			
#20151009
	事件通知
		待完成；
		
#20151012
	事件通知，bug修复；之前setId()方法中，未使用定义；现阶段事件通知功能已测试完成；
	事件通知： 在调用之前，调用之后，出现异常时，会触发oninvoke, onreturn, onthrow三个事件，可以配置当事件发生时，通知哪个类的哪个方法。
		在服务消费者调用服务提供者的某个方法的时候，将通知服务消费者的某个方法（NotifyImpl.onreturn()/NotifyImple.onthrow()）方法；
			通知消费者某个方法正在执行，并且放回相对应的数据参数形式；
				async=true，表示结果是否马上返回.
				onreturn 表示是否需要回调.
				组合情况：(async=false 默认)
					异步回调模式：async=true onreturn="xxx"
					同步回调模式：async=false onreturn="xxx"
					异步无回调 ：async=true
					同步无回调 ：async=false
	
	本地存根：
		远程服务后，客户端通常只剩下接口，而实现全在服务器端，但提供方有些时候想在客户端也执行部分逻辑，比如：做ThreadLocal缓存，提前验证参数，调用失败后伪造容错数据等等，
			此时就需要在API中带上Stub，客户端生成Proxy时，会把Proxy通过构造函数传给Stub，然后把Stub暴露给用户，Stub可以决定要不要去调Proxy。
			
	本地伪装：
		Mock通常用于服务降级，比如某验权服务，当服务提供方全部挂掉后，客户端不抛出异常，而是通过Mock数据返回授权失败。
		
		Mock是Stub的一个子集，便于服务提供方在客户端执行容错逻辑，因经常需要在出现RpcException(比如网络失败，超时等)时进行容错，而在出现业务异常(比如登录用户名密码错误)时不需要容错，
		如果用Stub，可能就需要捕获并依赖RpcException类，而用Mock就可以不依赖RpcException，因为它的约定就是只有出现RpcException时才执行。
		
			在Dubbo开发过程中，可能由于服务没有启动或者说网络不通，调用过程中会出现RpcException，也就是远程调用失败，如果是服务器启动顺序的问题，可以使用check=false的配置得到解决；
			如果是服务down掉或者并发数太高导致的RpcException，比如列表页在大并发的情况下，查询出来的列表数据为空，恢复正常情况后，列表数据又查询出来，这时候，可以使用mock实现这个逻辑，
				mock只在出现非业务异常(比如超时，网络异常等)时执行
	
	延迟暴露：
		如果你的服务需要Warmup时间，比如初始化缓存，等待相关资源就位等，可以使用delay进行延迟暴露。
			 	延迟5秒暴露服务：
			 	延迟到Spring初始化完成后，再暴露服务：(基于Spring的ContextRefreshedEvent事件触发暴露)
		
		规避办法
			1. 强烈建议不要在服务的实现类中有applicationContext.getBean()的调用，全部采用IoC注入的方式使用Spring的Bean。
			2. 如果实在要调getBean()，可以将Dubbo的配置放在Spring的最后加载。
			3. 如果不想依赖配置顺序，可以使用 ，使Dubbo在Spring容器初始化完后，再暴露服务。
			4. 如果大量使用getBean()，相当于已经把Spring退化为工厂模式在用，可以将Dubbo的服务隔离单独的Spring容器。
			
	并发控制：
	
		限制com.foo.BarService的每个方法，服务器端并发执行（或占用线程池线程数）不能超过10个：
			 
		限制com.foo.BarService的sayHello方法，服务器端并发执行（或占用线程池线程数）不能超过10个：
			 
			     
			 
		限制com.foo.BarService的每个方法，每客户端并发执行（或占用连接的请求数）不能超过10个：
			 
			
			 
		限制com.foo.BarService的sayHello方法，每客户端并发执行（或占用连接的请求数）不能超过10个：
			 
			     
			 

			 
			     
			 
		如果 和 都配了actives， 优先
	
	连接控制：
		
		限制服务器端接受的连接不能超过10个：（以连接在Server上，所以配置在Provider上）
			 
			 
			
		限制客户端服务使用连接连接数：(如果是长连接，比如Dubbo协议，connections表示该服务对每个提供者建立的长连接数)
			 
			 
			
		如果 和 都配了connections， 优先	
		
	延迟链接：
		延迟链接，用于减少长连接数，当有调用发起时，在创建长连接，只对使用长连接的dubbo协议生效；  
		
	粘滞连接
		粘滞连接用于有状态服务，尽可能让客户端总是向同一提供者发起调用，除非该提供者挂了，再连另一台。粘滞连接将自动开启延迟连接，以减少长连接数
		 
		
	令牌验证
		防止消费者绕过注册中心访问提供者; 在注册中心控制权限，以决定要不要下发令牌给消费者; 注册中心可灵活改变授权方式，而不需修改或升级提供者;
		
#20151013
	路由规则
		向注册中心写入路由规则：(通常由监控中心或治理中心的页面完成)
			可以用来设置 白名单、黑名单、读写分离、前后端分离……
			
	服务降级：
		向注册中心写入动态配置覆盖规则：(通过由监控中心或治理中心的页面完成)
		registry.register(URL.valueOf("override://0.0.0.0/com.foo.BarService?category=configurators&dynamic=false&application=foo&mock=force:return+null"));
			mock=force:return+null 		表示消费方对该服务的方法调用都直接返回null值，不发起远程调用。屏蔽不重要服务不可用时对调用方的影响。
			mock=fail:return+null		表示消费方对该服务的方法调用在失败后，再返回null值，不抛异常。容忍不重要服务不稳定时对调用方的影响。
			
	优雅停机：
		Dubbo是通过JDK的ShutdownHook来完成优雅停机的，所以如果用户使用"kill -9 PID"等强制关闭指令，是不会执行优雅停机的，只有通过"kill PID"时，才会执行。
			 
			       
			 
		原理：  	服务提供方
					停止时，先标记为不接收新请求，新请求过来时直接报错，让客户端重试其它机器。 然后，检测线程池中的线程是否正在运行，如果有，等待所有线程执行完成，除非超时，则强制关闭。
				服务消费方
					停止时，不再发起新的调用请求，所有新的调用在客户端即报错。 然后，检测有没有请求的响应还没有返回，等待响应返回，除非超时，则强制关闭。
					
	日志适配&&访问日志
		缺省自动查找： log4j slf4j jcl jdk	 
		将访问日志输出到当前应用的log4j日志：	  
		将访问日志输出到指定文件：		  
		
	服务容器
		服务容器是一个standalone的启动程序，因为后台服务不需要Tomcat或JBoss等Web容器的功能，如果硬要用Web容器去加载服务提供方，增加复杂性，也浪费资源。
		服务容器只是一个简单的Main方法，并加载一个简单的Spring容器，用于暴露服务。
		服务容器的加载内容可以扩展，内置了spring, jetty, log4j等加载，可通过Container扩展点进行扩展
			如：(缺省只加载spring) 自动加载META-INF/spring目录下的所有Spring配置。
				配置：(配在java命令-D参数或者dubbo.properties中) dubbo.spring.config=classpath*:META-INF/spring/*.xml ----配置spring配置加载位置
				java com.alibaba.dubbo.container.Main 
		
	dubbo://
		Dubbo缺省协议采用单一长连接和NIO异步通讯，适合于小数据量大并发的服务调用，以及服务消费者机器数远大于服务提供者机器数的情况。
		Dubbo缺省协议不适合传送大数据量的服务，比如传文件，传视频等，除非请求量很低。
		Dubbo协议缺省每服务每提供者每消费者使用单一长连接，如果数据量较大，可以使用多个连接。
			 或 表示该服务使用JVM共享长连接。(缺省)
			 或 表示该服务使用独立长连接。
			 或 表示该服务使用独立两条长连接。
	
	Telnet命令
		Dubbo2.0.5以上版本服务提供端口支持telnet命令，
			使用如： telnet localhost 20880 或者： echo status | nc -i 1 localhost 20880
			
#20151014
	服务化最佳实践
		分包
			建议将服务接口，服务模型，服务异常等均放在API包中，因为服务模型及异常也是API的一部分， 同时，这样做也符合分包原则：重用发布等价原则(REP)，共同重用原则(CRP)
			如果需要，也可以考虑在API包中放置一份spring的引用配置，这样使用方，只需在Spring加载过程中引用此配置即可， 配置建议放在模块的包目录下，以免冲突，如：com/alibaba/china/xxx/dubbo-reference.xml
			
		粒度
			服务接口尽可能大粒度，每个服务方法应代表一个功能，而不是某功能的一个步骤，否则将面临分布式事务问题，Dubbo暂未提供分布式事务支持。
			服务接口建议以业务场景为单位划分，并对相近业务做抽象，防止接口数量爆炸
			不建议使用过于抽象的通用接口，如：Map query(Map)，这样的接口没有明确语义，会给后期维护带来不便。
			
		版本
			每个接口都应定义版本号，为后续不兼容升级提供可能，如： 
			建议使用两位版本号，因为第三位版本号通常表示兼容升级，只有不兼容时才需要变更服务版本。
			当不兼容时，先升级一半提供者为新版本，再将消费者全部升为新版本，然后将剩下的一半提供者升为新版本。
			
		兼容性
			服务接口增加方法，或服务模型增加字段，可向后兼容，删除方法或删除字段，将不兼容，枚举类型新增字段也不兼容，需通过变更版本号升级。
			
		枚举值
			如果是完备集，可以用Enum，比如：ENABLE, DISABLE。
			如果是业务种类，以后明显会有类型增加，不建议用Enum，可以用String代替。
			如果是在返回值中用了Enum，并新增了Enum值，建议先升级服务消费方，这样服务提供方不会返回新值。
			如果是在传入参数中用了Enum，并新增了Enum值，建议先升级服务提供方，这样服务消费方不会传入新值。
		
		序列化
			服务参数及返回值建议使用POJO对象，即通过set,get方法表示属性的对象。
			服务参数及返回值不建议使用接口，因为数据模型抽象的意义不大，并且序列化需要接口实现类的元信息，并不能起到隐藏实现的意图。
			服务参数及返回值都必需是byValue的，而不能是byRef的，消费方和提供方的参数或返回值引用并不是同一个，只是值相同，Dubbo不支持引用远程对象。
			
		异常
			建议使用异常汇报错误，而不是返回错误码，异常信息能携带更多信息，以及语义更友好，
			如果担心性能问题，在必要时，可以通过override掉异常类的fillInStackTrace()方法为空方法，使其不拷贝栈信息，
			查询方法不建议抛出checked异常，否则调用方在查询时将过多的try...catch，并且不能进行有效处理，
			服务提供方不应将DAO或SQL等异常抛给消费方，应在服务实现中对消费方不关心的异常进行包装，否则可能出现消费方无法反序列化相应异常。
			
		调用
			不要只是因为是Dubbo调用，而把调用Try-Catch起来。Try-Catch应该加上合适的回滚边界上。
			对于输入参数的校验逻辑在Provider端要有。如有性能上的考虑，服务实现者可以考虑在API包上加上服务Stub类来完成检验。
			
	推荐用法
		在Provider上尽量多配置Consumer端属性
			作服务的提供者，比服务使用方更清楚服务性能参数，如调用的超时时间，合理的重试次数，等等
			在Provider配置后，Consumer不配置则会使用Provider的配置值，即Provider配置可以作为Consumer的缺省值。
			否则，Consumer会使用Consumer端的全局设置，这对于Provider不可控的，并且往往是不合理的。
			PS: 配置的覆盖规则：1) 方法级配置别优于接口级别，即小Scope优先 2) Consumer端配置 优于 Provider配置 优于 全局配置，最后是Dubbo Hard Code的配置值（见配置文档）
				在Provider可以配置的Consumer端属性有：
					timeout，方法调用超时
					retries，失败重试次数，缺省是2（表示加上第一次调用，会调用3次）
					loadbalance，负载均衡算法（有多个Provider时，如何挑选Provider调用），缺省是随机（random）。
					还可以有轮训(roundrobin)、最不活跃优先（leastactive，指从Consumer端并发调用最好的Provider，可以减少的反应慢的Provider的调用，因为反应更容易累积并发的调用）
					actives，消费者端，最大并发调用限制，即当Consumer对一个服务的并发调用到上限后，新调用会Wait直到超时。
					在方法上配置（dubbo:method ）则并发限制针对方法，在接口上配置（dubbo:service），则并发限制针对服务。
					
		Provider上配置合理的Provider端属性
			threads，服务线程池大小
			executes，一个服务提供者并行执行请求上限，即当Provider对一个服务的并发调用到上限后，新调用会Wait（Consumer可能到超时）。
					在方法上配置（dubbo:method ）则并发限制针对方法，在接口上配置（dubbo:service），则并发限制针对服务。
					
		配置上Dubbo缓存文件
			 
				文件的路径，应用可以根据需要调整，保证这个文件不会在发布过程中被清除。 如果有多个应用进程注意不要使用同一个文件，避免内容被覆盖。
				缓存：注册中心的列表、 服务提供者列表；
				有了这项配置后，当应用重启过程中，Dubbo注册中心不可用时则应用会从这个缓存文件读取服务提供者列表的信息，进一步保证应用可靠性。
				
#20151015
	Zookeeper注册中心安装
		下载zookeeper 解压tar.gz 文件，进入zookeeper解压文件，执行：cp conf/zoo_sample.cfg conf/zoo.cfg 配置  vi conf/zoo.cfg	如果不需要集群，zoo.cfg的内容如下：(其中data目录需改成你真实输出目录) 	即可；
		启动命令   ./bin/zkServer.sh start	停止命令：  ./bin/zkServer.sh stop 
		命令行: 	telnet 127.0.0.1 2181	echo dump | nc 127.0.0.1 2181
		
	并且在resources 文件夹下增加 log4j.properties文件，用来输出相关的日志记录，进一步跟踪日志记录；生成环境修改日志级别DEBUG
	
	管理控制台安装
		dubbo-admin-*.war	放置tomcat中，进行启动，修改 /WEB-INF/dubbo.properties 中的 zookeeper://127.0.0.1:2181 相关配置；
		访问: (用户:root,密码:root 或 用户:guest,密码:guest)
		即可完成管理控制台的相关操作；
		
#20151016
	新增模块： Dubbo-test-provider && Dubbo-test-consumer 两个模块，
		两个模块增加数据库相关的流程操作，并且将Service层的接口放置 Dubbo-api模块中；
		本地单元测试，provider模块提供服务，从数据库中查询出来相关数据，consumer模块获取serivce接口，并且将相关的数据值从服务端获取打印出来；
		
#20151019
	1.Dubbo发布的服务事务操作	DubboSpringAll.xml 内部引入spring-transaction.xml 文件夹，服务端处理事务操作；
	2.mybatis插入操作返回主键id的功能操作在 Dubbo-test-provider 模块的serviceImple 实现类中进行了多余操作，如果更新行数大于0，直接返回主键id;
	3.服务端 消费端 简单功能测试并通过（事务，CRUD）；
	4.使用此 Dubbo-test-provider && Dubbo-test-consumer 两个模块时，需要注意启动Zookeeper注册中心；
	
	5： Druid相关的监控功能，需要在webapp环境下配置servlet功能进行监控，此环境下无此环境，故配置了log4j的日志配置相关，完成sql相关的文件记录；
		https://github.com/alibaba/druid/wiki/%E9%85%8D%E7%BD%AE_LogFilter

#20151020
	Druid 默认提供的监控功能需要在webapp环境下，此环境下使用log4j的默认日志功能将对应的需要的数据进行输出保存在日至环境中，进行下一步监控功能的使用；
		注意 log4j.properties 文件的配置，将相关的监控点数据进行输出并保存在日志文件中；	
		
#20151021
	开启zookeeper整合，
		运行Dubbo-test-provider模块（Dubbo服务提供者），
		tomcat下运行Dubbo-test-web这个webapp模块，
			访问 http://127.0.0.1:8080/Dubbo-test-web/index	， 即可调用服务提供者提供的方法，并且将对应的值显示在页面上；
		
	至此，现阶段的模块划分为： 
		Dubbo-test-provider为普通java模块，可打包为jar,之后启动运行，作为一个服务提供者对外发布服务（事务控制，druid的监控现阶段都在此模块下进行控制）
		Dubbo-test-web 为webapp模块，打包为war,在tomcat容器下运行，作为一个服务消费者，获取到对应的service，调用provider提供的方法；
		
	PS： 需要注意的是，现阶段事务控制仅仅控制在同一个服务下，并没有完成分布式事务控制相关的流程；
	
	项目在引入Dubbo之后，XML文件报错：cvc-complex-type.2.4.c: The matching wildcard is strict, but no declaration can be found for element 'dubbo:service'.
		1： 解压缩 Dubbo-*.jar 文件，在文件中找到 dubbo.xsd 文件；
		2：windows->preferrence->xml->xmlcatalog  add->catalog entry  ->file system 
			选择刚刚下载的文件路径 修改key值和配置文件的http://code.alibabatech.com/schema/dubbo/dubbo.xsd 相同 保存。
			在xml文件右键validate  ok解决了。
	
#20151024
	考虑provider模块打包为jar文件之后，启动jar包过程中可以自定义配置部分参数属性，完成动态设定 数据库连接池、事务控制…… 相关的设定
	java -jar test.jar para1 para2 para3	后面的参数可以进行动态参数设定；
		修改 DemoDubboTest 方法，增加  org.springframework.beans.factory.config.PropertyPlaceholderConfigurer 属性配置，用来在项目启动过程中，自定义某些参数，
		同时修改部分配置文件，将 PropertyPlaceholderConfigurer 对象设定的参数值动态传递给 xml 配置文件，完成 动态配置;
		
	java -jar commons.cli 命令行参数 解析  并实现
		
	pom.xml 增加 maven-shade-plugin 插件； 在执行 mvn install 命令构建的时候，会生成 相关的jar 文件，此jar文件可以直接执行， jar -jar test.jar 
	
#20151026
	新建Dubbo-test-webservices模块（webapp模块）。对外发布 webservice 接口 。 是基于http协议的实现，暴露wenservice的标准化接口
	
#20151029
	新建
		Dubbo-RWSeparate-api							公共API接口，接口部分进行读写分离，读取数据的接口放入Read相关，写入数据的接口放入Write相关
		Dubbo-RWSeparate-provider-read					provider服务提供者接口，针对读取数据部分，数据库读写分离过程中可设定数据库为丛库
	    Dubbo-RWSeparate-provider-write					provider服务提供者接口，针对写入数据部分，数据库读写分离过程中可设定数据库为主库
	    Dubbo-RWSeparete-consumer-web					consumer服务消费者，为webapp项目，调用上面的两个服务提供者，做到读写分离

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)