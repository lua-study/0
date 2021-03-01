##   综合实验 

院（系）名称：网络空间安全学院  
专业班级： 17软卓2班  
学号： 201741402120  
姓名： 许楷沂  
实验题目： 实验2  利用SpringBoot的自动装配特性实现动态注册组件  
实验日期：2020.4.07  
实验（上机）学时： 2  
成绩： 
- - - 
#### 一、实验目标
- 掌握Spring Boot的自动配置原理； 
- 掌握Spring框架动态注册Bean的原理； 
- 掌握自动生成元数据文件。 
- 掌握spring框架的事件模型。
- - -
#### 二、实验环境
- JDK 1.8或更高版本
- Maven 3.6+
- IntelliJ IDEA 

- - -
#### 三、实验任务
1. 通过IntelliJ IDEA的Spring Initializr向导创建Spring Boot项目
创建项目时，添加Spring Configuration Processor依赖。  
2. 创建一个自定义的CommandLineRunner接口的实现类。  
```java
@SuppressWarnings("unused")
public class CustomCommandLineRunner implements CommandLineRunner {
    Environment env;
    public CustomCommandLineRunner(Environment env){
        this.env=env;
    }
    @Override
    public void run(String...args){
        System.out.println("利用springboot自动装配的commandLineRunner");
        System.out.println("随机生成一个字符串：".concat(Objects.requireNonNull(env.getProperty("random."))));
    }
}

```
3. 创建一个自定义的自动配置类。  
```java
@EnableConfigurationProperties(CustomProperties.class)
public class Lab2AutoConfig {
    @Bean
    @ConditionalOnProperty(prefix = "cargo.auto",name="enable",havingValue = "true")
    CommandLineRunner createCustomCommandLineRunner(Environment env){
        return new CustomCommandLineRunner(env);
    }
}

```
4. 创建spring.factories文件;
 
     
 
运行：
 
     
 

5. 利用@ConditionalOnProperty注解，添加属性条件。  
 cargo.auto.enable=true 时，
  
      
  
 cargo.auto.enable=false 时，
  
       
   
   
6. 自定义的一个Bean，绑定属性值，并生成spring配置类的元数据文件，步骤如下：   
  - 创建一个类，并在类上加@ConfigurationProperties注解，设置注解的prefix属
  性指定绑定的属性的前缀。  
  ```java
@ConfigurationProperties(prefix = "cargo.auto")
public class CustomProperties {
    /*
    * 自动配置类是否生效
    */
    private boolean enable;
    public boolean isEable(){return enable;}
    public void setEnable(boolean enable){this.enable=enable;}
}

```
  - 在某个配置类上添加@EnableConfigurationProperties，并指定装配的属性Bean。
   
         
     

7. 自定义事件发布器：
```java

    /*
     * @Author cargo
     * @Description 自定义事件发布器
     * @Date:2020/04/10 14:41
     * */
    @Bean(AbstractApplicationContext.APPLICATION_EVENT_MULTICASTER_BEAN_NAME)
    ApplicationEventMulticaster applicationEventMulticaster(Executor taskExecutor){
        SimpleApplicationEventMulticaster simpleApplicationEventMulticaster= new SimpleApplicationEventMulticaster();
        simpleApplicationEventMulticaster.setTaskExecutor(taskExecutor);
        return simpleApplicationEventMulticaster;
    }
```

8. 自定义事件类：
```java
public class NoticeEvent extends ApplicationEvent {
//    private static final Logger logger= LoggerFactory.getLogger(NoticeEvent.class);
    private final String message;
    public NoticeEvent(String message) {
        super(message);
        this.message=message;
//        logger.info("添加事件成功！ message:{}",message);
    }
    public String getMessage(){return message;}
}

```
9. 自定义监听器：
```java
@Component
public class CustomNoticeListener implements ApplicationListener  {

    @Override
    public void onApplicationEvent(NoticeEvent noticeEvent) {
        System.out.println("获取CustomNoticeEvent，睡眠当前线程2秒");

        try {
            Thread.sleep(2000);
//            TimeUnit.SECONDS.sleep(2);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        System.out.println("CustomNoticeEvent 的 message 属性是:"+noticeEvent.getMessage());
    }
}

```
10. 编写测试用例，检查发布事件时，是否使用了多线程异步处理。
```java
@SpringBootTest
public class Lab2DemoApplicationTests {
    @Autowired
    ApplicationEventMulticaster eventMulticaster;
    @Test
    void testAsyncEventMulicaster() throws InterruptedException{
        eventMulticaster.multicastEvent(new NoticeEvent("东莞理工学院"));
        eventMulticaster.multicastEvent(new NoticeEvent("201741402120"));
        eventMulticaster.multicastEvent(new NoticeEvent("17软卓2"));
        eventMulticaster.multicastEvent(new NoticeEvent("许楷沂"));
    }
}

```
测试结果如下:
 
       
   
   

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)