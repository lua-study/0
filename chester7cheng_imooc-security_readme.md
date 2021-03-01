###Spring Security过滤器链
![Spring Security基本原理](images/Spring Security基本原理.JPG)



###Spring Security认证流程
![](images/Spring Security认证流程.JPG)


###Spring Security记住我原理
![](images/Spring Security记住我流程.JPG)

记住我过滤器的位置
![](images/完整过滤器流程.JPG)

###自定义验证码接口重构流程
![](images/自定义验证码接口流程图.JPG)


###自定义的短信验证码过滤器流程
![](images/自定义短信验证码接口流程.JPG)
单独自定义短信验证码过滤器是为了其他模块可以重用而不仅仅是登录的时候才能用


###Spring Security配置重构图
![](images/Spring Security配置重构.JPG)


###OAuth2协议授权码模式原理
![](images/OAuth协议授权码模式原理.JPG)


###使用Spring Social完成社交登录
![](images/Spring Social原理.JPG)

![](images/Spring Social过滤器位置.JPG)

###Spring Social简述图
![](images/Spring Social简述图.JPG)

###Spring Social运行流程(橘色部分为自定义组件)
![](images/Spring Social流程.JPG)

####SocialAuthenticationFilter调用attemptAuthService()方法调用OAuth2AuthenticationService的getAuthToken方法
#####OAuth2AuthenticationService
```java
public SocialAuthenticationToken getAuthToken(HttpServletRequest request, HttpServletResponse response) throws SocialAuthenticationRedirectException {
		String code = request.getParameter("code");
		if (!StringUtils.hasText(code)) {//参数中没有code
			OAuth2Parameters params =  new OAuth2Parameters();
			params.setRedirectUri(buildReturnToUrl(request));
			setScope(request, params);
			params.add("state", generateState(connectionFactory, request));
			addCustomParameters(params);
			//没有传入code,抛出重定向异常重定向到QQ的授权网址上去
			throw new SocialAuthenticationRedirectException(getConnectionFactory().getOAuthOperations().buildAuthenticateUrl(params));
		} else if (StringUtils.hasText(code)) {//请求参数中有code
			try {
				String returnToUrl = buildReturnToUrl(request);
				//拿到ConnectionFactory(QQConnectionFactory)和OAuthOperations(QQOAthTemplate)去换取令牌(accessToken)
				AccessGrant accessGrant = getConnectionFactory().getOAuthOperations().exchangeForAccess(code, returnToUrl, null);
				// TODO avoid API call if possible (auth using token would be fine)
				Connection  connection = getConnectionFactory().createConnection(accessGrant);
				return new SocialAuthenticationToken(connection, null);
			} catch (RestClientException e) {
				logger.debug("failed to exchange for access", e);
				return null;
			}
		} else {
			return null;
		}
	}
```
第一次访问时没有code参数会跳转到授权页面,若携带code参数则会进行申请令牌操作，AccessGrant其实就是封装了accessToken的实体类


####OAuth2AuthenticationService调用的QQConnectionFactory是如何注入进去的
ConnectionFactory在QQAutoConfiguration中进行配置，其父类SocialAutoConfigurerAdapter会调用addConnectionFactories方法
把ConnectionFactory放入到ConnectionFactoryLocator(ConnectionFactoryRegistry)中的Map集合connectionFactories中
以下是代码
#####QQAutoConfiguration(自定义)
```java
public class QQAutoConfiguration extends SocialAutoConfigurerAdapter {
    
    ...
    
    /**
    	 * 创建QQConnectionFactory
    	 * 父类的addConnectionFactories方法会将QQConnectionFactory加入到ConnectionFactoryConfigurer中
    	 * @return
    	 */
    	@Override
    	protected ConnectionFactory  createConnectionFactory() {
    		QQProperties qqConfig = securityProperties.getSocial().getQq();
    		return new QQConnectionFactory(qqConfig.getProviderId(), qqConfig.getAppId(), qqConfig.getAppSecret());
    	}
}

```


