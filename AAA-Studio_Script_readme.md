

# 微服务介绍

##  架构变迁

[从单体架构到微服务变迁](https://cloud.tencent.com/developer/article/1481339)

## 微服务优缺点

### 优点

* 通过分解巨大单体式应用为多个服务方法解决了复杂性问题

* 支撑多开发语言，通过Http或RPC协议通讯

* 每个微服务独立的开发，部署

* 易于规模化开发，多个开发团队可以并行开发，每个团队负责一项服务

* 改善故障隔离。一个服务宕机不会影响其他的服务

### 缺点

* 开发者需要应对创建分布式系统所产生的额外的复杂因素
  * 测试工作更加困难
  * 需要采用服务间的通讯机制
  * 很难在不采用分布式事务的情况下跨服务实现功能
  * 跨服务实现要求功能要求团队之间的紧密协作
* 部署复杂

## Spring Cloud

### 版本介绍

![Spring cloud版本](https://images.gitee.com/uploads/images/2020/0401/095933_d6748ffe_1764378.png "QQ图片20200401095817.png")

![Spring cloud 对应 Spring Boot](https://images.gitee.com/uploads/images/2020/0401/103545_af4bef0a_1764378.png)

## 微服务调用介绍

![输入图片说明](https://gitee.com/uploads/images/2019/0424/103247_d4105061_1764378.png "435188-20180412214011124-1859129542.png")

**模块注解**

- Provider: 暴露服务的服务提供方。
- Consumer: 调用远程服务的服务消费方。
- Registry: 服务注册与发现的注册中心。
- Monitor: 统计服务的调用次调和调用时间的监控中心。
- Container: 服务运行容器。

**流程详解**

0. 服务容器负责启动/加载，运行服务提供者。

1. 服务提供者在启动时，向注册中心注册自己提供的服务（Zookeeper/Eureka/Nacos/Consul）。
2. 服务消费者在启动时，向注册中心订阅自己所需的服务。
3. 注册中心返回服务提供者地址列表给消费者，如果有变更，注册中心将基于长连接推送变更数据给消费者。
4. 服务消费者，从提供者地址列表中，基于软负载均衡算法，选一台提供者进行调用，如果调用失败，再选另一台调用。
5. 服务消费者和提供者，在内存中累计调用次数和调用时间，定时每分钟发送一次统计数据到监控中心（根据数据可以动态调整权重）。

## CAP
[推荐文章](https://www.cnblogs.com/duanxz/p/5229352.html)

## 领域驱动设计(DDD:Domain-Driven Design)

* 现在很多的微服务开发团队在设计和实现微服务的时候觉得**只要把原来的单体拆小**，就是微服务了。但是这不一定是正确的微服务，可能只是一个拆小的小单体。

* 我听过太多业务开发的声音，“面试造航母、工作拧螺丝”，日常工作就是建表写增删改查。为什么会有这样的认知，其根源在于**表驱动设计思想而非领域驱动设计**。

[推荐文章](https://zhuanlan.zhihu.com/p/42565478)

# Jaina

## 微服务架构

![输入图片说明](https://images.gitee.com/uploads/images/2020/0323/161245_cd8c6b31_1764378.jpeg "Spring Cloud 微服务架构图.jpg")

## 技术导图

![输入图片说明](https://images.gitee.com/uploads/images/2020/0401/113554_b3efda2b_1764378.jpeg "微服务技术导图.jpg")

## 配置属性

### JWT 配置属性

|  配置项          |  含义                      |  默认值  |
| :------------------------------ | ----------------------------------------- | ----------------------- |
| `jaina.jwt.id`                  | JWT 唯一ID                                | 随机UUID                |
| `jaina.jwt.issuer`              | 发行人                                    |                         |
| `jaina.jwt.subject`             | 主题                                      |                         |
| `jaina.jwt.audience`            | 读者                                      |                         |
| `jaina.jwt.expiration`          | 距现在Token终止时间分钟数                 | 43200(30天)             |
| `jaina.jwt.notBefore`           | 距现在Token生效时间分钟数 0为立即生效 | 0                       |
| `jaina.jwt.signature.algorithm` | 签名算法                                  | HS256                   |
| `jaina.jwt.signature.key`       | 签名密钥                                  | bankgl*&uyTTg^b         |

### Gateway配置属性

|  配置项                  |  含义                                         |  默认值  |
| :-------------------------------------- | ------------------------------------------------------------ | ----------------------- |
| `jaina.gateway.client`                  | 客户端信息列表(数据类型MAP), key为client_id,子属性参考[Client配置属性](#Client配置属性) |                         |
| `jaina.gateway.auth-header`             | Http Herader认证属性                                         | X-AAA-Authorization     |
| `jaina.gateway.data-id`                 | Nacos动态路由dataId                                          | Jaina-gateway-route     |
| `jaina.gateway.group`                   | Nacos动态路由group                                           | DEFAULT_GROUP           |
| `jaina.gateway.token-path`              | 获取Token Uri地址                                            | /oauth/v2/token         |
| `jaina.gateway.filter.enable`           | 是否开启过滤器检查                                           | true                    |
| `jaina.gateway.swagger.path`            | Swagger返回JSON文档的接口路径（全局配置）                    | /v2/api-docs            |
| `jaina.gateway.swagger.version`         | Swagger文档版本（全局配置）                                  | 2.0                     |
| `jaina.gateway.swagger.generate-routes` | 自动生成文档的路由名称，设置了generateRoutes之后，ignoreRoutes不生效 |                         |
| `jaina.gateway.swagger.ignore-routes`   | 不自动生成文档的路由名称，设置了generateRoutes之后，本配置不生效 |                         |

### Client配置属性

|  配置项                   |  含义     |  默认值  |
| :--------------------------------------- | ------------------------ | ----------------------- |
| `jaina.gateway.client.[key].secret`      | 客户密钥                 |                         |
| `jaina.gateway.client.[key].description` | 描述                     |                         |
| `jaina.gateway.client.[key].white-list`  | IP白名单,多地址用","分割 |                         |

## 服务模块访问地址

| 模块名                         |  描述                                                              | 账号/密码                                                        |
| :----------------------------:| :--------------------------------------------------------------------------------| :----------------------------:|
| Nacos             | http://124.232.135.106:7848/nacos | nacos/nacos |
| Sky Walking      | http://124.232.135.106:8080/                   | admin/3kuJHG#87Ytg^                            |
| Sentinel Dashboard | http://124.232.135.106:6610/ |                                                                                  |
| Spring Boot Admin |http://124.232.135.106:6512/login                                                |admin/admin                                                |
| GPE            |http://124.232.135.106:3000/                                         |                                         |
| ELK          | http://124.232.135.106:5601/                         |                                                      |
| Gateway | http://124.232.135.106:6510/specialline/{业务访问URI} |  |
| Access Token | http://124.232.135.106:6510/oauth/v2/token?client_id=&client_secret= | client_id: test client_secret: secret |

# Spring Boot 高阶用法

## @Conditional

Spring Boot条件注解`@Conditional`，可用于根据某个特定的条件来判断是否需要创建某个特定的Bean。接下来我们就对@Conditional的使用做一个简单的介绍。

@Conditional注解需要和Condition接口搭配一起使用。通过对应Condition接口来告知是否满足匹配条件。

```java
@Target({ElementType.TYPE, ElementType.METHOD})
@Retention(RetentionPolicy.RUNTIME)
@Documented
public @interface Conditional {
    /**
     * 所有用于匹配的Condition接口(实现该接口的类)，只有这些类都返回true才认为是满足条件
     */
    Class [] value();
}
```

`@Conditional`注解可以添加在`@Configuration、@Component、@Service`等修饰的类上用于控制对应的Bean是否需要创建，或者添加在@Bean修饰的方法上用于控制方法对应的Bean是否需要创建。

> `@Conditional`添加在`@Configuration`修饰的类上，用于控制该类和该类里面`所有添加的@Bean方法`对应的Bean是否需要创建。



**@Conditional扩展注解**

| 条件注解                        | 实例                                                         | 解释                                                         |
| ------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| @ConditionalOnBean              | @ConditionalOnBean(DataSource.class)                         | Spring容器中不存在对应的实例生效                             |
| @ConditionalOnMissingBean       | @ConditionalOnMissingBean(name = "redisTemplate")            | Spring容器中不存在对应的实例生效                             |
| @ConditionalOnSingleCandidate   | @ConditionalOnSingleCandidate(FilteringNotifier.class)       | Spring容器中是否存在且只存在一个对应的实例，或者虽然有多个但 是指定首选的Bean生效 |
| @ConditionalOnClass             | @ConditionalOnClass(RedisOperations.class)                   | 类加载器中存在对应的类生效                                   |
| @ConditionalOnMissingClass      | @ConditionalOnMissingClass(RedisOperations.class)            | 类加载器中不存在对应的类生效                                 |
| @ConditionalOnExpression        | @ConditionalOnExpression(“’${server.host}’==’localhost’”)    | 判断SpEL 表达式成立生效                                      |
| @ConditionalOnJava              | @ConditionalOnJava(JavaVersion.EIGHT)                        | 指定Java版本符合要求生效                                     |
| @ConditionalOnProperty          | @ConditionalOnProperty(prefix = “spring.aop”, name = “auto”, havingValue = “true”, matchIfMissing = true) | 应用环境中的属性满足条件生效                                 |
| @ConditionalOnResource          | @ConditionalOnResource(resources=”mybatis.xml”)              | 存在指定的资源文件生效                                       |
| @ConditionalOnWebApplication    |                                                              | 当前应用是Web应用生效                                        |
| @ConditionalOnNotWebApplication |                                                              | 当前应用不是Web应用生效                                      |

​    上面的扩展注解我们可以简单的分为以下几类：

- Bean作为条件：@ConditionalOnBean、@ConditionalOnMissingBean、@ConditionalOnSingleCandidate。
- 类作为条件：@ConditionalOnClass、@ConditionalOnMissingClass。
- SpEL表达式作为条件：@ConditionalOnExpression。
- JAVA版本作为条件: @ConditionalOnJava
- 配置属性作为条件：@ConditionalOnProperty。
- 资源文件作为条件：@ConditionalOnResource。
- 是否Web应用作为判断条件：@ConditionalOnWebApplication、@ConditionalOnNotWebApplication。

## 自定义配置

**添加自定义配置类**

使用注解`@ConfigurationProperties`

```java
@ConfigurationProperties(prefix = JwtProperties.PREFIX)
public class JwtProperties {
    public static final String PREFIX = "jaina.jwt";
    /**
	 * jwt ID
	 */
	private String id = IdUtil.randomUUID();
	/**
	 * 发行人
	 */
	private String issuer;
    ...
}
```

**添加注解处理器**

为配置类`JwtProperties`添加注解`@ConfigurationProperties`后，IDEA会出现红色提示`Spring Boot Configuration Annotation Processor not found in classpath`，这是因为还需要为注解配置处理器

```maven
 
   org.springframework.boot 
   spring-boot-configuration-processor 
 
```

**编译生成提示文件**

在`resources`目录下新建`META-INF`文件夹，在下面新建`spring-configuration-metadata.json`文件，在这里面进行配置

```json
{
  "groups": [
    {
      "name": "jaina.jwt",
      "type": "org.jaina.common.properties.JwtPropertie",
      "sourceType": "org.jaina.common.properties.JwtPropertie"
    }
  ],
  "properties": [
    {
      "name": "jaina.jwt.id",
      "type": "java.lang.String",
      "description": "jwt唯一ID.",
      "defaultValue": "随机UUID",
      "sourceType": "org.jaina.common.properties.JwtPropertie"
    }, {
      "name": "jaina.jwt.issuer",
      "type": "java.lang.String",
      "description": "发行人.",
      "sourceType": "org.jaina.common.properties.JwtPropertie"
    }
    ... 
  ],
  "hints": []
}
```

大家参考下面`properties`表格进行配置上的理解。

|     名称     |  类型  |  说明                                         |
| :----------: | :----: | :----------------------------------------------------------- |
|     name     | String | 属性的全名。名称采用小写的周期分隔形式(例如server.address)。此属性是强制性的。 |
|     type     | String | 属性的数据类型的完整签名（例如java.lang.String），但也是完整的泛型类型（例如java.util.Map ）。您可以使用此属性来指导用户可以输入的值的类型。为了保持一致性，通过使用其包装对应项（例如，boolean变为java.lang.Boolean）来指定基元的类型。请注意，此类可能是一个复杂类型，它从Stringas绑定的值转换而来。如果类型未知，则可以省略。 |
| description  | String | 可以向用户显示的组的简短描述。如果没有可用的描述，则可以省略。建议描述为简短段落，第一行提供简明摘要。描述中的最后一行应以句点（.）结尾。 |
|  sourceType  | String | 贡献此属性的源的类名称。例如，如果属性来自带注释的类@ConfigurationProperties，则此属性将包含该类的完全限定名称。如果源类型未知，则可以省略。 |
| defaultValue | Object | 默认值，如果未指定属性，则使用该值。如果属性的类型是数组，则它可以是值数组。如果默认值未知，则可以省略。 |

**配置类注入Spring**

将配置类注入`Spring`有以下两种方式`(推荐第一种)`

* @EnableConfigurationProperties

  ```java 
  @Configuration
  @AutoConfigureAfter({ JwtProperties.class })
  @EnableConfigurationProperties({ JwtProperties.class })
  public class JwtAutoConfiguration {
  
  	@Bean
  	@ConditionalOnMissingBean({ Jwt.class })
  	public Jwt instance(JwtProperties propertie) {
  		Jwt jwt = new Jwt(propertie);
  		return jwt;
  	}
  }
  ```

* @Component

	```java @ConfigurationProperties(prefix = JwtProperties.PREFIX)
  @Componet
  @ConfigurationProperties(prefix = JwtProperties.PREFIX)
  public class JwtProperties {
      public static final String PREFIX = "jaina.jwt";
      /**
  	 * jwt ID
  	 */
  	private String id = IdUtil.randomUUID();
      ...
  }
  ```

**完成上述操作即可在`application.yml或application.properties`进行自定义配置**

## 自动装配

**定义**

基于约定大于配置的原则，实现Spring组件自动装配的目的

**装配的依赖(方式)**

模式注解、@Enable模块、条件装配、工厂加载机制

激活自动化装配、实现自动化装配、配置自动装配实现

**命名规范**

spring官方提供的starts，命名规范：spring-boot-starter-*

第三方提供的starts, 命名 *-spring-boot-starter

**底层装配技术**

- Spring 模式注解装配
- Spring `@Enable`模块装配
- Spring条件装配
- Spring工厂加载机制
  - 实现类： SpringFactoriesLoader
  - 配置资源：META-INF/spring.factories

**实现方式**

**自定义配置类**

```java
@Configuration
@AutoConfigureAfter({ JwtProperties.class })
@EnableConfigurationProperties({ JwtProperties.class })
public class JwtAutoConfiguration {

	@Bean
	@ConditionalOnMissingBean({ Jwt.class })
	public Jwt instance(JwtProperties propertie) {
		Jwt jwt = new Jwt(propertie);
		return jwt;
	}
}
```

**配置自动装配**
在`resources`目录下新建`META-INF`文件夹，在下面新建`spring.factories`文件，在这里面进行配置，将`JwtAutoConfiguration`绑定给`@EnableAutoConfiguration`

```
# Auto Configure
org.springframework.boot.autoconfigure.EnableAutoConfiguration=\
org.jaina.common.jwt.config.JwtAutoConfiguration
```
# Future
## 云原生
云原生应用的三大特征：容器化封装、动态管理、面向微服务
[推荐文章](http://dockone.io/article/2991)

## Service mesh
Service Mesh 又译作“服务网格”，作为服务间通信的基础设施层。
如果用一句话来解释什么是 Service Mesh，可以将它比作是应用程序或者说微服务间的 TCP/IP，负责服务之间的网络调用、限流、熔断和监控。
[推荐文章](https://www.cnblogs.com/xishuai/p/microservices-and-service-mesh.html)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)