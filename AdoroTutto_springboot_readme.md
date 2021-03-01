# SpringBoot

## 一、SpringBoot简介

### 1. SpringBoot是什么？

​	产生背景：Spring开发变的越来越笨重，大量的XML文件，繁琐的配置，复杂的部署流程，整合第三方技术时难度大等，导致开发效率低下

​	SpringBoot是一个用来简化Spring应用的初始化创建和开发的框架，简化配置，实现快速开发

### 2. 为什么使用SpringBoot

​	优点：

- 快速创建独立运行的Spring应用并与主流框架集成
- 内置Servlet容器，应用无需打包war包
- 使用starter（启动器）管理依赖并进行版本控制
- 大量的自动配置，简化开发
- 提供了准生产环境的运行时监控，如指标、 健康检查、外部配置等
- 无需配置XML，没有生成冗余代码，开箱即用

## 二、第一个SpringBoot应用

### 1. 简介

​	推荐环境：

- SpringBoot 2.0（基于Spring5.0）
- JDK 1.8及以上
- Maven 3.2及以上
- Tomcat 8.5及以上

### 2. 步骤

​	步骤：

1. 创建一个maven的java工程

   传统Web应用需要创建一个web工程，后期要打成war包，然后放到tomcat中

   springboot应用只需要创建一个java工程，后期直接打成jar包，其内置tomcat

2. 导入SpringBoot相关依赖

   ```xml
    
    
      org.springframework.boot 
      spring-boot-starter-parent 
      2.0.3.RELEASE 
    

    
    
      
        org.springframework.boot 
        spring-boot-starter-web 
      
    
   ```

3. 编写Controller

4. 编写主程序类

   ````java
   @SpringBootApplication
   public class MainApplication {
       public static void main(String[] args) {
           //启动SpringBoot应用
           SpringApplication.run(MainApplication.class, args); //传入主程序类的Class对象
       }
   }
   ````

   https://192.168.5.8/svn/wbs18031/

5. 部署打包

   添加spring-boot-maven-plugin

   ```xml
    
    
      
        
          org.springframework.boot 
          spring-boot-maven-plugin 
        
      
    
   ```

### 3. 分析HelloWorld

#### 3.1 POM文件

- 父项目是spring-boot-starter-parent

  ```xml
   
     org.springframework.boot 
     spring-boot-starter-parent 
     2.0.3.RELEASE 
   
  ```

  父项目的父项目是spring-boot-dependencies，用来管理SpringBoot应用中依赖的版本

  ```xml
   
     org.springframework.boot 
     spring-boot-dependencies 
     2.0.3.RELEASE 
     ../../spring-boot-dependencies 
   
  ```

- 通过启动器starter添加依赖

  ```xml
   
     
       org.springframework.boot 
       spring-boot-starter-web 
     
   
  ```

  SpringBoot提供了许多Starter（启动器），分别对应不同中的应用场景，只要在项目中引入这些starter，相应场景的依赖就会被导入

#### 3.2 主程序类

- @SpringBootApplication

  标注在类上，表示这个类是一个SpringBoot应用

  @SpringBootConfiguration标注在类上，表示这个SpringBoot的配置类，相当于xml配置文件

  @Configuration标注在类上，表示这个类是Spring的配置类

- @EnableAutoConfiguration

  **开启自动配置功能**，SpringBoot会自动完成许多配置，简化了以前的繁琐的配置

- @ComponentScan

  标注在类上，指定要扫描的包，默认只扫描主程序类所在的包及其子包

## 三、快速创建SpringBoot项目

### 1. 简介

​	使用向导快速创建SpringBoot项目

### 2. 基本操作

- 默认生成的.mvn、.gitignore等可以删除

- POM文件和主程序类都已经生成好了，直接写业务逻辑即可

- resources文件夹的目录结构

  ```java
  |-resources
    	|-static  存放静态资源，如css js images
    	|-templates  存放模板页，可以使用模板引擎，如freemarker、velocity、theamleaf等
    	|-application.properties  SpringBoot应用的配置文件
  ```

