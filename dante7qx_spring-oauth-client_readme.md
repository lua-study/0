#spring-oauth-client

 
  spring-oauth-client depend on  spring-oauth-server ,
  it is the oauth2 client demos.
 

 


项目用Maven管理


使用的技术与版本号
 
      JDK (1.7.0_40) 
      Spring (4.1.6.RELEASE) 
      Spring MVC (4.1.6.RELEASE) 
      HttpClient (4.3.5) 
      json-lib (2.4) 
      Log4j (1.2.14) 
 
前端使用的技术与版本号
 
     Angular-JS (1.1.5) 
     Bootstrap (3.3.4) 
 
 

 
    Oauth服务端项目请访问  spring-oauth-server 
 
 
    在线测试地址  https://andaily.com/spring-oauth-client/ 
 

 
 
     如何使用? 
     
    前提: 在使用之前必须保证 spring-oauth-server 项目已正常运行.
     
         
            项目是Maven管理的, 需要本地安装maven(开发用的maven版本号为3.1.0)
         
         
             下载 (或clone)项目到本地
         
         
            修改 spring-oauth-client.properties (位于src/main/resources目录)中的配置信息(主要包括与spring-oauth-server的连接地址)
         
         
            将本地项目导入到IDE(如Intellij IDEA)中,配置Tomcat(或类似的servlet运行服务器), 并启动Tomcat(默认端口为8080) ,通过浏览器访问即可.
             
            注意将项目的 contextPath(根路径) 设置为 'spring-oauth-client'.
             
            所有的操作说明都在页面上体现.
             
               另: 也可通过maven package命令将项目编译为war文件(spring-oauth-client.war),
                     将war放在Tomcat中并启动(注意: 这种方式需要将spring-oauth-client.properties加入到classpath中并正确配置)
         
         
             
                若在 Android 中使用, 可查看示例代码  AndroidClientTest.java (位于  src/master/src /test /java /com/andaily/springoauth/client/ 目录).
                里面包括获取 access_token 与 调用API的示例.
             
         
     
 


 
 
     实现思路 
     
        spring-oauth-client 的实现没有使用开源项目  spring-security-oauth2  中提供的代码与配置, 如: &lt;oauth:client
        id="oauth2ClientFilter" /&gt; 
     
     
        而是按照Oauth2协议支持的5类grant_type依次去实现.
         
         
              authorization_code  -- 授权码模式(即先登录获取code,再获取token) 
              password  -- 密码模式(将用户名,密码传过去,直接获取token) 
              client_credentials  -- 客户端模式(无用户,用户向客户端注册,然后客户端以自己的名义向'服务端'获取资源) 
              implicit  -- 简化模式(在redirect_uri 的Hash传递token; Auth客户端运行在浏览器中,如JS,Flash) 
              refresh_token  -- 刷新access_token 
         

     
 

 
    项目的开发管理使用开源项目  andaily-developer .
 
 

 
     项目日志 
     
         
             2015-03-17    项目创建 
         
         
             2015-06-02    V-0.1版本发布 
         
         
             2015-11-16    添加在线测试, 访问地址 https://andaily.com/spring-oauth-client/  
         
     
 

 
 
     参考资源 
     
    以下是在开发与学习过程中参考的Oauth资源,总结下来方便学习回顾.
     
          
             OAuth2：Authorization Flows 
          
          
             OAuth2：隐式授权（Implicit Grant）类型的开放授权 
          
          
             oauth2.0协议之Implicit grant模式解析 
          
     
 

 
 
    与项目相关的技术文章请访问  http://andaily.com/blog/?cat=19  (不断更新与Oauth相关的文章)
 
 
     问答与讨论 
     
    与项目相关的，与Oauth相关的问题与回答，以及各类讨论请访问 
     http://andaily.com/blog/?dwqa-question_category=oauth 
 

 
 
 关注更多我的开源项目请访问  http://andaily.com/my_projects.html 
 
 
 若需更多的技术支持请联系  monkeyk@shengzhaoli.com 
 

 
 
  Expect your joining...
 

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)