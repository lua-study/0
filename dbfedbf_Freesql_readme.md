Freesql 基于FreeMarker自由的动态sql框架
==============================

Freesql是基于Java的动态sql框架，可以简单快速的使用FreeMarker语法构建动态sql。
    
使用指南
===================

如何在JFinal中使用Freesql
--------------------

Freesql默认提供了基于JFinal的插件，可以在JFinal中直接使用Freesql。

#初始化Freesql
在JFinalConfig中添加Freesql插件

```java
public class ProjectConfig extends JFinalConfig {
    //...
    @Override
    public void configPlugin(Plugins me) {
        //Freesql默认使用web根目录下的freesql作为模板存放根目录
        FreesqlPlugin freesql = new FreesqlPlugin();  

        //设置Freesql的模板存放目录为web根目录下的sql文件夹
        //FreesqlPlugin freesql = new FreesqlPlugin("sql");
        me.add(freesql);
    }
}
```

#扩展Model
JFinal的dao对象是继承自```com.jfinal.plugin.activerecord.Model```，Freesql在该块原有的功能上针对模板进行了扩展，在使用时需要替换原先Model的导入定义。

```java
import com.freesql.jfinal.Model;

public class User extends Model  {
    public static final User dao = new User();
}
```

#####根据模板使用分页功能

```java
public class UserController extends Controller{
    public void list() {
        Page  page = User.dao.paginateByTemp(getParaToInt("page"), getParaToInt("rows"), 
                "test/test.ftl", this.getParaMap());
        renderJson(page);
    }
}
```

#编写模板
用FreeMarker语法编写sql，动态、方便。简单的传值无法满足你时，可以使用函数进行解析。
Freesql默认用```{值}```的方式，设置sql查询参数。当普通的sql传值无法满足你时，可以Freesql函数，Freesql函数的使用方法为 ```{函数名(值[,值])}``` 如： ```{like(name)}```，需要存入多个值时可以用逗号分割参数：```{func(paramA, paramB)}```

#####模板test.ftl

```sql
SELECT
    * FROM user
WHERE 1 = 1
 
    AND username {like(username)} #使用Freesql函数like，username为参数名，此处为页面提交的值
 
 
    AND status = {status}         #使用status作为参数，此处为页面提交的值
 
```

#####Html页面

```html
     
        用户名： 
        状态：
         
             所有 
             有效 
             无效 
         
         
     
```


扩展函数
---------

当Freesql默认函数无法满足你时，可以自定义函数，并添加到Freesql中。

```java
public class LikeFunction implements FreesqlFunction {

    /**
     * 基于函数参数，及Map对象，返回sql参数列表，
     * 该方法返回的sql参数列表应该与sqlReplace的参数相对应
     *
     * @param funcParas     函数参数字符串
     * @param requestParams 参数值
     * @return sql参数列表
     * @throws com.freesql.function.FunctionParamsException
     */
    @Override
    public List  setSqlParas(String funcParas, Map  requestParams) throws FunctionParamsException {
        List  list = new ArrayList ();
        String value = requestParams.get(funcParas.trim());
        list.add('%' + value + '%');
        return list;
    }



    /**
     * 对sql的函数片段进行替换
     *
     * @param funcParas 函数参数字符串
     * @return sql函数替换结果
     */
    @Override
    public String sqlReplace(String funcParas) {
        return "LIKE ?";
    }
}
```

#####注册函数到Freesql中
```java
public class ProjectConfig extends JFinalConfig {
    //...
    @Override
    public void configPlugin(Plugins me) {
        FreesqlPlugin freesql = new FreesqlPlugin();
        freesql.add("like", new LikeFunction());
        me.add(freesql);
    }
}
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)