## 四、配置文件

### 1. 简介

​	SpringBoot的配置文件默认有两个：

- application.properties
- application.yml

​       文件名固定，放在classpath:/或classpath:/config目录下

​	

### 2. YAML用法

#### 2.1 简介

​	YAML不是一种标记语言

​	YAML是专门用来写配置文件的语言，比xml、properties更适合作为配置文件

​	YAML文件的后缀是.yml或.yaml

#### 2.2 语法规则

- 大小写敏感
- 使用缩进表示层级关系
- 缩进时不允许使用Tag键，只允许使用空格
- 缩进的空格数目不重要，只要相同层级的元素左侧对齐即可
- `#`表示注释

```yaml
# 修改默认配置
server:
  port: 8882 # 写法key: value，冒号后面必须有空格
  servlet:
    context-path: /springboot03
```

#### 2.3 基本用法

​	YAML支持的数据结构有三种：

- 字面量：单个值
- 对象：键值对
- 数组：一组数据的集合

​      三种数据结构的用法：

1. 字面量：普通的值，字符串、数字、布尔等

   ```yaml
   number: 25
   str: 'hello world'
   flag: true
   ```

2. 对象，也称为Map映射，包含属性和值

   ```yaml
   # 写法1：换行写，使用缩进
   user: 
   	name: tom
   	age: 21
   # 写法2：行内写法
   user: {name: tom,age: 21}
   ```

3. 数组，如List、Set等

   ```yaml
   # 写法1：换行写，使用短横线
   names:
   	- tom
   	- jack
   	- alice
   # 写法2：行内写法
   names: [tom,jack,alice]
   ```

### 3. 为属性注入值

​	通过加载配置文件，为类中的属性注入值

#### 3.1 使用.yml配置文件

```xml
user:
  username: admin
  age: 18
  status: true
  birthday: 2018/2/14
  address:
    province: 江苏省
    city: 南京市
  lists:
    - list1
    - list2
    - list3
  maps: {k1: v1,k2: v2}
```

```java
// 将当前Bean添加到容器中
@Component
// 默认读取全局配置文件获取值，将当前类中的属性与配置文件中的user进行绑定
@ConfigurationProperties(prefix = "user")
public class User implements Serializable {

    private String username;
    private Integer age;
    private Boolean status;
```

#### 3.2 使用.properties文件

```properties
user.username=tom
user.age=21
user.status=false
user.birthday=2017/7/12
user.address.province=山东省
user.address.city=威海市
user.lists=list1,list2,list2
user.maps.k1=v1
user.maps.k2=v2
```

#### 3.3 使用@Value为属性注入值

```java
// 将当前Bean添加到容器中
@Component
// 默认读取全局配置文件获取值，将当前类中的属性与配置文件中的user进行绑定
// @ConfigurationProperties(prefix = "user")
public class User implements Serializable {

    @Value("${user.username}")
    private String username;
    @Value("${user.age}")
    private Integer age;
    @Value("${user.status}")
    private Boolean status;
    @Value("${user.birthday}")
    private Date birthday;
    //@Value不支持复杂类型封装
    private Address address;
    @Value("${user.lists}")
    private List  lists;
```

@Value和@ConfigurationProperties的比较：

- @Value只能一个个为属性注入值，而@ConfigurationProperties可以指为属性注入值
- @Value不支持复杂类型封装，而@ConfigurationProperties可以

### 4. 多环境配置

​	可以为不同环境提供不同中的配置信息，如开发环境、测试环境、生产环境

​	两种方式：

- 创建多个properties文件
- 定义yml文档块

#### 4.1 创建多个properties文件

​	步骤：

1. 创建不同环境的properties文件

   文件命名要必须application-xxx.properties

2. 在application.properties文件中指定要激活的配置

   ```properties
   # 指定激活的配置
   spring.profiles.active=prod
   ```

#### 4.2 定义yml文档块

​	步骤：

