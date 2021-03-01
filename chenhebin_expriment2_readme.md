##   东莞理工学院网络空间安全学院   
####   实验报告模板   
  课程名称：企业级开发框架专题  &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;
  学期：2020春季    

`实验名称`：利用Spring boot的自动装配特性实现动态注册组件&emsp;&emsp;&emsp;&emsp;`实验序号`：二  
`姓名`：陈和斌&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;`学号`：201741404201&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;`班级`：17软卓1班  
`实验地址`：居家&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;`实验日期`：2020-4-7&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;`指导老师`：黎志雄  
`教师评语`：XXX&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;`实验成绩`：XXX&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;`百分制`：XXX  
`同组同学`：无  

  
#### 一、实验目标
1、 掌握Spring Boot的自动配置原理；
2、 掌握Spring框架动态注册Bean的原理；
3、 掌握自动生成元数据文件。
4、 掌握spring框架的事件模型。

  
#### 二、实验环境
1、 JDK 1.8或更高版本
2、 Maven 3.6+
3、 IntelliJ IDEA

  
#### 三、实验内容与实验步骤
##### 1、通过IntelliJ IDEA的Spring Initializr向导创建Spring Boot项目；  
#### `步骤`：
File->new Project->选择Spring Initializr->填写项目信息->选择所需的Spring COnfiguration Processor依赖,具体如下图：  

 
     
     
   

##### 2、创建一个自定义的CommandLineRunner接口的实现类;
#### `步骤`：   
新建一个CustomCommandLineRunner.class文件,代码具体如下:

```
public class CustomCommandLineRunner implements CommandLineRunner {
    Environment env;
    public CustomCommandLineRunner(Environment env) {
        this.env = env;
    }
    @Override
    public void run(String... args) throws Exception {
        System.out.println("利用Spring Boot 自动装配的CommandLineRunner");
//        生成一个32位随机子串
        System.out.println("生成一个随机字符串: ".concat(Objects.requireNonNull(env.getProperty("random."))));
    }
}
```
#### `说明`：   
该类的run方法会在项目运行的时候自动运行

##### 3、创建一个自定义的自动配置类。
#### `步骤`：   
新建一个Expriment2AutoConfig.class文件 ,代码具体如下:

```
public class Expriment2AutoConfig {
    @Bean
    CommandLineRunner createCustomCommandLineRunner(Environment env){
        return new CustomCommandLineRunner(env);
    }
}
```
#### `说明`：    
@Bean注解用于告诉方法，产生一个Bean对象，然后这个Bean对象交给Spring管理。产生这个Bean对象的方法Spring只会调用一次，随后这个Spring将会将这个Bean对象放在自己的IOC容器中。


##### 4、 创建spring.factories文件
#### `步骤`：   
1. 在resources目录下新建一个META-INF文件夹
2. 新建一个spring.factories文件 
3. 在spring.factories文件中输入代码如下:

```
org.springframework.boot.autoconfigure.EnableAutoConfiguration=edu.chb.expriment2.Expriment2AutoConfig

```
#### `说明`：    
edu.chb.expriment2.Expriment2AutoConfig是我自定义的自动配置类的全限定类路径的类名。   



##### 5、 给自动配置类添加有效条件。
#### `步骤`：   
1. 利用@ConditionalOnProperty注解，添加属性条件。
 
    
  
2. 在application.properties属性文件中添加一个自定义的属性。   

```
chb.auto.enable=true

```
#### `说明`：    
自动配置类是否生效取决于chb.auto.enable的值是否为true



##### 6、 自定义的一个Bean，绑定属性值，并生成spring配置类的元数据文件。
#### `步骤`：   
1. 创建一个类，并在类上加@ConfigurationProperties注解，设置注解的prefix属性指定绑定的属性的前缀。

 
    
  
2. 在某个配置类上添加@EnableConfigurationProperties，并指定装配的属性Bean。
 
    
  
3. 使用mvn package后会使用spring boot框架提供的注解处理器生成自定义属性的元数据文件。
 
    
      

#### `说明`：     
前面引入的spring-boot-configuration-processor依赖是spring boot框架提供的注解处理器



##### 7. 自定义一个事件发布器，并设置线程池，实现异步发布事件。
#### `步骤`：   
在自定义配置类Expriment2AutoConfig.class中添加如下代码：
```
 @Bean(AbstractApplicationContext.APPLICATION_EVENT_MULTICASTER_BEAN_NAME)
 ApplicationEventMulticaster customApplicationEventMulticaster(ThreadPoolTaskExecutor taskExecutor){
     SimpleApplicationEventMulticaster eventMulticaster = new SimpleApplicationEventMulticaster();
     eventMulticaster.setTaskExecutor(taskExecutor);
     return eventMulticaster;
 }
```
#### `说明`：    
 这个自定义的事件发布器的Bean的名称必须是“applicationEventMulticaster”, 使用了默认的线程池