看下父类SocialAutoConfigurerAdapter
#####SocialAutoConfigurerAdapter
```java
    @Override
	public void addConnectionFactories(ConnectionFactoryConfigurer configurer,
			Environment environment) {
        //这里的configurer其实就是SecurityEnabledConnectionFactoryConfigurer
		configurer.addConnectionFactory(createConnectionFactory());
	}

	protected abstract ConnectionFactory  createConnectionFactory();
```

看看SecurityEnabledConnectionFactoryConfigurer是如何将ConnectionFactory注入给OAuthenticationService的
#####SecurityEnabledConnectionFactoryConfigurer
```java
    private SocialAuthenticationServiceRegistry registry;
	...
	public void addConnectionFactory(ConnectionFactory  connectionFactory) {
	    //将SocialAuthenticationService加入到SocialAuthenticationServiceRegistry中的authenticationServices集合中
		registry.addAuthenticationService(wrapAsSocialAuthenticationService(connectionFactory));
	}
	...
	private   SocialAuthenticationService  wrapAsSocialAuthenticationService(ConnectionFactory  cf) {
		if (cf instanceof OAuth1ConnectionFactory) {
			return new OAuth1AuthenticationService ((OAuth1ConnectionFactory ) cf);
		} else if (cf instanceof OAuth2ConnectionFactory) {
		    
		    //这里就是真正的把QQConnectionFactory注入到OAuth2AuthenticationService中
			final OAuth2AuthenticationService  authService = new OAuth2AuthenticationService ((OAuth2ConnectionFactory ) cf);
			authService.setDefaultScope(((OAuth2ConnectionFactory ) cf).getScope());
			return authService;
		}
		throw new IllegalArgumentException("The connection factory must be one of OAuth1ConnectionFactory or OAuth2ConnectionFactory");
	}
```
这里SecurityEnabledConnectionFactoryConfigurer主要完成了2件事:
1.初始化了OAuth2AuthenticationService，把ConnectionFactory注入到了其中
2.把OAuth2AuthenticationService注入到SocialAuthenticationServiceRegistry的Map集合authenticationServices中


####而SocialAuthenticationFilter又是如何拿到带有authenticationServices集合的SocialAuthenticationServiceRegistry呢
```java
public class SpringSocialConfigurer extends SecurityConfigurerAdapter  {
    
    ...
    
    @Override
    	public void configure(HttpSecurity http) throws Exception {		
    		ApplicationContext applicationContext = http.getSharedObject(ApplicationContext.class);
    		UsersConnectionRepository usersConnectionRepository = getDependency(applicationContext, UsersConnectionRepository.class);
    		//从容器中获取SocialAuthenticationServiceLocator(SocialAuthenticationServiceRegistry)
    		**SocialAuthenticationServiceLocator authServiceLocator = getDependency(applicationContext, SocialAuthenticationServiceLocator.class);**
    		SocialUserDetailsService socialUsersDetailsService = getDependency(applicationContext, SocialUserDetailsService.class);
    		
    		//将从容器中获取的SocialAuthenticationServiceLocator传入SocialAuthenticationFilter构造函数
    		SocialAuthenticationFilter filter = new SocialAuthenticationFilter(
    				http.getSharedObject(AuthenticationManager.class), 
    				userIdSource != null ? userIdSource : new AuthenticationNameUserIdSource(), 
    				usersConnectionRepository, 
    				authServiceLocator);
    		
    		...
    		
    		//注册SocialAuthenticationFilter
    		http.authenticationProvider(
            				new SocialAuthenticationProvider(usersConnectionRepository, socialUsersDetailsService))
            			.addFilterBefore(postProcess(filter), AbstractPreAuthenticatedProcessingFilter.class);
}
```
可以看到SocialAuthenticationFilter中的SocialAuthenticationServiceRegistry是在容器中获取的，那SocialAuthenticationServiceRegistry又是在哪里注册的呢
打开org.springframework.social.config.annotation包下的SocialConfiguration类可以看到
#####SocialConfiguration
```java
@Configuration
public class SocialConfiguration {
    ...
    @Bean
    	public ConnectionFactoryLocator connectionFactoryLocator() {
    		if (securityEnabled) {
    			SecurityEnabledConnectionFactoryConfigurer cfConfig = new SecurityEnabledConnectionFactoryConfigurer();
    			for (SocialConfigurer socialConfigurer : socialConfigurers) {
    				socialConfigurer.addConnectionFactories(cfConfig, environment);
    			}
    			return cfConfig.getConnectionFactoryLocator();
    		} else {
    			DefaultConnectionFactoryConfigurer cfConfig = new DefaultConnectionFactoryConfigurer();
    			for (SocialConfigurer socialConfigurer : socialConfigurers) {
    				socialConfigurer.addConnectionFactories(cfConfig, environment);
    			}
    			return cfConfig.getConnectionFactoryLocator();
    		}
    	}
}
```
ConnectionFactoryLocator其实就是SocialAuthenticationServiceLocator的父接口