1. 定义yml文档块

   ```yaml
   ---

   spring:
     profiles: develop
   server:
     port: 7771

   ---

   spring:
     profiles: testing
   server:
     port: 7772

   ---

   spring:
      profiles: product
   server:
     port: 80

   ```

2. 在第一个文档块中指定要激活的配置

   ```yaml
   # 指定要激活的配置
   spring:
     profiles:
       active: testing
   ```

### 5. 加载外部的配置文件

#### 5.1 加载properties属性文件

​	使用@PropertySource加载外部的属性文件

```java
// 将当前Bean添加到容器中
@Component
// 加载外部的属性文件
@PropertySource({"classpath:user.properties"})
// 默认读取全局配置文件获取值，将当前类中的属性与配置文件中的user进行绑定
@ConfigurationProperties(prefix = "user")
public class User implements Serializable {
```

#### 5.2 加载spring配置文件

​	使用@ImportResoruce加载外部的Spring的XML文件

```java
// 加载外部的spring配置文件
@ImportResource({"classpath:spring.xml"})
@SpringBootApplication
public class Springboot03ConfigApplication {
```

#### 5.3 使用注解方式添加组件

​	使用@Configuration和@Bean

```java
// 标注在类上，表示这是一个配置文件，相当于以前的spring配置文件
@Configuration
public class SpringConfig {

    // 标注在方法上，向容器中添加组件，将方法的返回值添加到到容器中，将方法名作为组件id
    @Bean
    public Address address(){
        Address address = new Address();
        address.setProvince("江苏");
        address.setCity("苏州");
        return address;
    }

}
```

## 五、自动配置的原理

### 1. 执行过程

1. SpringBoot应用启动时会加载主程序类，开启了自动配置功能@EnableAutoConfiguration

2. @EnableAutoConfiguration作用

   扫描所有jar包类路径下的META-INF/spring.factories文件，获取到EnableAutoConfiguration对应的值，将这些**自动配置类**添加容器中

3. 通过这些自动配置类完成相应的配置功能

### 2. 原理分析

​	以HttpEncodingAutoConfiguration为例：

```java
// 表示这是一个Spring配置类
@Configuration
// 启用HttpEncodingProperties类的ConfigurationProperties功能，通过配置文件为其属性注入值，并将其添加到容器中
@EnableConfigurationProperties({HttpEncodingProperties.class})
// 如果当前应用是Web应用，则该配置类生效，否则不生效
@ConditionalOnWebApplication(
    type = Type.SERVLET
)
// 如果当前应用中有CharacterEncodingFilter类，则该配置类生效，否则不生效
@ConditionalOnClass({CharacterEncodingFilter.class})
// 如果配置文件中有spring.http.encoding.enabled选项，则该配置项生效，否则不生效，默认已经设置为True，所以默认生效
@ConditionalOnProperty(
    prefix = "spring.http.encoding",
    value = {"enabled"},
    matchIfMissing = true
)
public class HttpEncodingAutoConfiguration {
    private final HttpEncodingProperties properties;
	
  	// 将容器中HttpEncodingProperties注入
    public HttpEncodingAutoConfiguration(HttpEncodingProperties properties) {
        this.properties = properties;
    }
	
  	// 将方法返回值添加到容器中
    @Bean
  	// 如果容器中没有这个组件，则添加
    @ConditionalOnMissingBean
    public CharacterEncodingFilter characterEncodingFilter() {
        CharacterEncodingFilter filter = new OrderedCharacterEncodingFilter();
        filter.setEncoding(this.properties.getCharset().name());
        filter.setForceRequestEncoding(this.properties.shouldForce(org.springframework.boot.autoconfigure.http.HttpEncodingProperties.Type.REQUEST));
        filter.setForceResponseEncoding(this.properties.shouldForce(org.springframework.boot.autoconfigure.http.HttpEncodingProperties.Type.RESPONSE));
        return filter;
    }
```



```properties
spring.http.encoding.charset=gbk
spring.http.encoding.force=true
```



​	总结：

