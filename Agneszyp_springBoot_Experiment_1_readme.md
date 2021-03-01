# 实验一  使用Spring Boot构建应用程序
## 一、 实验目的
- 1、 掌握使用IntelliJ IDEA创建Spring Boot应用程序的方法；
- 2、 了解spring-boot-starter-parent的配置内容；
- 3、 掌握如何利用Starter扩展Spring Boot应用程序的功能；
- 4、 掌握如何配置Starter;
- 5、 掌握如何通过属性文件定制Spring Boot应用程序的初始化参数；
- 6、 掌握使用Spring Boot编写简单的单元测试；
- 7、 了解Spring Boot应用程序的Fat Jar文件；
- 8、 掌握Markdown轻量级标记语言编写README.md文件。
## 二、 实验环境
- 1、JDK 11
- 2、Maven 3.6.0
- 3、IntelliJ IDEA
## 三、 实验任务
1、 通过IntelliJ IDEA的Spring Initializr向导创建Spring Boot项目；

2、 添加两个功能模块：spring MVC、lombok；
 
     
 

3、 添加阿里云镜像仓库作为项目maven仓库；在pom.xml里添加以下的代码即可
```
     
         
             AliYun-public 
             public 
             https://maven.aliyun.com/repository/public 
         
     
```
4、 解释项目pom.xml文件中主要标签的意义；
- parent：父项目，如果项目中没有规定某个元素的值，那么父项目中的对应值即为项目的默认值
```
     
         
         
         
         
         
         
         
         
     
```
- group ID&artifactId:标识一个构件,不能有两个不同的项目拥有同样的artifact ID和groupID
```
     
     jar 
     
     1.0.0 
     
     experiment_1 
     
     Demo project for Spring Boot 
```
- build:构建项目需要的信息
```
     
        
         
             
             
                 
                 
                     
                     
                     
                     
                     
                     
                 
             
         
     
```
- dependencies:依赖信息，CAV缺一不可，maven在网络下回自动下载jar包
```
 
     
     
        ......
     
 
```
5、 配置jetty或undertow作为Spring Boot应用程序的默认Servlet容器；
在pom.xml中`spring-boot-starter-web`依赖中排除`spring-boot-starter-tomcat`,再加上`spring-boot-starter-jetty`依赖，如以下代码
```
         
             org.springframework.boot 
             spring-boot-starter-web 
             
                 
                     org.springframework.boot 
                     spring-boot-starter-tomcat 
                 
             
         
         
             org.springframework.boot 
             spring-boot-starter-jetty 
         
```
改完后，运行代码可以看到如图
 
     
 
6、 添加一个简单的Spring Mvc控制器组件

```
@RestController
public class TestController {
    @RequestMapping("/hello")
    public String testController(){
        return "hello world";
    }
}
```

7、 定义一个CommandLineRunner的Bean，用于检查Spring Boot应用程序启动完成后在Spring IoC容器中注册的所有Bean。
```
    @Bean
    public CommandLineRunner commandLineRunner(ApplicationContext ctx){
        return args -> {
            System.out.println("由SpringBoot注册的所有bean：");

            String[] beanNames = ctx.getBeanDefinitionNames();
            Arrays.sort(beanNames);
            for(String beanName:beanNames){
                System.out.println(beanName);
            }
        };
    }
```
运行后我们可以看到如图：（以下省略了许多bean）
 
     
 
8、 编写一个简单的单元测试

```
@SpringBootTest
@AutoConfigureMockMvc
class Experiment1ApplicationTests {
    @Autowired
    private MockMvc mockMvc;

    @Test
    public void test() throws Exception {
        this.mockMvc.perform(get("/hello")).andDo(print()).andExpect(status().isOk())
                .andExpect(content().string(containsString("hello world")));
    }
}
```

使用Spring MockMvc这种方法根本不启动服务器，Spring在该层处理传入的HTTP请求并将其交给控制器。这样，几乎使用了整个堆栈，并且将以与处理真实HTTP请求完全相同的方式调用您的代码，而无需花费启动服务器的费用。

![运行结果](https://images.gitee.com/uploads/images/2020/0324/172400_c3a249d8_4850054.png)

9、 使用IntelliJ IDEA的HTTP Client工具测试控制器端口；
在项目的根目录下新建test.http文件，并加上以下代码
```
GET localhost:8080/hello
```
运行脚本后，结果如图
 
     
 

10、 在命令行中使用spring-boot插件运行Spring Boot应用程序，并把嵌入式Servlet容器的默认端口8080改为9090；
在terminal输入以下命令：
```
mvn spring-boot:run -Dspring-boot.run.jvmArguments="-Dserver.port=9090"
```
结果如图：
 
     
 
 
     
 

11、 在属性文件中配置Spring Boot应用程序以debug模式运行。
在application.properties文件中加入以下代码

```
debug=true
```
运行后可发现终端出现更多的信息，如图

 
     
 
12、 在命令行中编译、打包Spring Boot应用程序。
在terminal输入以下命令

```
mvn clean package -DskipTests
```
执行`clean`和`package`并跳过`test`,结果如下

 
     
 
13、 在命令行中使用java命令运行Spring Boot应用程序的Jar文件。
首先cd进入jar文件所在的目录，在使用java命令执行

```
cd 'jar文件所在目录'
java -jar '可执行jar文件名称'
```

如图：

 
     
 

14、 在命令行中使用java命令运行Spring Boot应用程序的Jar文件，带参数改变嵌入式Servlet容器的默认端口8080改为9090。
在terminal把命令改为
```
java -jar experiment_1-1.0.0.jar --server.port=9090
```
结果如下：
 
     
 




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)