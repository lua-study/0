# auto-code-ui
欢迎使用auto-code-ui可视化界面代码生成器. [演示地址](http://106.13.119.110:8010/auto-code-ui/ui/index.html)
#### 介绍
本项目基于 [auto-code](https://gitee.com/ztp/auto-code),
在该项目的基础上增加可视化界面生成 `单表`,`一对一`,`一对多`,`多对多`代码.
如果你使用的是spring boot 开发. 请看 [如何与spring-boot集成](https://gitee.com/ztp/auto-code-ui-spring-boot-starter).

#### 软件架构

1.springMVC

2.servlet3.0

3.[auto-code代码生成器](https://gitee.com/ztp/auto-code)

4.layui


#### 安装教程

> 1.按照非常简单只需要在pom.xml增加一个jar包就行

```xml
 
     com.zengtengpeng 
     auto-code-ui 
     1.0.7 
 
```


#### 使用说明 [实例demo](https://gitee.com/ztp/auto-code-web-demo)

>1.集成一个 id="dataSource" 的数据源(可以使用任何连接池.只要id=dataSource就行). 如下:
```xml
     
    		 
    		 
    		 
    		 
    	 
```

> 2. 扫描controller时 必须要扫描 `com.zengtengpeng.ui.controller`,如下:
```xml
 
	 
```


> 3.在 `src/main/resources` 下增加`auto-code.yaml`文件  (更多参数请参考 [auto-code](https://gitee.com/ztp/auto-code#3))
```yaml
globalConfig:
  #生成代码的项目根路径
  parentPath: E:\resource\workspaceJDB\auto-code-web-demo
  #生成代码的父包,如父包是com.zengtengpeng.test则controller将在com.zengtengpeng.test.controller下.bean,service,dao同理
  parentPack: com.zengtengpeng.test
```

> 4. 集成完毕,启动自己的项目,访问 http://localhost:8080/auto-code-ui/ui/index.html.界面如下:

![global](http://images.zengtengpeng.com/auto-code-ui/global.png)


### 补充说明

>1.pagehelper(mybatis分页插件.如果不集成则分页失效)

    在 MyBatis-Configuration.xml 配置文件中增加拦截器
    
     
         
         
     
    
>2.swagger2 API接口文档(可选,如果不集成API看不了.对代码没有任何影响),(请注意.增加类的一定要在 `context:component-scan` 的扫描包里面.不然会找不到地址)

> 增加swagger2配置类

```java
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.stereotype.Component;
import springfox.documentation.builders.ApiInfoBuilder;
import springfox.documentation.builders.PathSelectors;
import springfox.documentation.builders.RequestHandlerSelectors;
import springfox.documentation.service.ApiInfo;
import springfox.documentation.service.Contact;
import springfox.documentation.spi.DocumentationType;
import springfox.documentation.spring.web.plugins.Docket;
import springfox.documentation.swagger2.annotations.EnableSwagger2;

@Configuration
@EnableSwagger2
@Component
public class Swagger2 {
    //swagger2的配置文件，这里可以配置swagger2的一些基本的内容，比如扫描的包等等
    @Bean
    public Docket createRestApi() {
        return new Docket(DocumentationType.SWAGGER_2)
                .apiInfo(apiInfo())
                .select()
                //为当前包路径
                .apis(RequestHandlerSelectors.basePackage("com.zengtengpeng"))
                .paths(PathSelectors.any())
                .build();
    }

    //构建 api文档的详细信息函数,注意这里的注解引用的是哪个
    private ApiInfo apiInfo() {
        return new ApiInfoBuilder()
                //页面标题
                .title("auto-code接口(swagger 目前有BUG,参数如果是实体类,设置忽略该参数不起作用.所以请忽略下面 (*.*) 带点的参数,这些参数不会被使用)")
                //创建人
                .contact(new Contact("ztp", "https://gitee.com/ztp/auto-code", "744489075@qq.com"))
                //版本号
                .version("1.0")
                //描述
                .description("API描述")
                .build();
    }
}
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)