- SpringBoot启动时会加载大量的自动配置类（**xxxAutoConfiguration**） xxxProperties
- 通过这些自动配置类向容器中添加组件
- 通过这些组件来实现自动配置功能，简化



## 六、Web开发

### 1. 简介

​	步骤：

1. 创建SpringBoot应用，选择相应的Starter
2. 在配置文件中指定必要的少量配置
3. 编写业务代码

​     Web开发的自动配置类：WebMvcAutoConfiguration

### 2. 静态资源的映射

#### 2.1 静态资源位置

​	查看WebMvcAutoConfiguration——>getStaticLocations()

​	静态资源的默认位置：

- "classpath:/META-INF/resources/"
- "classpath:/resources/"
- "classpath:/static/"
- "classpath:/public/"

​     修改默认的静态资源的位置：

```properties
# 指定静态资源的位置
spring.resources.static-locations=classpath:/static,classpath:/public
```

#### 2.2 欢迎页

​	将index.html页面放到任意一个静态资源文件夹中即可

#### 2.3 图标

​	将favicon.ico放到任意一个静态资源文件夹中即可

## 七、模板引擎

### 1. 简介

​	目前Java  Web开发推荐使用模板引擎，不建议使用JSP页面

- JSP缺点：本质上就是Servlet，需要后台编译，耗时，效率低
- 模板引擎：不需要编译，速度快

​        常见的模板引擎：Freemarker、Velocity、Thymeleaf等

​	SpringBoot推荐使用Thymeleaf，且默认不支持JSP，因为JSP必须要打包war包才行

​	补充：目前主流Web开发更推荐采**用前后端分离**的形式，前端使用MVVM框架：Vue.js、Angular、React等

### 2. 使用步骤

​	步骤：

1. 添加Thymeleaf的依赖

   ```xml
    
      org.springframework.boot 
      spring-boot-starter-thymeleaf 
    
   ```

2. 将HTML页面放到templates目录中

   templates目录下的HTML页面默认不能被直接访问，需要通过controller来访问，由thymeleaf来渲染，自动添加前缀和后缀

   ```java
   @Controller
   public class TemplateController  {

       @RequestMapping("/test1")
       public String test1(Model model){
           model.addAttribute("name","alice");
           return "success"; //自动添加前缀/templates和后缀.html
       }

   }
   ```

3. 使用Thymeleaf

   ```html
    
    
    
    
        
        Title 
    
    
        success 

        
         
    
    
   ```

4. 修改页面后，让其立即生效

   由于thymeleaf默认启用了缓存，所以修改html页面并不会实时生效

   ```properties
   # 禁用thymeleaf的缓存
   spring.thymeleaf.cache=false
   ```

   **补充：还需要开启IDEA的自动编译，IDEA默认是不自动编译**

   - Settting——>搜索Compiler——>Build Project Automatically
   - Help——>Find Action——>搜索Registry——>勾选compiler.automake......

### 3. 语法规则

#### 3.1 常用属性

- th:text、th:utext

  设置元素中的文本内容

  th:text对特殊字符进行转义，等价于内联方式[[${  }]]

  th:utext对特殊字符不进行转义，等价于内联方式[(${  })]

- th:html原生属性

  用来替换指定的html原生属性的值

- th:if、th:unless、th:switch、th:case

  条件判断，类似于c:if

- th:each

  循环，类似于c:forEach

- th:object、th:field

  用于表单数据对象的绑定，将表单绑定到Controller的一个JavaBean参数，常与th:field一起使用

  需要和*{}选择表达式配合使用

- th:fragment

  声明代码片段，常用于页面头部和尾部的引入

- th:include、th:insert、th:replace

  引入代码片段，类似于jsp:include

  三者的区别：

  > th:include 保留自己的标签，不要th:frament的标签（Thymeleaf 3.0中不推荐使用）
  >
  > th:insert 保留自己的标签，保留th:frament的标签
  >
  > th:replace 不要自己的标签，保留th:frament的标签


#### 3.2 表达式

