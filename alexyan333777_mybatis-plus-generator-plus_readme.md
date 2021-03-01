## 比mybatis-plus代码生成器更好用的生成器 mybatis-plus-generator-plus 
### 优势
- #### 可以自动生成代码注释从数据库中取得
- #### 使用freemarker来自定义模板使其更加方便
- #### 灵活选择模板，可以自行配置多套，并且灵活切换
- #### 已经给定了预留的模板，可以做到拿来即用
- #### 无需修改代码，仅修改GenerateConfig.xml中的配置即可，更加清晰 

### 使用方式 
 - ##### 打开src\main\resources 下的 GenerateConfig.xml文件 并对文件进行修改
```
     
     
         
         yu_chen 

         
         
             com.mysql.cj.jdbc.Driver 
             jdbc:mysql://localhost:3306/information_schema?serverTimezone=GMT%2B8 
             root 
             chenyu 
         
         
         
         
         com.jsly -->
         com.zynn.count 
    
         
         
             
             
         
    
    
         
         
         
             *.java 
             *Mapper.java 
             *Mapper.xml 
             *Service.java 
             *ServiceImpl.java 
             *Controller.java 
         
    
```
#### 修改完配置之后 打开com.yu.GenerateCodeRun 这个类直接运行就可以 不需要做任何修改

```
public class GenerateCodeRun {

    public static void main(String[] args) throws DocumentException, IOException, TemplateException {

        //找到配置文件的路径
        String path = System.getProperty("user.dir") + "\\src\\main\\resources\\" + "GenerateConfig.xml";
        final Config config = ConfigParser.getConfig(path);
        System.out.println(config);
        //获取得到的表的集合
        List  entityList = InitDb.getInstence(config).initTables();
        for (EntityVO entity : entityList) {
            GenerateUtil.generateTemplate(entity, "model");
            GenerateUtil.generateTemplate(entity, "dao");
            GenerateUtil.generateTemplate(entity, "mapper");
            GenerateUtil.generateTemplate(entity, "service");
            GenerateUtil.generateTemplate(entity, "serviceImpl");
            GenerateUtil.generateTemplate(entity, "controller");
            System.out.println(entity);
        }
        System.out.println("------------生成完毕!-------------");
    }


```
### 模板文件
- #### 对应的模板文件地址 \ftl\model-mybatis-plus 
- #### 如果觉得模板生成的文件不是很满意，可以自行进行修改
- #### 模板引擎中输出的对象格式如下
```
{
    "className":"Student",
    "tableName":"bs_student",
    "basePackage":"com.zynn.count",
    "ftlPath":"\\ftl\\model-mybatis-plus",
    "tableComment":"学生表",
    "basePackageMap":{
        "controller":{
            "basePackageName":"controller",
            "ftlName":"controller.ftl",
            "outputFileName":"*Controller.java",
            "outputFilePath":"\\output\\com\\zynn\\count\\controller",
            "packageName":"com.zynn.count.controller"
        },
        "dao":{
            "basePackageName":"dao",
            "ftlName":"dao.ftl",
            "outputFileName":"*Mapper.java",
            "outputFilePath":"\\output\\com\\zynn\\count\\dao",
            "packageName":"com.zynn.count.dao"
        },
        "service":{
            "basePackageName":"service",
            "ftlName":"service.ftl",
            "outputFileName":"*Service.java",
            "outputFilePath":"\\output\\com\\zynn\\count\\service",
            "packageName":"com.zynn.count.service"
        },
        "model":{
            "basePackageName":"entity",
            "ftlName":"model.ftl",
            "outputFileName":"*.java",
            "outputFilePath":"\\output\\com\\zynn\\count\\entity",
            "packageName":"com.zynn.count.entity"
        },
        "mapper":{
            "basePackageName":"mapper",
            "ftlName":"mapper.ftl",
            "outputFileName":"*Mapper.xml",
            "outputFilePath":"\\output\\com\\zynn\\count\\mapper",
            "packageName":"com.zynn.count.mapper"
        },
        "serviceImpl":{
            "basePackageName":"service.impl",
            "ftlName":"serviceImpl.ftl",
            "outputFileName":"*ServiceImpl.java",
            "outputFilePath":"\\output\\com\\zynn\\count\\service\\impl",
            "packageName":"com.zynn.count.service.impl"
        }
    },
    "entityAttrs":[
        {
            "fieldName":"id",
            "javaType":"Integer",
            "comment":"",
            "jdbcFieldName":"id",
            "jdbcType":"INTEGER",
            "isPrimaryKey":"1"
        },
        {
            "fieldName":"name",
            "javaType":"String",
            "comment":"学生姓名",
            "jdbcFieldName":"name",
            "jdbcType":"VARCHAR",
            "isPrimaryKey":"0"
        },
        {
            "fieldName":"num",
            "javaType":"String",
            "comment":"学号",
            "jdbcFieldName":"num",
            "jdbcType":"VARCHAR",
            "isPrimaryKey":"0"
        },
        {
            "fieldName":"createTime",
            "javaType":"LocalDateTime",
            "comment":"创建时间",
            "jdbcFieldName":"create_time",
            "jdbcType":"TIMESTAMP",
            "isPrimaryKey":"0"
        },
        {
            "fieldName":"updateTime",
            "javaType":"LocalDateTime",
            "comment":"更新时间",
            "jdbcFieldName":"update_time",
            "jdbcType":"TIMESTAMP",
            "isPrimaryKey":"0"
        }
    ]
}

```
- #### freemarker 取值格式为：${属性名!}，对freemarker取值不熟的同学可以看下面这个链接
- ####  freemarker取值教程 

### 生成文件的目录结构

![avatar](https://app.public.zhuiyinanian.com/TIM20191115160928.png)

### 生成文件预览 以Student为例
- #### model文件
```
    package com.zynn.count.entity;
    
    import lombok.Data;
    
    /**
    * 学生表
    * @author yu_chen
    * @date 2019-11-15 15:06:43
    **/
    @Data
    @TableName("bs_student")
    public class Student extends BaseEntity implements java.io.Serializable{
    
    	private static final long serialVersionUID = 1L;
    
    
        /**
         * 
         */
        @TableId
        private Integer id;
        /**
         * 学生姓名
         */
        @TableField("name")
        private String name;
        /**
         * 学号
         */
        @TableField("num")
        private String num;
        /**
         * 创建时间
         */
        @TableField("create_time")
        private LocalDateTime createTime;
        /**
         * 更新时间
         */
        @TableField("update_time")
        private LocalDateTime updateTime;
    
    }
```
- #### dao文件
```
package com.zynn.count.dao;


/**
* @author yu_chen
* @date 2019-11-15 15:06:43
**/
public interface StudentMapper extends BaseMapper {


}

```
- #### Mapper文件
```
 
 
 

     
         
         
         
         
         
     

     
        id,name,num,create_time,update_time
     

 
```
- #### Service文件
```
package com.zynn.count.service;

import com.zynn.count.entity.Student;

/**
* @author yu_chen
* @date 2019-11-15 15:06:43
**/
public interface StudentService extends BaseService  {


}

```
- #### ServiceImpl文件
```
package com.zynn.count.service.impl;


/**
* @author yu_chen
* @date 2019-11-15 15:06
**/
@Service
public class StudentServiceImpl extends BaseServiceImpl  implements StudentService{


}

```
- #### Controller文件（一般用不上）
```
package com.zynn.count.controller;

import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.RequestMapping;

/**
* @author yu_chen
* @date 2019-11-15 15:06:43
**/
@Controller
@RequestMapping("student")
public class StudentController {


}
```

#### 有问题就留言吧！！


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)