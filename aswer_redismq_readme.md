# redismq

框架开发宗旨：项目内的轻量级消息队列。
框架开发目的：在项目内部，我们常常需要做异步操作，常规的做法是提交给线程池去做，这样会导致一些：

* 线程池大小不可控，任务可能因为线程池满了被抛弃。
* 任务执行失败没有重试机制。
* 任务执行失败没有统一的异常处理。

为了解决如上问题，基于redis的队列开发了该消息队列，具有如下特点： 

* 足够轻量级，队列配置简单，只要使用redis即可，不需要额外部署环境；
* 支持分布式，任务提交后由多台机器分布式处理，机器资源分配合理；
* 处理效率高，任务交给多线程并发处理； 
* 处理有重试机制，并且可自定义错误处理。
* 对于小型数据入队列，出队列效率高。


引入依赖
```
 
	 com.ourhours.redismq 
	 redismq 
	 0.0.1 
 
```



## DEMO

## 使用指南
### SpringBoot引入

```
@Configuration
public class RedisMQConfig extends CachingConfigurerSupport {
	
	@Autowired
	Environment env;
	
	@Bean(name="messageTrunktaskExecutor")
	public ThreadPoolTaskExecutor getMessageTrunktaskExecutor() {
		ThreadPoolTaskExecutor threadPool = new ThreadPoolTaskExecutor();
		//线程池维护线程的最少数量
		threadPool.setCorePoolSize(100);
		//线程池维护线程所允许的空闲时间
		threadPool.setKeepAliveSeconds(30000);
		//线程池维护线程的最大数量
		threadPool.setMaxPoolSize(1000);
		//线程池所使用的缓冲队列
		threadPool.setQueueCapacity(1000);
		return threadPool;
	}

    @Bean
    public RedisUtil redisUtil() {
    		//redis config 配置
    		JedisPoolConfig config = new JedisPoolConfig();
    		
    		//控制一个pool最多有多少个状态为idle(空闲的)的JEDIS实例
    		try {
    			Integer maxIdle = Integer.parseInt(env.getProperty("spring.redis.pool.max-idle"));
    			config.setMaxIdle(maxIdle);
		} catch (Exception e) {}
    		
	    	//控制一个pool最少有多少个状态为idle(空闲的)的JEDIS实例
    		try {
    			Integer minIdle = Integer.parseInt(env.getProperty("spring.redis.pool.min-idle"));
    	    		config.setMinIdle(minIdle);
		} catch (Exception e) {}
    		//最大连接数，如果赋值为-1，则表示不限制；如果pool已经分配了maxActive个JEDIS实例，则此时pool的状态为exhausted(耗尽)。
    		try {
	    	    	Integer maxTotal = Integer.parseInt(env.getProperty("spring.redis.pool.max-active"));
	    	    	config.setMaxTotal(maxTotal);
		} catch (Exception e) {}
    		
    		Integer maxWait = -1;
    		try {
    			maxWait = Integer.parseInt(env.getProperty("spring.redis.pool.max-wait"));
    			config.setMaxWaitMillis(maxWait);
    		} catch (Exception e) {}
    		
    		Integer timeout = 0;
    		try {
    			timeout = Integer.parseInt(env.getProperty("spring.redis.timeout"));
    		} catch (Exception e) {}
	    
	    	//sentinel节点，如果为空则为单机模式
	    	String sentinelNodes = env.getProperty("spring.redis.sentinel.nodes");
	    	//密码
    		String password = env.getProperty("spring.redis.password");
    		
    		//连接池
    		Pool  pool = null;
    		
    		//单机模式
    		if(StringUtil.isEmpty(sentinelNodes)) {
    			String host = env.getProperty("spring.redis.host");
    			Integer port = Integer.parseInt(env.getProperty("spring.redis.port"));
    			
    			if(StringUtil.isEmpty(password)) {
    				pool = new JedisPool(config, host, port, timeout);
    			}else {
    				pool = new JedisPool(config,host,port,timeout,password);
    			}
    		}else {//sentinal模式
    			String masterName = env.getProperty("spring.redis.sentinel.master");
    			Set  sentinels = new HashSet ();  
    			sentinels.add(sentinelNodes);
    			if(StringUtil.isEmpty(password)) {
    				pool  = new JedisSentinelPool(masterName, sentinels, config, timeout);
    			}else {
    				pool  = new JedisSentinelPool(masterName, sentinels, config, timeout, password);
    			}
    		}
    		//构建redis util
    		RedisUtil redisUtil = new RedisUtil(pool);
        return redisUtil;
    }
    
}
```

### 1.消息入队列
获取消息队列全局对象MessageTrunk（可以用spring注入），put入消息即可。

```
        // 获取RedisMQMessageSender实例
        @Autowired
        RedisMQMessageSender messageSender;
		//发送消息
		String msg = "发送的消息";
        messageSender.put(new Message("QUEUE_NAME", msg));
```

### 2. 处理消息
消息处理器：继承AbstarctMessageHandler抽象类。

```
@Service
public class DemoHandler extends AbstarctMessageHandler
{
	private static Log logger = LogFactory.getLog(DemoHandler.class);

	public DemoHandler()
	{
		// 说明该handler监控的消息类型，第一个参数是队列名称，第二个为重试次数
		super("QUEUE_NAME", 10);
	}

	/**
	 * 监听到消息后处理方法
	 */
	@Override
	public void handle(String message)
	{
		System.out.println("正在处理消息：" + message);
	}

	@Override
	public void handleFailed(String obj)
	{
		StringBuilder sb = new StringBuilder();
		sb.append("msg:[").append(obj).append("], 超过失败次数，停止重试。");
		logger.warn(sb.toString());
	}

}
```

## 实现原理
基本原理是redis的阻塞取命令： Blpop，该命令移出并获取列表的第一个元素， 如果列表没有元素会阻塞列表直到等待超时或发现可弹出元素为止。





 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)