- ${} 变量表达式

  获取对象的属性、方法

  使用内置的基本对象，如session、application等

  使用内置的工具对象，如#strings、#dates、#arrays、#lists、#maps等

- *{}选择表达式（星号表达式）

  需要和th:object配合使用，简化获取对象的属性

- @{} url表达式

  定义url

- 运算符

  eq  gt le   ==  !=   三目运算符

### 4. 热部署

​	使用SpringBoot提供的devtools实现热部署

​	原理：实现监控classpath下文件的变化，如果发生变化则自动重启

​	配置：添加devtools依赖

```xml
 
 
   org.springframework.boot 
   spring-boot-devtools 
   
   true 
 
```

## 八、扩展默认的SpringMVC功能

### 1. 简介

​	以前在SpringMVC中通过如下代码实现视图跳转和拦截器：

```xml
 
 
	 
      	 
  		 
  	 
 
```

​	SpringBoot自动配置默认并没有提供以上功能配置，需要自己扩展，使用WebMvcConfigure接口

### 2. 基本操作

​	步骤：

1. 定义一个配置类，实现WebMvcConfigure接口

2. 根据需要实现相应的方法

   ```java
   /**
    * Description：扩展默认的SpringMVC功能
    * 要求：
    * 1.使用@Configuration标注为配置类
    * 2.实现WebMvcConfigurer接口
    * 3.根据需要实现相应的方法
    * 注：这个接口中的方法都添加了Jdk1.8中的default方法修饰，不强制实现所有的方法（jdk1.8新特性）
    *  在SpringBoot1.0中是继承WebMvcConfigurerAdapter类，在SpringBoot2.0中已过时
    */
   @Configuration
   public class CustomMvcConfig implements WebMvcConfigurer {

       //添加ViewController
       @Override
       public void addViewControllers(ViewControllerRegistry registry) {
           //访问/showLogin时跳转到login视图
           registry.addViewController("/showLogin").setViewName("login");
       }

       // 添加Interceptor
       @Override
       public void addInterceptors(InterceptorRegistry registry) {
           registry.addInterceptor(new MyInterceptor()).addPathPatterns("/**").excludePathPatterns("/test2");
       }

   }
   ```

   ​

## 九、全局异常处理

### 1. 简介

​	当程序出现异常时进行全局处理，SpringBoot默认的异常提示：`Whitelabel Error Page`

​	两种方式：

- 定义错误码页面
- 定义异常通知

### 2. 定义错误码页面

​	创建`错误状态码.html`页面，放在templates/error目录中，当发生错误时会自动到该目录下查找对应的错误页面

​	可以创建如`4xx.html`或`5xx.html`页面，用来匹配所有该类型的错误（会先进行精确匹配）

```html
 5xx错误 
 状态码：[[${status}]] 
 错误提示：[[${error}]] 
 异常消息：[[${message}]] 
 时间戳：[[${timestamp}]] 
```

### 3. 定义异常通知

```java
@ControllerAdvice
public class ExceptionAdvice {

    @ExceptionHandler(ArithmeticException.class)
    public String arithmetic(Exception e){
        System.out.println("警报，程序出现异常，发短信："+e.getMessage());
        return "error/5xx";
    }

    @ExceptionHandler(Exception.class)
    public String exception(Exception e){
        System.out.println("警报，程序出现异常，发邮件："+e.getMessage());
        return "error/5xx";
    }

}
```

## 十、关于Servlet容器

### 1. 简介

​	SpringBoot中默认内置了Servlet容器：Tomcat

​	问题：SpringBoot默认是以jar包的方式启动内置的Servlet容器，没有web.xml文件，如何注册Servlet三大组件：Servlet、Filter、Listener？

​	解决：通过自定义Servlet配置，使用ServletRegistrationBean、FilterRegistrationBean、ListenerRegistrationBean

### 2. 注册Servlet组件

​	步骤：

1. 定义一个配置类

