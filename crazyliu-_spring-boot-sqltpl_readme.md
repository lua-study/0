# spring-boot-sqltpl

#### 介绍
一个帮你超轻量的管理sql模版插件，你可以自定义一个渲染引擎来使用模版。

- 使用 xml 对 sql 片段进行管理，类似 mybatis
- 可以自定义渲染 sql语句的引擎，默认采用 beetl html 引擎渲染
- 环境要求JDK1.8+ spring-boot 
- xml中的 exp 标签 是给未来准备开发的idea插件做的准备（非必须的）。

#### 使用说明三部曲

### 第一步编辑POM
```xml 
 
  
      com.github.threefish 
      sql-tpl 
      1.0.2.RELEASE 
  
 
 
     com.ibeetl 
     beetl 
     3.0.19.RELEASE 
 
 
 
     org.apache.commons 
     commons-lang3 
     3.9 
 

  
     
     
         
             src/main/resources 
         
         
             src/main/java 
             
                 **/*.xml 
             
             false 
         
     
 

```

### 第二步写注解
```java

package com.github.threefish.sqltpldemo;

import com.github.threefish.spring.sqltpl.SqlTplResourceLoader;
import com.github.threefish.spring.sqltpl.annotation.EnableSqlTpl;
import com.github.threefish.spring.sqltpl.templte.beetl.BeetlSqlTemplteEngineImpl;
import com.github.threefish.sqltpldemo.dao.SqlDao;
import org.apache.commons.lang3.StringUtils;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.context.annotation.Bean;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

/**
 * @author 黄川 huchuc@vip.qq.com
 * date: 2020/3/14
 */
@SpringBootApplication
@EnableSqlTpl
public class SqlTplDemoApplication {

    public static void main(String[] args) {
        //开启热更新
        SqlTplResourceLoader.DEVELOPER_MODE = true;
        SpringApplication.run(SqlTplDemoApplication.class, args);
    }

    @Bean
    public BeetlSqlTemplteEngineImpl sqlTemplteEngine() {
        BeetlSqlTemplteEngineImpl beetlSqlTemplteEngine = new BeetlSqlTemplteEngineImpl();
        beetlSqlTemplteEngine.getGt().registerFunctionPackage("S", StringUtils.class);
        return beetlSqlTemplteEngine;
    }

    @RestController
    class SqlXmlRest {

        @Autowired
        SqlDao sqlDao;

        @GetMapping("/selectOne")
        public String selectOne() {
            return sqlDao.selectOne();
        }

        @GetMapping("/selectTwo")
        public String selectTwo() {
            return sqlDao.selectTwo();
        }
    }

}

```

### 第三步写DAO和xml
```java

package com.github.threefish.sqltpldemo.dao;

import com.github.threefish.spring.sqltpl.SqlTplHolder;
import com.github.threefish.spring.sqltpl.annotation.SqlXml;
import com.github.threefish.spring.sqltpl.service.ISqlTpl;
import org.springframework.stereotype.Service;

import java.util.HashMap;
import java.util.Map;

/**
 * @author 黄川 huchuc@vip.qq.com
 * date: 2020/3/11
 */
@Service
@SqlXml
public class SqlDao implements ISqlTpl {

    private SqlTplHolder tplHolder;

    public String selectOne() {
        return tplHolder.getOriginalTemplate("selectOne");
    }


    public String selectTwo() {
        Map  stringObjectMap = new HashMap<>(1);
        stringObjectMap.put("name","测试");
        stringObjectMap.put("age",18);
        return tplHolder.getSql("selectTwo", stringObjectMap);
    }


    @Override
    public SqlTplHolder getSqlTplHolder() {
        return tplHolder;
    }

    @Override
    public void setSqlTpl(SqlTplHolder sqlsTplHolder) {
        this.tplHolder = sqlsTplHolder;
    }
}

```
```xml
 
 
 
 
     
     tableName_1 
     
        SELECT * from ${tableName}
     
     
     
        SELECT * from ${tableName} where
         if(S.isNotEmpty(name)){ 
        name like CONCAT('%', '${name}', '%');
         } 
         if(age>0){ 
        and age >= ${age}
         } 
     
 
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)