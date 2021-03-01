- 项目需打包成war部署到tomcat能够正常运行，jar会因为文件路径运行失败。
    - 使用外部Tomcat
        1. 修改 com/ajobs/yuns/YunsApplication.java
        2. 修改 pom.xml  
          ```
             
               org.springframework.boot 
               spring-boot-starter-web 
               
                 
                   org.springframework.boot 
                   spring-boot-starter-tomcat 
                 
               
             
           ```
         3. application.yml
            ```
              mvc:
                servlet:
                  path: /yuns/
            ```
      
- 修改分享文件的链接：
   代码在： resources/static/js/myResCmd.js 的第14行
   ```
  /**
   * 部署修改
   * @type {string}
   */
  var sharePageLink = 'http://localhost:8080/yuns/show/share.html';
  ```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)