2. 自定义一个方法，用来注册组件

   ```java
   @Configuration
   public class CustomServletConfig {

       // 注册Servlet
       @Bean
       public ServletRegistrationBean myServlet() {
           ServletRegistrationBean  registrationBean = new ServletRegistrationBean<>();
           registrationBean.setServlet(new MyServlet());
           registrationBean.addUrlMappings("/myServlet");
           return registrationBean;
       }

       // 注册Filter
       @Bean
       public FilterRegistrationBean myFilter(){
           FilterRegistrationBean  registrationBean = new FilterRegistrationBean<>();
           registrationBean.setFilter(new MyFilter());
           registrationBean.addUrlPatterns("/showLogin","/test1");
           return registrationBean;
       }

       // 注册Listener
       @Bean
       public ServletListenerRegistrationBean myListener(){
           ServletListenerRegistrationBean  registrationBean = new ServletListenerRegistrationBean<>();
           registrationBean.setListener(new MyListener());
           return registrationBean;
       }

   }
   ```

   ​

### 3. 使用外部的Servlet容器

#### 3.1 优缺点

​	使用内置Servlet容器：将应用打成可执行的jar包，直接运行

​		优点：简单、方便

​		缺点：不支持JSP、可定制性差

​	使用外部Servlet容器：将应用打成war包，然后部署到外部的Tomcat

​		优点：支持JSP、可定制性强

#### 3.2 操作步骤

​	步骤：

1. 创建一个Maven的war工程

   有如下三个变化：

   - 打包方式为war

     ```xml
      war 
     ```

   - 将内置Tomcat的scope配置为provided

     ```xml
       
         org.springframework.boot 
         spring-boot-starter-tomcat 
         provided 
      
     ```

   - 定义了一个SpringBootServletInitializer的子类

     ```java
     /**
      * 要求：
      * 1.继承SpringBootServletInitializer类
      * 2.重写configure()方法
      * 3.调用SpringApplicationBuilder的sources()方法，传入SpringBoot应用的主程序类
      */
     public class ServletInitializer extends SpringBootServletInitializer {

         @Override
         protected SpringApplicationBuilder configure(SpringApplicationBuilder application) {
             // 传入SpringBoot应用的主程序类
             return application.sources(Springboot05WarApplication.class);
         }

     }
     ```

   2. 创建Web目录

      Project Structure——>Modules——>Deployment Descriptors——>+

   3. 配置前缀和后缀

      ```properties
      spring.mvc.view.prefix=/WEB-INF/views/
      spring.mvc.view.suffix=.jsp
      ```

      ​

   4. 配置Tomcat

      Tomcat 8.5及以上

## 十一、SpringBoot数据访问

### 1. JDBC

​	步骤：

1. 创建一个工程，选择以下模板：Web、MySQL、JDBC

2. 配置数据库连接信息

   ```properties
   spring.datasource.driver-class-name=com.mysql.jdbc.Driver
   spring.datasource.url=jdbc:mysql://localhost:3306/springboot?useUnicode=true&characterEncoding=utf-8
   spring.datasource.username=root
   spring.datasource.password=

   spring.datasource.type=org.apache.commons.dbcp.BasicDataSource
   ```

3. 测试

   ```java
   @RunWith(SpringRunner.class)
   @SpringBootTest
   public class Springboot06JdbcApplicationTests {

       @Autowired
       private DataSource dataSource;

       @Test
       public void contextLoads() throws SQLException {
           System.out.println("----------------------------------------------");
           System.out.println("DataSource类型："+dataSource.getClass());
           System.out.println("Connection连接："+dataSource.getConnection());
       }

   }
   ```

4. 配置连接池参数

   ```properties
   spring.datasource.initialSize=10
   spring.datasource.maxActive=100
   spring.datasource.minIdle=5
   spring.datasource.maxWait=50000
   ```

   ​

   问题：添加上面的参数后并不生效，因为SpringBoot默认并不支持这些参数（DataSourceProperties）

   解决：自定义数据源配置

   ```java
   @Configuration
   public class DataSourceConfig {

       @Bean
       // 从配置文件中读取spring.datasource属性，并注入给数据源的属性
       @ConfigurationProperties(prefix = "spring.datasource")
       public DataSource dataSource(){
          return new BasicDataSource();
       }

   }
   ```

