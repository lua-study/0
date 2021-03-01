 
   
    
   
 

 MyBatis-Plus 

 
  Born To Simplify Development
 

 
   
     
   

   
     
   
 

---

## What is MyBatis-Plus?

MyBatis-Plus is an powerful enhanced toolkit of MyBatis for simplify development. This toolkit provides some efficient, useful, out-of-the-box features for MyBatis, use it can effectively save your development time.

## Links

-   [Documentation](https://mybatis.plus)
-   [Samples](https://github.com/baomidou/mybatis-plus-samples.git)
-   [Showcase](https://github.com/baomidou/awosome-mybaits-plus)

## Features

-   Fully compatible with MyBatis
-   Auto configuration on startup
-   Out-of-the-box interfaces for operate database
-   Powerful and flexible where condition wrapper
-   Multiple strategy to generate primary key
-   Lambda-style API
-   Almighty and highly customizable code generator
-   Automatic paging operation
-   SQL Injection defense
-   Support active record
-   Support pluggable custom interface
-   Build-in many extensions

## Getting started

-   Create a basic Maven or Gradle spring boot project
-   Add MyBatis-Plus dependency
    -   Maven:
        ```xml
         
             com.baomidou 
             mybatis-plus-boot-starter 
             3.0.6 
         
        ```
    -   Gradle
        ```groovy
        compile group: 'com.baomidou', name: 'mybatis-plus-boot-starter', version: '3.0.6'
        ```
-   Modify mapper file extends BaseMapper interface
    ```java
    public interface UserMapper extends BaseMapper  {

    }
    ```
-   Use it
    ```java
    List  userList = userMapper.selectList(
            new QueryWrapper ()
                    .lambda()
                    .ge(User::getAge, 18)
    );
    ```
    SQL executed
    ```sql
    SELECT * FROM user WHERE age >= 18
    ```

## Reporting bugs


## License

MyBatis-Plus is under the Apache 2.0 license. See the [Apache License 2.0](http://www.apache.org/licenses/LICENSE-2.0) file for details.


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)