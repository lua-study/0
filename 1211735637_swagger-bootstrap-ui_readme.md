# swagger-bootstrap-ui



## 简介



`swagger-bootstrap-ui`是`Swagger`的前端UI实现,目的是替换`Swagger`默认的UI实现`Swagger-UI`,使文档更友好一点儿....



`swagger-bootstrap-ui` 只是`Swagger`的UI实现,并不是替换`Swagger`功能,所以后端模块依然是依赖`Swagger`的,需要配合`Swagger`的注解达到效果,[注解说明](swagger-annotation.md)





## 功能


* 接口文档说明,效果图如下：



![](https://xiaoymin.github.io/cloud-sdk-doc/assets/apidoc.jpg)

* 在线调试功能,效果图如下:

![](https://xiaoymin.github.io/cloud-sdk-doc/assets/debug1.jpg)

## Swagger简介



Swagger 是一个规范和完整的框架，用于生成、描述、调用和可视化 RESTful 风格的 Web 服务。总体目标是使客户端和文件系统作为服务器以同样的速度来更新。文件的方法，参数和模型紧密集成到服务器端的代码，允许API来始终保持同步。Swagger 让部署管理和使用功能强大的API从未如此简单。



Swagger-UI默认效果图如下：



![](https://xiaoymin.github.io/cloud-sdk-doc/assets/swagger.png)



## demo演示

[swagger-bootstarp-ui-demo](http://git.oschina.net/xiaoym/swagger-bootstrap-ui-demo)



## 下载



`swagger-bootstrap-ui`下载地址：[下载](http://git.oschina.net/xiaoym/swagger-bootstrap-ui/releases)



## 使用说明





* 首先需要引入swagger的配置包信息,如下：



```java

 

  io.springfox 

  springfox-swagger2 

  2.2.2 

 



 

 

  io.springfox 

  springfox-swagger-ui 

  2.2.2 

 



```






* maven项目中引用`swagger-bootstrap-ui`的jar包依赖,如下：



```java

 

  com.drore.cloud 

  swagger-bootstrap-ui 

  1.0 

 



```



* Spring项目中启用swagger,代码如下：


1.注解方式



```java

@Configuration

@EnableSwagger2

public class SwaggerConfiguration {



 @Bean

 public Docket createRestApi() {

 return new Docket(DocumentationType.SWAGGER_2)

 .apiInfo(apiInfo())

 .select()

 .apis(RequestHandlerSelectors.basePackage("com.drore.cloud"))

 .paths(PathSelectors.any())

 .build();

 }



 private ApiInfo apiInfo() {

 return new ApiInfoBuilder()

 .title("swagger-bootstrap-ui RESTful APIs")

 .description("swagger-bootstrap-ui")

 .termsOfServiceUrl("http://api.test.com/")

 .contact("developer@mail.com")

 .version("1.0")

 .build();

 }



}



```



* `swagger-bootstrap-ui`默认访问地址是：`http://${host}:${port}/doc.html`



## 注意事项



* swagger封装给出的请求地址默认是`/v2/api-docs`,所以`swagger-bootstrap-ui`调用后台也是`/v2/api-docs`,不能带后缀,且需返回json格式数据,框架如果是spring boot的可以不用修改,直接使用,如果是Spring MVC在web.xml中配置了`DispatcherServlet`,则需要追加一个url匹配规则,如下：



```java

 

  cmsMvc 

  org.springframework.web.servlet.DispatcherServlet 

  

  contextConfigLocation 

  classpath:config/spring.xml 

  

  1 

 



 

 

  cmsMvc 

  *.htm 

 

 

 

  cmsMvc 

  /v2/api-docs 

 



```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)