5. 使用JdbcTemplate操作数据库

   ````java
   @Controller
   @RequestMapping("/user")
   public class UserController {

       @Autowired
       private JdbcTemplate jdbcTemplate;

       @RequestMapping("/findAll")
       @ResponseBody
       public List > findAll(){
           List > list =  jdbcTemplate.queryForList("select * from t_user");
           return list;

       }

   }
   ````

### 2. MyBatis

#### 2.1  基本用法

​	步骤：

1. 创建一个工程，选择以下模块：Web、MySQL、MyBatis

2. 配置application.yml

   ```yaml
   # 配置DataSource
   spring:
     datasource:
       driver-class-name: com.mysql.jdbc.Driver
       url: jdbc:mysql://localhost:3306/springboot?useUnicode=true&characterEncoding=utf-8
       username: root
       password:
       initialSize: 5
       maxActive: 100
       minIdle: 3
       maxWait: 50000

   # 配置MyBatis
   mybatis:
     type-aliases-package: com.itany.pojo
     mapper-locations: classpath:mapper/*.xml
   ```

3. 编写Mapper、Service、Controller

   映射文件

4. 配置MyBatisConfig

   ```java
   @Configuration
   //扫描MyBatis的Mapper接口所在的包
   @MapperScan("com.itany.mapper")
   public class MyBatisConfig {

       @Bean
       @ConfigurationProperties(prefix = "spring.datasource")
       public DataSource dataSource(){
           return new DruidDataSource();
       }

   }
   ```


#### 2.2 配置PageHelper分页插件

​	步骤：

1. 添加PageHelper的依赖

   ```xml
    
      com.github.pagehelper 
      pagehelper-spring-boot-starter 
      1.2.5 
    
   ```

2. 配置PageHelper的属性

   ```yaml
   # 配置PageHelper
   pagehelper:
     helper-dialect: mysql
   ```

3. 使用PageHelper实现分页

   ```java
   public PageInfo  findByPage(int pageNum, int pageSize) {

     //使用PageHelper设置分页
     PageHelper.startPage(pageNum,pageSize);

     List  users = userMapper.selectAll();

     PageInfo  pageInfo = new PageInfo<>(users);

     return pageInfo;
   }
   ```

#### 2.3 使用MyBatis-Plus

​	参考：http://mp.baomidou.com/

​	步骤：

1. 添加mybatis-plus的依赖（starter）

   ```xml
    
    
      com.baomidou 
      mybatis-plus-boot-starter 
      2.3 
    

    
    
      com.alibaba 
      druid 
      1.1.10 
    
   ```

2. 配置application.yml

   ```yaml
   mybatis-plus:
     mapper-locations: classpath:mapper/*.xml
     typeAliasesPackage: com.itany.pojo
     global-config:
       #主键类型  0:"数据库ID自增", 1:"用户输入ID",2:"全局唯一ID (数字类型唯一ID)", 3:"全局唯一ID UUID";
       id-type: 0
       #字段策略 0:"忽略判断",1:"非 NULL 判断"),2:"非空判断"
       field-strategy: 2
       #驼峰下划线转换
       db-column-underline: true
       #mp2.3+ 全局表前缀 t_
       #table-prefix: t_
       #刷新mapper 调试神器
       refresh-mapper: true
       #逻辑删除配置（下面3个配置）
       logic-delete-value: 1
       logic-not-delete-value: 0
       sql-injector: com.baomidou.mybatisplus.mapper.LogicSqlInjector
       #配置返回数据库(column下划线命名&&返回java实体是驼峰命名)，自动匹配无需as（没开启这个，SQL需要写as： select user_id as userId）
       map-underscore-to-camel-case: true
       cache-enabled: false
   ```

