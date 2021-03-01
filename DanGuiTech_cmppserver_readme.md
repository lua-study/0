
 
  
  
  
  
 hljs.initHighlightingOnLoad(); 
 
 $(document).ready(function(){
      $("h2,h3,h4,h5,h6").each(function(i,item){
        var tag = $(item).get(0).localName;
        $(item).attr("id","wow"+i);
        $("#category").append(' '+$(this).text()+'  ');
        $(".newh2").css("margin-left",0);
        $(".newh3").css("margin-left",20);
        $(".newh4").css("margin-left",40);
        $(".newh5").css("margin-left",60);
        $(".newh6").css("margin-left",80);
      });
 });
 
  




## CmppServer使用手册 ##

###版本变更记录###

- 1.0.5

- 1.0.6 修改autoDeliver=true的处理,放弃thread yield的实现。 增加removeClientConfig方法,可以删除接入(并断链)

- 1.0.7 增加getUserRunTime(String user)方法,增加速率日志。优化上行/状态报告处理逻辑。

- 1.0.8 fix bug,高并发返回report时full gc过于频繁

- 1.0.9 增加cmppserver.deliveryRetry(#上行/状态报告无法接受应答情况下是否重试,如果否则maxDeliveryRetryHtSize,maxMoRetryTimes,moRetryTimeOut三个配置无意义)的配置

###1. 概述###

####1.1 简介####

- 基于mina2.0.7 及spring4.1.7 实现了标准的Cmpp服务端，支持cmpp3.0和2.0

- 上游程序能够运行期对接入进行管理。提供下行输出和上行输入的接口供上游程序自定义 

- 提供数据统计/监控数据的相关返回以及能够自动返回上行或状态报告(模拟测试)

####1.2 如何获取####

[获取源码](https://git.oschina.net/dajiangnan/cmppserver.git)

[demo源码](https://git.oschina.net/dajiangnan/cmppserverDemo.git)

Maven坐标如下(version变量为版本变更记录中的最后一个版本号)
    
	 
	        net.oschina.dajiangnan 
	        cmppserver 
	        $version 
	 





###2. 如何使用###

####2.1 Spring配置引入####

	 

####2.2 配置Server####

	#cmppserver端口，如7890
    cmppserver.serverPort=7890
    
    #处理长连接上socket请求的线程池配置。配制进mina的配置。通过修改相关配置，可以对低效的socket请求处理容忍度进行调整。通常情况下这个值无需修改，因为对socket请求的处理属于cmppServer的内部实现
    cmppserver.corePoolSize=4
    cmppserver.maximumPoolSize=5
    cmppserver.keepAliveTime=10
    cmppserver.workQueueCapacity=5000
    
    #心跳间隔时间配置，如果InterValIdelTime时间内长连接上没有任何交互，则cmppserver会发起心跳请求。
    cmppserver.InterValIdelTime=60
    #心跳超时配置，cmppserver发起心跳后如果KeepAliveTimeOut时间内未得到应答，则会主动关闭当前连接
    cmppserver.KeepAliveTimeOut=5
    
    #是否同步进行下行处理
    cmppserver.syncProcessSubmit=false
    
    #下行处理线程池的配置。通过修改相关配置，可以调整对上游程序低效的下行输出实现的容忍度,如果cmppserver.syncProcessSubmit=true则该配置无意义
    cmppserver.submitCorePoolSize=4
    cmppserver.submitMaximumPoolSize=5
    cmppserver.submitKeepAliveTime=10
    cmppserver.submitWorkQueueCapacity=100
    
    #上游程序实现的上行输入作为生产者，cmppserver向接入发送上行或状态报告作为消费者。moQueueSize就是中间内存队列的最大值。增大这个值，则增大系统对发送上行消息缓慢的容忍度。通常情况下这个值无需修改，相关处理属于CmppServer的内部实现。
    cmppserver.moQueueSize=10
    #等待上行应答的ht大小，增大这个值，则增大系统对client低效返回应答的容忍度
    cmppserver.maxDeliveryRetryHtSize=5
    
    #上行请求如果无法得到来自接入的应答的重试次数。
    cmppserver.maxMoRetryTimes=2
    #上行请求无法得到来自接入的应答则会重试的超时时间(秒)。
    cmppserver.moRetryTimeOut=15
    
    
    #对于submit中destTerminalId为多个手机号的情况,是否拆分多条处理
    cmppserver.splitSubmitMsg=true
    
    #判断手机号合法性的类,必须实现com.aspire.nm.component.cmppserver.plugins.TerminalIdVerify接口,如果为空表示cmppserver不进行手机号校验
    terminalIdVerifyImplClassName=com.aspire.nm.component.cmppserverDemo.plugins.TerminalIdVerifyImpl
    
    #判断内容是否含有关键字的类,必须实现com.aspire.nm.component.cmppserver.plugins.KeyWordVerify接口,如果为空表示cmppserver不进行关键字校验
    keyWordVerifyImplClassName=com.aspire.nm.component.cmppserverDemo.plugins.KeyWordVerifyImpl
    
    #自定义下行输出的类,必须实现com.aspire.nm.component.cmppserver.plugins.ProcessSubmit接口,如果为空表示下行输出无处理
    processSubmitImplClassName=com.aspire.nm.component.cmppserverDemo.plugins.ProcessSubmitImpl
    
    #是否自动返回状态报告或上行
    autoDeliver=true


####2.3 增加全局黑名单####

	/**
	 * 增加全局黑名单
	 * @param blackIps
	 */
	public void addBlackIps(List  blackIps)



####2.4 新增接入/自定义上行输入####

	/** 
	 * @param clientConfig 接入用户的配置信息
	 */
	public CmppServer addClientConfig(ClientConfig clientConfig)



对ClientConfig 类的对象进行相关set可以配置接入的各种参数，如下

- setPass(String pass) ： 接入用户的登陆密码，cmpp协议中connectReq请求的密码

- setMaxConnNum(int maxConnNum) ： 接入用户的最大连接数，超过这个连接数后，新的连接将会登录失败

- setIp(String ip) ： 接入用户的IP地址，为空表示不限制IP

- setSrcId(String srcId) ： Cmpp协议中submitReq请求中的srcId,如果该接入用户使用的srcId并非已所配置的srcId为起始，则下行请求会返回相应的错误

- setDayMtLimit(int dayMtLimit) ： 接入用户每日允许下行的阀值，如果当日下行超过这个限制，则下行请求会返回相应的错误。0表示不设限制

- setMoLimitInSec(int moLimitInSec) ： 接入用户每秒允许上行的阀值，cmppserver会循环调用DeliverGetter接口中的getDeliver方法，如果返回速度超过moLimitInSec,则会适当延时。0表示不做限制

- setMtLimitInSec(int mtLimitInSec) ： 接入用户每个连接每秒允许下行的阀值，如果一秒内下行数量超过这个限制，则下行请求会返回相应的错误。0表示不设限制

- setServiceId(String serviceId) ： 接入用户下行时候允许的ServiceId

- setUserName(String userName) ： 接入用户名，即cmpp协议中connectReq请求的用户名

- setWhileDestTerminalId(List  whileDestTerminalId) ： 接入用户允许下行的手机号白名单，如果下行请求中手机号不在白名单中，则会返回相应的错误。Null表示没有白名单限制

- setBlackDestTerminalId(List  BlackDestTerminalId) ： 接入用不户允许下行手机号码的黑名单，如果下行请求中的手机号码在黑名单中，则会返回相应的错误。Null表示没有黑名单限制


####2.5 上行/状态报告发送####

    UserRunTime userRunTime = cmppServer.getUserRunTime(aspId);
    if(userRunTime != null){
        userRunTime.addMo(cmppDeliverPacket, true);
    }


####2.6 获取数据统计/监控数据等####

	 /**
	 * 获取CmppServer运行信息
	 * @return
	 */
	public String getRunTimeInfo()
	
	
	
###3. 功能点/状态码定义###	

####3.1 正常流程####

- 多链路正常登陆
- 下行普通中文短信
- 下行中文长短信 
- 心跳发送策略以及无心跳应答断链
- 上行/状态报告无应答自动重试
- 自动返回状态报告(for test)
- 自动返回上行(for test)

####3.2 登录异常/状态码####

- 错误spid登陆(非法源地址),登录应答2
- 错误密码登陆,登录应答3
- 错误ip登陆,登录应答1002
- 链接数限制,登录应答1001

####3.2 下行异常/状态码####

- srcid错误,下行应答10
- serviceid错误,下行应答7
- 超速(超过每秒限制),下行应答8
- 超量(超过每天限制),下行应答38
- 黑名单过滤,下行应答18
- 白名单过滤,下行应答17
- 打包发送的号码拆分成多个下行进行发送
- 敏感字过滤,下行应答15
- 手机号非法,下行应答13
- feetype长度不是2,下行应答1
- 内容字节流超长,下行应答6
- msglength值不大于0,下行应答4
- feecode不是数字,下行应答5
- 使用上行连接发送下行,下行应答14



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)