#json4bean
---
超轻量级Json4Bean工具包(小于30k)，源码不依赖任何第三方jar包，可扩展

特点：

    超轻量级Json4Bean工具包(小于30k)，源码不依赖任何第三方jar包

方法与功能：

    JSON.writeBean方法(生成非赋值)
        根据传入json参数生成javaBean实体
        支持自定义生成javaBean包名
        支持自定义生成javaBean模式（嵌套内部类或外部类）
        支持自定义生成javaBean代码注释模板

    JSON.parseObject方法(赋值非生成)
        把Json字符串转为javaBean对象

    JSON.toJsonString方法
        把javaBean对象转为字符串


演示 DEMO
```
示例代码
package com.javaear.json4bean;

import com.javaear.test.Student;

import java.io.File;

public class Json4BeanTest {

    /* 测试json 数据 */
    static String data = "[{\n" +
            "  \"id\": 123,\n" +
            "  \"name\": \"张三\",\n" +
            "  \"firend\": {\n" +
            "    \"fid\": \"f123\",\n" +
            "    \"fname\": \"李四\"\n" +
            "  },\n" +
            "  \"subjects\": [\n" +
            "    {\n" +
            "      \"sid\": \"o123\",\n" +
            "      \"sname\": \"王五\"\n" +
            "    },\n" +
            "    {\n" +
            "      \"sid\": \"o124\",\n" +
            "      \"sname\": \"马六\"\n" +
            "    }\n" +
            "  ]\n" +
            "}]";

    public static void main(String[] args) {
        //JSON.setWriteMultiBean(true); //去掉此注释，生成javabean为多个对象，非内部类形式
        //默认生成内部类JavaBean，可以通过去掉上边一行注释选择非内部类形式
        writeBeanSimpleTest();
        writeBeanWithPackageNameTest();
        writeBeanWithPackageNameAndCodeTemplateTest();
        parseObjectTest();
        toJsonStringTest();
    }

    /**
     * 极简生成测试
     */
    public static void writeBeanSimpleTest(){
        JSON.writeBean(data, "Student");
    }

    /**
     * 附带pageckName生成测试
     */
    public static void writeBeanWithPackageNameTest(){
        JSON.writeBean(data, "Student", "com.javaear.test");
    }

    /**
     * 附带pageckName、注释模板、生成测试
     */
    public static void writeBeanWithPackageNameAndCodeTemplateTest(){
        JSON.setCodeTemplate(System.getProperty("user.dir") + File.separator + "json4bean/src/test/resources/code-template.txt");
        JSON.writeBean(data, "Student", "com.javaear.test", System.getProperty("user.dir") + File.separator + "json4bean/src/test/java/" + "com/javaear/test");
    }

    /**
     * 解析json字符串为bean测试
     */
    public static void parseObjectTest(){
        Student student = JSON.parseObject(data, Student.class);
        System.out.println(
                "id为："+student.getId()+
                "name为："+student.getName()+
                "firend name为："+student.getFirend().getFname()+
                "subject 2 sname为："+student.getSubjects().get(1).getSname());
    }

    /**
     * 解析bean为Json测试
     */
    public static void toJsonStringTest(){
        //调用parse方法赋值的对象
        Student student = JSON.parseObject(data, Student.class);
        //解析bean为字符串
        String str = JSON.toJsonString(student);
        System.out.println(str);
    }


}

生成效果
/*
 * Copyright 2016-2016 Javaear Group Holding Ltd.
 */
package com.javaear.test;

import java.util.List;

/**
 * @author aooer
 */
public class Student {
    private Long id;
    private String name;
    private Firend firend;
    private List  subjects;

    public static class Firend {
        private String fid;
        private String fname;

        /**
         * @return fid
         */
        public String getFid() {
            return this.fid;
        }

        /**
         * @param fid fid
         */
        public void setFid(String fid) {
            this.fid = fid;
        }

        /**
         * @return fname
         */
        public String getFname() {
            return this.fname;
        }

        /**
         * @param fname fname
         */
        public void setFname(String fname) {
            this.fname = fname;
        }
    }

    public static class Subjects {
        private String sid;
        private String sname;

        /**
         * @return sid
         */
        public String getSid() {
            return this.sid;
        }

        /**
         * @param sid sid
         */
        public void setSid(String sid) {
            this.sid = sid;
        }

        /**
         * @return sname
         */
        public String getSname() {
            return this.sname;
        }

        /**
         * @param sname sname
         */
        public void setSname(String sname) {
            this.sname = sname;
        }
    }

    /**
     * @return id
     */
    public Long getId() {
        return this.id;
    }

    /**
     * @param id id
     */
    public void setId(Long id) {
        this.id = id;
    }

    /**
     * @return name
     */
    public String getName() {
        return this.name;
    }

    /**
     * @param name name
     */
    public void setName(String name) {
        this.name = name;
    }

    /**
     * @return firend
     */
    public Firend getFirend() {
        return this.firend;
    }

    /**
     * @param firend firend
     */
    public void setFirend(Firend firend) {
        this.firend = firend;
    }

    /**
     * @return subjects
     */
    public List  getSubjects() {
        return this.subjects;
    }

    /**
     * @param subjects subjects
     */
    public void setSubjects(List  subjects) {
        this.subjects = subjects;
    }
}
```

### 功能
√表示已支持、×表示暂未支持
1. 根据json字符串生成javaBean对象√
2. 根据业务需要，后续会提供支持生成三种JavaBean选择
    - DTO 数据传输对象，多用于Api接口联调对接使用，对代码美化度、格式无硬性要求√
    - Model 数据模型，对Java开发者友好的字段排序方式√
    - DO 数据库持久层使用对象√
3. 代码模板支持，比如getter setter自定义注释，类注释等√
4. JsonArray生成JavaBean对象√
5. Json字符串json value为Null 生成提示检查是否有空值√
6. Json字符串内嵌的对象，生成多个独立的JavaBean√
7. 支持json字符串转javaBean对象(给已有的JavaBean对象复制)√
8. 支持javaBean对象转json字符串√

### 人群
1. 经常进行api接口联调对接的java开发者，由于接口提供者未提供sdk包，对接人员经常需要根据request、response的json示例去写javaBean，这种大量重复且枯燥的工作，完全可以用json4bean轻松搞定。 ^ _ ^

2.其他需要根据json生成javaBean的不明真相的吃瓜群众。 ^ _ ^



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)