####ProviderSignInUtils工具类
Social中的一个工具类，用户登录以后可以通过次类获取用户信息

###绑定与解绑
org.springframework.social.connect.web.ConnectController默认实现了获取用户绑定信息的控制器
```java
@Controller
@RequestMapping("/connect")
public class ConnectController implements InitializingBean {
    //...
    
    @RequestMapping(method=RequestMethod.GET)
    	public String connectionStatus(NativeWebRequest request, Model model) {
    		setNoCache(request);
    		processFlash(request, model);
    		Map >> connections = connectionRepository.findAllConnections();
    		model.addAttribute("providerIds", connectionFactoryLocator.registeredProviderIds());		
    		model.addAttribute("connectionMap", connections);
    		//返回connect/status的视图
    		return connectView();
    	}
}
```
这个控制器默认返回当前用户绑定信息，自己定义一个connect/status的视图

```java
/**
 * 接收绑定信息的视图
 */
@Component("connect/status")
public class ImoocConnectionStatusView extends AbstractView {
	
	@Autowired
	private ObjectMapper objectMapper;

	@SuppressWarnings("unchecked")
	@Override
	protected void renderMergedOutputModel(Map  model, HttpServletRequest request,
			HttpServletResponse response) throws Exception {
		
		Map >> connections = (Map >>) model.get("connectionMap");
		
		Map  result = new HashMap<>();
		for (String key : connections.keySet()) {
			result.put(key, CollectionUtils.isNotEmpty(connections.get(key)));
		}
		
		response.setContentType("application/json;charset=UTF-8");
		response.getWriter().write(objectMapper.writeValueAsString(result));
	}
}
```
绑定
```java
@Controller
@RequestMapping("/connect")
public class ConnectController implements InitializingBean {
   
    //...
   
    @RequestMapping(value="/{providerId}", method=RequestMethod.GET)
    	public String connectionStatus(@PathVariable String providerId, NativeWebRequest request, Model model) {
    		setNoCache(request);
    		processFlash(request, model);
    		List > connections = connectionRepository.findConnections(providerId);
    		setNoCache(request);
    		if (connections.isEmpty()) {
    			return connectView(providerId); 
    		} else {
    			model.addAttribute("connections", connections);
    			return connectedView(providerId);			
    		}
    	}
    	
    	//...
}
```
Spring Social默认实现了connect/{providerId}的控制,返回connect/{providerId}Connected的视图

###Session管理

可在配置文件中配置如下设置超时时间，少于60s按60s算
server.session.timeout = 600

![](images/集群session管理.JPG)

在配置文件中配置session的类型，推荐Redis
spring.session.store-type = none

#Spring Security OAuth2
![](images/Spring Security OAuth2.JPG)

![](images/Spring Security自定义认证、资源服务器.JPG)

###Spring Security OAuth2原理
![](images/Spring Security OAuth2原理.JPG)
蓝色部分为接口以及实现类

###重构Spring Security OAuth2
![](images/重构Spring Securty OAuth2.JPG)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)