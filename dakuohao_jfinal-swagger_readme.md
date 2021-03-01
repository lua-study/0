### JFinal-Swagger

上周开始接触JFinal框架，第一感觉就是提高了开发速度。之前使用Spring的时候，方便API文档生成，便继承了Swagger
在研究一段时间后，决定将Swagger集成到JFinal中，由于时间仓促，当前第一版本提供基础功能

#### JFinal-Swagger 使用说明
- mvn clean
- mvn install

**1. 添加依赖**

```
     
         com.feizhou 
         jfinal-swagger 
         1.0-SNAPSHOT 
     
```

**2. 下载 swagger-ui-master 将 dist 中文件加入到项目中**

```
可配置成类似如下路径：
    webapp
        static
            swagger
                favicon-16x16.png
                ...
                swagger-ui.js.map
    WEB-INF
        views
            swagger
                index.html
```

**3. 增加Swagger路由控制**

```
    以第二步的形式配置的目录结构，可直接使用如下路由配置
    routes.add(new SwaggerRoutes());
    
    也可自行配置路由信息
    
    public class SwaggerRoutes extends Routes {
    
        @Override
        public void config() {
            setBaseViewPath("/WEB-INF/views");
            add("/swagger", SwaggerController.class);
        }
    
    }

```

**4. 添加注解**

```
    提供四种注解：
    
    @Api(tag = "index", description = "测试输出")
    
    @ApiOperation(url = "/test", tag = "index", httpMethod = "get", description = "测试json")
    
    @Param(name = "id", description = "编号", required = true, dataType = "Long")
    
    @Params
    
```

**5. 配置扫描包信息**

```
    config.properties增加：swagger.base_package
    如：
    swagger.base_package=com.feizhou.swagger.test
```

注解使用示例：

```java

@Api(tag = "index", description = "测试输出")
public class IndexController extends Controller {

    public void index() {
        setAttr("aaa", "aaaaaa");
        this.render("index.html");
    }

    @ApiOperation(url = "/test", tag = "index", httpMethod = "get", description = "测试json")
    @Params({
            @Param(name = "id", description = "编号", required = true, dataType = "Long"),
            @Param(name = "name", description = "姓名", required = true, dataType = "String")
    })
    public void test() {
        List  list = Arrays.asList("123","456");
        this.renderJson(list);
    }
}
    
```




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)