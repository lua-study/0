# 一个异常通知的spring-boot-start框架 prometheus-spring-boot-starter

#### 前言的前言：


- 个人用异常通知请移步：[个人版分支](https://gitee.com/ITEater/prometheus-spring-boot-starter/tree/personal/)

- 多人协作开发需要异常通知请移步：[团队版分支](https://gitee.com/ITEater/prometheus-spring-boot-starter/tree/team/)



## 前言

首先，本人很懒（orz），虽然说日常写完项目代码后是都需要进行相关代码段的测试的，但事与愿违，有很多情况你可能会忘了测试，或者测试了感觉没问题实际上问题没暴露（主观测试很容易让测试结果按照你的想法输出），然后把代码merge，然后提交到测试服务器，然后就去睡大觉了，第二天醒来以后，发现程序运行各种bug，这时候你就开始把前一天的代码重新拉出来开始看……等等，我先收集一下bug吧，然后打开服务器，打开输出日志……天哪，由于是测试服务器，你可能会开很多的日志（比如：sql日志，格式化了还带参数；接口调用日志等等等等），有可能某个同事由于闲的蛋疼，特意对于某个出错的功能试了十几遍……面对成千上万行的日志，针对性的找出相应的异常实在是一件令人头疼的事。所以就需要每当工程出异常了，直接通知我不就好了嘛？

#### 系统需求

![jdk版本](https://img.shields.io/badge/java-1.8%2B-red.svg?style=for-the-badge&logo=appveyor)
![maven版本](https://img.shields.io/badge/maven-3.2.5%2B-red.svg?style=for-the-badge&logo=appveyor)
![spring boot](https://img.shields.io/badge/spring%20boot-2.0.0.RELEASE%2B-red.svg?style=for-the-badge&logo=appveyor)

#### 2019-08-27更新

1. 修改config的先后配置顺序，更加灵活的sendcomponent组件的配置

2. 修复``exceptionnotice.open-notice=false``时（关闭异常通知）的配置错误

3. 版本号变为**0.2.3-personal**


#### 2019-07-31更新

1. **集成了团队版所带的所有新特性（web-mvc模式、策略等）**

2. 版本号变为**0.2.2-personal**

3. 对说明文档进行详细的修改

#### 2019-04-25更新

1. 将spring的版本升级为最新版本（2.1.4），本工程的版本升级为0.2.1

2. 在``ExceptionNoticeProperty``配置中加入了新的注解``openNotice``(默认状态为false)，方便开启或关闭整个异常通知框架（感谢网友支持）

3. 关于工程名的问题：``exceptionnotice.project-name``建议添上，之前想过用``spring.application.name``做替代方案，之后再加


#### 2019-03-14更新

1. 对``ExceptionNoticeConfig``中aop的配置：``exceptionNoticeAop(ExceptionHandler exceptionHandler)``的一个条件中添加了``matchIfMissing = true``来保证默认情况下的aop对象的正常加载

```
        @Bean
	@ConditionalOnProperty(name = "exceptionnotice.enable-check-annotation", havingValue = "true", matchIfMissing = true)
	@ConditionalOnMissingBean(ExceptionNoticeAop.class)
	public ExceptionNoticeAop exceptionNoticeAop(ExceptionHandler exceptionHandler) {
		ExceptionNoticeAop aop = new ExceptionNoticeAop(exceptionHandler);
		return aop;
	}
```

#### 2019-01-14更新

1. 修改了一些bug（修改了aop处理注解的路径拼写问题linstener... orz），之前用注解报错的童鞋请重新拉取本工程，并重新再本地maven仓库打包……对于大家的困扰我很抱歉，最近由于很忙，也没顾上测试我就提交了……
2. 这个工程的issue已经开放，pr也是开放的，我欢迎大家多提问题，多做改善。



## 最快上手

1. 将此工程通过``mvn clean install``打包到本地仓库中。

2. 在你的工程中的``pom.xml``中做如下依赖

```
		 
			 com.kuding 
			 prometheus-spring-boot-starter 
			 0.2.3-personal 
		 
```

3. 在``application.properties``或者``application.yml``中做如下的配置：（至于以上的配置说明后面的章节会讲到）

```
spring:
  application:
    name: 普罗米修斯-demo
exceptionnotice:
  dinding:
    phone-num: 钉钉注册时的手机号
    web-hook: 设置的钉钉机器人的web-hook
  included-trace-package: 异常追踪的包路径
  notice-type: dingding
  listen-type: common
  open-notice: true
  exclude-exceptions:
  - java.lang.IllegalArgumentException

```

4. 至于钉钉的配置请移步：[钉钉机器人](https://open-doc.dingtalk.com/microapp/serverapi2/krgddi "自定义机器人")

5. 以上配置好以后就可以写demo测试啦，首先创建一个bean：

```
@Component
@ExceptionListener //异常通知的监控来自这个注解
public class NoticeComponents {

	public void someMethod(String name) {
		System.out.println("这是一个参数：" + name);
		throw new NullPointerException("第一个异常");
	}

	public void anotherMethod(String name, int age) {
		System.out.println("这又是一个参数" + age);
		throw new IllegalArgumentException(name + ":" + age);
	}
}

```

6. 以上都建立好了以后，就可以写单元测试了，首先上第一个测试：

```
@RunWith(SpringRunner.class)
@SpringBootTest
public class DemoApplicationTests {

	@Autowired
	private NoticeComponents noticeComponents;

	@Test
	public void contextLoads() {
		noticeComponents.someMethod("这是个参数");
	}
}
```

当运行单元测试后，假如钉钉配置没有问题的话，你的钉钉中就会出现如下类似的消息：

![效果](/src/main/resources/demo1.png)

你也可以做另一个测试``noticeComponents.anotherMethod("赵四" , 55);``，但是可以明确的告诉你没有任何结果通知这是因为配置了

```

exclude-exceptions:
  - java.lang.IllegalArgumentException
  
```

而且方法抛出的也恰恰是此异常：

```
public void anotherMethod(String name, int age) {
		System.out.println("这又是一个参数" + age);
		throw new IllegalArgumentException(name + ":" + age);
	}
```

所以自然不会有结果。

综上，一个简单的例子就完成了


## 咋做的

本框架遵循spring boot starter的自动化配置规范而开发的自动化异常通知框架，整体业务流程如下：
![架构](/src/main/resources/new.png)


### 配置

本框架配置主要分为4部分：
1. 全局配置
2. 通知配置
3. 策略配置
4. 外援配置

#### 全局配置

- 全局配置主要包含在``ExceptionNoticeProperty``类下，最根本的配置便是是否开启异常通知配置``exceptionnotice.open-notice``，在开发环境，由于测试与调试都是实时反馈，有bug就即时的改掉了，并不需要进行异常通知的配置，但是在线上测试或者是生产环境还是需要进行开启的

- 每次抛出的异常的时候，异常的追踪信息非常的长，``exceptionnotice.included-trace-package``就是为了解决这个问题而存在的，一般情况下，此配置项就是配置你工程的包路径就可以了，当你的工程中出现异常时，``exceptionnotice.included-trace-package``就会把包含此包路径的追踪信息给过滤出来，并且去掉代理产生的追踪信息，这样就一目了然的知道是哪里出错了。


- 每一个工程都会有工程名，毕竟我需要知道是哪个工程出错了，配置工程名的就是``exceptionnotice.project-name``，假如工程名没有配置，框架就会优先去找``spring.application.name``，假如这个也没配置，那么这个工程我也不知道叫啥了，所以其名曰：无名工程

- 框架配置里面 **最重要的配置是** ：``exceptionnotice.listen-type``表示的是此工程的监听方式，目前有两种监听方式：**普通监听（common）** ；**mvc监听（web-mvc）** 。这两种监听方式各有千秋，普通监听方式主要运用aop的方式对有注解的方法或类进行监听，可以加在任何类与方法上。但是mvc监听只能对controller层进行监听，对其它层无效，不过异常通知的信息更丰富，不仅仅包括了普通监听的所有信息（不包含参数），还包含了请求中的参数信息（param）、请求中的请求体信息（body）和请求体中的头信息（header）：

![请求异常通知](/src/main/resources/demo2.png)

- 配合``exceptionnotice.listen-type=web-mvc``，可以对请求头进行筛选，默认情况下会把所有的请求头返回

```
exceptionnotice.include-header-name=headerName1,headerName2

```

- 项目中的异常一般分类两大类：第一类为未捕获异常，第二类为业务异常。业务异常一般由用户自己定义的异常，在javaweb项目中，假如用户的请求不满足返回结果的条件，一般是需要主动抛出自定义异常的，所以这类异常并不需要进行通知。排除不需要异常通知的配置如下：

```
 exceptionnotice.exclude-exceptions=java.lang.IllegalArgumentException,com.yourpackage.SomeException
```

- 为了方便进行扩展开发，本框架还支持异常信息的持久化，目前只支持进行redis的持久化，开启redis持久化需要进行如下配置

```
exceptionnotice.enable-redis-storage=true
exceptionnotice.redis-key=你自己的redis键
```

存储redis的结构为redis的HASH接口，HASH的键是异常通知信息中的算出的一个唯一id，HASH的值是对应的异常信息，唯一id的算法也很简单：

```
private String calUid() {
		String md5 = DigestUtils.md5DigestAsHex(
				String.format("%s-%s", exceptionMessage, traceInfo.size() > 0 ? traceInfo.get(0) : "").getBytes());
		return md5;
	}
```

**这里开启redis存储需要依赖spring-boot-starter-data-redis，需要用户自行配置**

#### 通知配置

- 目前框架提供的异常通知配置有两种：**钉钉配置**与**邮件配置**，除了以上两种以外，用户可根据自身情况来进行自定义的通知配置，只需要继承``INoticeSendComponent``接口并交由IOC容器进行管理即可；对于配置何种通知是通过	``application.properties``中``exceptionnotice.notice-type``来进行选择。

- 选择**钉钉**通知需要配置``exceptionnotice.notice-type=dingding``，同时需要配置钉钉的相关信息：

```
exceptionnotice:
  dinding:
    phone-num: 钉钉注册时的手机号
    web-hook: 设置的钉钉机器人的web-hook
```

- 选择**邮件**通知需要配置``exceptionnotice.notice-type=email``，同时需要配置邮件相关信息：

```
exceptionnotice:
  email:
    to: 给谁发
    cc: 抄送谁
    bcc: 秘密抄送谁
    
```

邮件通知是建立在spring的邮件配置之上的，所以除了以上配置以外，还需要spring的email相关配置信息：

```

spring:
  mail:
    host: smtp.xxx.com
    port: 25
    username: 开启smtp权限的邮箱用户名
    password: 密码

```

#### 策略配置

一般而言，一个方法出现异常信息，意味着每当同样的方式进行调用时都会抛出相同的异常方法，放任不管的话，钉钉异常通知与邮件异常通知会重复的收到同一个异常，所以为了限制发送频率，默认情况下，某个方法出现的异常需要通知，那么这条通知**每天只会出现一次**。当然这样也可能会出现问题，假如邮件或钉钉信息没有收到，很可能会漏掉此通知，所以这里创造了一个通知的策略。

- 通知策略对应的配置类为``ExceptionNoticeFrequencyStrategy``，开启策略需要在``application.properties``中加入如下配置

```
exceptionnotice.strategy.enabled=true
```

- 目前一共有两种通知策略
    - 时间策略
    - 出现频次策略
对应的配置为：

```
exceptionnotice.strategy.frequency-type=timeout/showcount
```

- 时间策略对应的配置项为``exceptionnotice.strategy.notice-time-interval``，类型为duration，表示的是自上次通知时间起，超过了此配置的时间后，便会再次通知。
- 频次策略对应的配置项为``exceptionnotice.strategy.notice-show-count``，表示的是自上次通知起，出现次数超过了此配置测次数后，便会再次通知

基本上以上策略足够使用，假如说还有更好的配置策略可以连系我

#### 外援配置

目前需要外援配置的信息有以下几个，其实上面也提到了

1. 开启redis存储的话需要在``pom.xml``中加入如下依赖

```
		 
			 org.springframework.boot 
			 spring-boot-starter-data-redis 
		 
```

加入依赖后需要开始配置redis

```
spring:
  redis:
    host: 127.0.0.1
    port: 6379
    database: 0
    password: 密码
```

2. 有邮件通知的话需要在``pom.xml``中加入如下依赖

```
		 
			 org.springframework.boot 
			 spring-boot-starter-mail 
		 
```

加入依赖后开始配置邮件信息

```
spring:
  mail:
    host: smtp.xxx.com
    port: 25
    username: 开启smtp权限的邮箱用户名
    password: 密码
```

3. 开启web-mvc模式的话，不说也知道，一定会引入如下依赖：

```
		 
			 org.springframework.boot 
			 spring-boot-starter-web 
		 
```


### 注解

- 上面讲的配置实际上是为此注解服务的，框架内唯一的注解``@ExceptionListener``，需要注意的是，凡是你需要异常通知的类或方法上必须加此注解。

- 根据配置类型``exceptionnotice.listen-type``的不同配置注解的位置也是不一样的
    - ``exceptionnotice.listen-type=common``时``@ExceptionListener``可以加到任意类上，任意方法上
    - ``exceptionnotice.listen-type=web-mvc``时，``@ExceptionListener``只能加在Controller层即带有``@Controller``或``@RestController``的类或者方法上，方法上也需要有对应的``@RequestMapping``相关的注解

[![Fork me on Gitee](https://gitee.com/ITEater/prometheus-spring-boot-starter/widgets/widget_3.svg?color=18181a)](https://gitee.com/ITEater/prometheus-spring-boot-starter)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)