##### 8、 自定义事件类。
#### `步骤`：   
在自定义配置类Expriment2AutoConfig.class中添加如下代码：
```
static class NoticeEvent extends ApplicationEvent{
    private static final Logger logger = LoggerFactory.getLogger(NoticeEvent.class);
    private final  String message;
    public NoticeEvent(String message) {
        super(message);
        this.message = message;
        logger.info("添加事件成功! message: {}",message);
    }
    public String getMessage() {
        return message;
    }
}
```


##### 9、 自定义事件监听器。
#### `步骤`：   
在自定义配置类Expriment2AutoConfig.class中添加如下代码：
```
@SuppressWarnings("unused")
@Component
static class NoticeListener implements ApplicationListener {
    private static final Logger logger = LoggerFactory.getLogger(NoticeListener.class);

    @Override
    public void onApplicationEvent(NoticeEvent noticeEvent) {
        logger.info("事件监听器获取到NoticeEvent, 睡眠当前线程 3 秒...");
        try{
            Thread.sleep(3000);
        }catch (InterruptedException e){
            e.printStackTrace();
        }
        logger.info("NoticeEvent的message属性是: {}", noticeEvent.getMessage());
    }
}
```
#### `说明`：     
监听上面自定义的事件,必须要加@Component,否则要报错.




##### 10、 编写一个测试用例，检查发布事件时，是否使用了多线程异步处理
#### `步骤`：   
在测试类Expriment2ApplicationTests.class中添加如下代码：
```
@SpringBootTest
class Expriment2ApplicationTests {
    @Autowired
    ApplicationEventMulticaster eventMulticaster;
    @Test
    void testAsyncEventMuticaster() throws InterruptedException{
        eventMulticaster.multicastEvent(new Expriment2AutoConfig.NoticeEvent("东莞理工学院"));
        eventMulticaster.multicastEvent(new Expriment2AutoConfig.NoticeEvent("网络空间安全学院"));
        Thread.sleep(2600); 
    }
}
```
#### `说明`：   
先注入自定义事件发布器, 然后依次在发布器中添加两个事件。




##### 附加题： 自定义一个线程池，然后给自定义的事件发布器使用。
#### `步骤`：   
1. 自定义一个线程池，在新增的类TaskPoolConfig.class中添加如下代码：
```
@Configuration
class TaskPoolConfig {
    @Bean("asyncTaskExecutor")
    public ThreadPoolTaskExecutor taskExecutor() {

        ThreadPoolTaskExecutor executor = new ThreadPoolTaskExecutor();
        executor.setCorePoolSize(10);
        executor.setMaxPoolSize(20);
        executor.setQueueCapacity(200);
        executor.setKeepAliveSeconds(60);
        executor.setThreadNamePrefix("taskExecutor-");
//        拒绝策略
        executor.setRejectedExecutionHandler(new ThreadPoolExecutor.CallerRunsPolicy());
        executor.initialize();
        return executor;
    }
}
```   

#### `说明`：     
@Bean注解用于告诉方法，产生一个Bean对象，然后这个Bean对象交给Spring管理。产生这个Bean对象的方法Spring只会调用一次，随后这个Spring将会将这个Bean对象放在自己的IOC容器中。这个名字在后面会用到。    

2. 在自定义发布器中替换默认的线程池，具体改动如下所示：
 
     
 



  
#### 四、实验结果
##### 1、自定义的CommandLineRunner接口的实现类和自动配置类测试结果:

 
     
    

#### `说明`：     
测试结果正确, 自定义的自动配置类已经生效。


##### 2、给自动配置类添加有效条件的测试结果：
1. 当chb.auto.enable=true时，运行结果如下：
 
     
    
2. 当chb.auto.enable=false时，运行结果如下：
 
     
     

#### `说明`：     
当有效条件属性值为true时，观察终端的显示，自动装配的配置类是生效;    
当有效条件属性值为false时，观察终端的显示，自动装配的配置类是不生效;    
  


##### 3、多线程事件发布测试结果：
1. 当chb.auto.enable=true时，运行结果如下：
 
     
    

#### `说明`：     
多线程事件发布成功 



##### 3、自定义多线程事件发布测试结果：
1. 当chb.auto.enable=true时，运行结果如下：
 
     
    

#### `说明`：     
自定义多线程事件发布成功


#### 五、实验总结
```
1.本次实验让我们逐步了解了springboot自动化配置原理。
2.注解功能很强大，也较容易遗漏。我在实验过程中曾试过因为遗漏了注解而报错。

```




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)