3. 配置MybatisPlusConfig

   ```java
   @Configuration
   @MapperScan("com.itany.mapper")
   public class MybatisPlusConfig {
       /*
        * 分页插件，自动识别数据库类型
        */
       @Bean
       public PaginationInterceptor paginationInterceptor() {
           return new PaginationInterceptor();
       }

       /*
        * 数据源
        */
       @Bean
       @ConfigurationProperties(prefix = "spring.datasource")
       public DataSource dataSource(){
           return new DruidDataSource();
       }
   }
   ```

4. 编写Mapper，继承BaseMapper

   ```java
   public interface UserMapper extends BaseMapper  {
   }
   ```



​	**补充：lombok的使用**

​	步骤：

1. 添加lombok的依赖

   ```xml
    
      org.projectlombok 
      lombok 
      1.16.18 
      provided 
    
   ```

2. 使用lombok提供的注解

   ```java
   /**
    * Description：lombok的使用
    * lombok提供了许多注解，标注在类上或属性上
    * 常用注解：@Getter、@Setter、@ToString、@EqualsAndHashCode
    */
   @TableName("t_user")  // 指定对应的数据库表名
   // @Getter
   // @Setter
   // @ToString
   // @EqualsAndHashCode
   @Data
   public class User implements Serializable {

       private Integer id;
       private String username;
       private String password;

   }
   ```

3. 在IDEA安装lombok插件

   由于源代码中并没有getter/setter等的定义，IDEA默认无法识别，会报错，需要安装lombok插件

## 十二、SpringBoot整合Redis

### 1. 简介

​	Redis是一个内存数据库，可以作为缓存、消息中间件、key-value数据库等来使用

### 2. 操作

​	步骤：

1. 添加相关依赖

   ```xml
    
    
      org.springframework.boot 
      spring-boot-starter-data-redis 
      
      
        
          io.lettuce 
          lettuce-core 
        
      
    

    
    
      redis.clients 
      jedis 
    
   ```

   注：在SpringBoot1.0中使用的Redis客户端是Jedis，在SpringBoot2.0中使用的是lettuce

2. 配置redis

   ```properties
   # Redis配置
   spring.redis.host=192.168.5.40
   spring.redis.port=6379
   spring.redis.password=itany
   spring.redis.database=0
   spring.redis.jedis.pool.max-active=100
   spring.redis.jedis.pool.max-idle=10
   spring.redis.jedis.pool.min-idle=3
   ```

3. 基本用法

   使用SpringDataRedis提供的工具：StringRedisTemplate、RedisTemplate

   ```java
   /**
        * 使用stringRedisTemplate
        * Redis数据类型：String、List、Set、ZSet、Hash
        */
       @Test
       public void test1(){
           // ValueOperations  stringStringValueOperations = stringRedisTemplate.opsForValue();
           // ListOperations  stringStringListOperations = stringRedisTemplate.opsForList();
           // SetOperations  stringStringSetOperations = stringRedisTemplate.opsForSet();
           // ZSetOperations  stringStringZSetOperations = stringRedisTemplate.opsForZSet();
           // HashOperations  stringObjectObjectHashOperations = stringRedisTemplate.opsForHash();

           /*
            * 操作String
            */
           // stringRedisTemplate.opsForValue().set("username","admin");
           // System.out.println(stringRedisTemplate.opsForValue().get("username"));

           /*
            * 操作List
            */
           // stringRedisTemplate.opsForList().leftPush("names","tom");
           // stringRedisTemplate.opsForList().leftPushAll("names","aaa","bbb","ccc");
           // System.out.println(stringRedisTemplate.opsForList().range("names",0,-1));

           /*
            * 存储对象
            */
           User user = new User();
           user.setId(1001);
           user.setUsername("tom");
           user.setPassword("123");

           //将对象转换为json字符串
           // String jsonString = JsonUtils.objectToJson(user);
           // System.out.println(jsonString);
           // stringRedisTemplate.opsForValue().set("user",jsonString);

           //将json字符串转换为对象
           String str = stringRedisTemplate.opsForValue().get("user");
           User u = JsonUtils.jsonToObject(str, User.class);
           System.out.println(u);
       }
   ```

   ​






 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)