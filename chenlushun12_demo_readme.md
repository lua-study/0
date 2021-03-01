# 微服务demo #
===========================

## 模块介绍

   * demo-spring-cloud spring-cloud相关demo
   * demo-spring-boot  spring-boot相关demo
   * demo-dubbo spring boot整合dubbo
   * demo-docker-maven 利用docker构建微服务示例
   
### demo-spring-boot ###

------------
spring-boot相关demo，spring boot突破了以往所有访问数据库的方法，实现了更高级的访问方法。使开发者更为简单的开发应用。

#### demo-spring-boot-jdbc

spring boot中使用mysql数据库
本例子演示spring boot中如何操作mysql数据库。
构建一个用户部门角色的实际案例来演示

pom文件中添加一下配置

```xml
         
             org.springframework.boot 
             spring-boot-starter-data-jpa 
         
         
             mysql 
             mysql-connector-java 
         
```

application.yml中配置信息

```properties
#服务器端口
server:
  port: 8010
spring:
  #数据库配置
  datasource:
    url: jdbc:mysql://localhost:3306/ytx_api
    username: root
    password: 123456
  jpa:
    database: MYSQL
    show-sql: true
    hibernate:
      ddl-auto: update
      #naming_strategy:
      naming:
        strategy: org.hibernate.cfg.ImprovedNamingStrategy
        implicit-strategy: org.springframework.boot.orm.jpa.hibernate.SpringImplicitNamingStrategy
    properties:
      hibernate:
        dialect: org.hibernate.dialect.MySQL5Dialect
```


User实体

```java
@Entity
@Table(name = "user")
@Data
public class User implements Serializable {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    private String name;
    @DateTimeFormat(pattern = "yyyy-MM-dd HH:mm:ss")
    private Date createdate;
    @ManyToOne
    @JoinColumn(name = "did")
    // @JsonBackReference
    private Department department;


    @ManyToMany(cascade = {}, fetch = FetchType.EAGER)
    @JoinTable(name = "user_role",
            joinColumns = {@JoinColumn(name = "user_id")})
    private List  roles;
}
```
角色实体
```java

@Entity
@Table(name = "role")
@Data
public class Role implements Serializable {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    private String name;
}

```
部门实体

```java

@Entity
@Table(name = "department")
@Data
public class Department implements Serializable {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String name;

}

```

jpa配置信息


```java

@Order(Ordered.HIGHEST_PRECEDENCE)
@Configuration
//启动jpa的事务管理
@ComponentScan
@EnableTransactionManagement(proxyTargetClass = true)
//启动jpa的资源库，并制定资源库的位置
@EnableJpaRepositories(basePackageClasses = {UserRepository.class, DepartmentRepository.class, RoleRepository.class})
//指定实体的位置,两种方式
//@EntityScan(basePackageClasses = {User.class, Role.class, Department.class})
@EntityScan(basePackages = "demo.spring.boot.jdbc.**")
public class JpaConfig {

    public JpaConfig() {
    }

    @Bean
    public PersistenceExceptionTranslationPostProcessor persistenceExceptionTranslationPostProcessor() {
        return new PersistenceExceptionTranslationPostProcessor();
    }
}
```

部门Repository

```java

@Repository
public interface DepartmentRepository extends JpaRepository  {
}
```
用户Repository

```java

@Repository
public interface UserRepository extends JpaRepository  {
}

```

角色Repository
```java

@Repository
public interface RoleRepository extends JpaRepository  {
}
```
写一个Controller

```java

@RestController
@RequestMapping
public class DemoController {

    private static Logger logger = LoggerFactory.getLogger(DemoController.class);

    @Autowired
    UserRepository userRepository;
    @Autowired
    DepartmentRepository departmentRepository;
    @Autowired
    RoleRepository roleRepository;

    @RequestMapping("/1")
    public void save() {
        userRepository.deleteAll();
        departmentRepository.deleteAll();
        roleRepository.deleteAll();

        Department department = new Department();
        department.setName("开发部");
        departmentRepository.save(department);

        Role role = new Role();
        role.setName("admin");
        roleRepository.save(role);
        Assert.assertNotNull(role.getId());

        User user = new User();
        user.setName("张三");
        user.setCreatedate(new Date());
        user.setDepartment(department);
        List  roleList = roleRepository.findAll();
        Assert.assertNotNull(roleList);
        user.setRoles(roleList);
        userRepository.save(user);
        Assert.assertNotNull(user);
    }

    @RequestMapping("/2")
    public Page  findPage() {
        Pageable pageable = new PageRequest(0, 10, new Sort(Sort.Direction.ASC, "id"));
        Page  page = userRepository.findAll(pageable);
        Assert.assertNotNull(page);
        for (User user : page.getContent()) {
            logger.info(user.getName());
        }
        return page;
    }
}
```
浏览器中访问：http://localhost.ytx.cc:8010/2

返回结果：

```json
{
content: [
{
id: 2,
name: "张三",
createdate: 1492254026000,
department: {
id: 2,
name: "开发部"
},
roles: []
}
],
last: true,
totalElements: 1,
totalPages: 1,
size: 10,
number: 0,
sort: [
{
direction: "ASC",
property: "id",
ignoreCase: false,
nullHandling: "NATIVE",
ascending: true,
descending: false
}
],
first: true,
numberOfElements: 1
}
```
虽然我们没有写一条sql，但是已经实现了对user、department、role的crud，以及常见的查询，比如分页查询

### demo-docker-maven  ####

------------
#### 使用dockerfile构建docker镜像

在文件目录下面创建 Dockerfile
```
#基础镜像
FROM java:8

#将本地文件挂到当前容器
VOLUME /Users/chenlushun/yc-code/demo/demo-docker-maven/target/demo-docker-maven-1.0-SNAPSHOT.jar

#拷贝文件到容器
ADD  demo-docker-maven-1.0-SNAPSHOT.jar  app.jar

RUN bash -c "touch /app.jar"

#暴露端口
EXPOSE 8761

#配置容器启动之后的命令
ENTRYPOINT ["java","-Djava.security.egd=file:/dev/./urandom","-jar","app.jar"]

```
docker build -t eacdy/test1 .  # 格式:docker build -t 标签 名称 Dockerfile的相对位置 

构建成功: Successfully built a7cc6f4de088 。

docker run -p 8761:8761 eacdy/t   #运行docker容器

#### 使用maven构建微服务镜像

使用maven构建微服务镜像
maven插件地址：https://github.com/spotify/docker-maven-plugin
```xml
 
 
     com.spotify 
     docker-maven-plugin 
     0.4.12 
     
         
         microservice-discovery-eureka 
         java 
         
         ["java","-jar","/${project.build.finalName}.jar"] 
         
             
                 / 
                 ${project.build.directory} 
                 ${project.build.finalName}.jar 
             
         
     
 
```
构建镜像 ：mvn clean package docker:build

## 参考文献

   * https://spring.io/guides/gs/spring-boot

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)