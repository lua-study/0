#oauth2-shiro


整合 Apache Oltu  与  Shiro . 提供一个轻量的OAUTH2应用框架.

并根据不同的应用场景提供不同的实现(如web场景,移动设备).

该项目与 spring-oauth-server 实现相同的需求与场合.
只是在实现上使用的技术不同(spring-oauth-server使用Spring Security + spring-security-oauth2实现; oauth2-oltu实现);
相比spring-oauth-server, oauth2-oltu具有如下特点:

 
     
           更加透明  -- 每一步实现都有可以查看的, 更容易理解的源代码, 一目了然  
           更多的可自定义与可扩展  -- 不管是ERROR返回信息的内容或格式, 都可根据需要自定义, 对请求参数,处理细节等可添加更多的具体实现  
           可读性更强  -- 由于Shiro, Oltu 没有Spring Security,spring-security-oauth2 的门槛高, 所有代码都是常用的Controller或Java Bean实现各项业务, 更可读,更易于理解  
           模块化  -- 得益于Oltu的模块化设计, 将 authz ,  resources 分开成不同的模块, 使用时可根据实际需要将二者合并在一个项目中或拆分为不同的模块  
     
 

 
 OAuth2下一代身份认证授权协议OIDC实现:  MyOIDC  
 
 
     主要技术及版本 
    Spring -- 3.2.2.RELEASE
     
    oltu  -- 1.0.2
     
    shiro -- 1.2.3
     
    MySQL -- 5.6
 

 
     开发环境 
     
          JDK -- 1.7.0_40  
          Maven -- 3.1.0  
          MySQL -- 5.6.23-log  
     
 
 
 
     项目模块说明 
     oauth2-shiro项目使用模块化开发, 以实现"高内聚, 低耦合"目标, 更符合实际项目需要; 分为三个模块: authz, core 与 resources, 具体说明如下 
     
           authz  实现使用各类grant_type去获取token业务逻辑----获取access_token  
           core  将公共部分提取到该模块中, 减少重复代码, 保证一致性, 如定义ClientDetails, AccessToken;  authz, resources 模块都依赖于该模块  
           resources  资源管理模块,将受OAUTH保护的资源(URI)放在这里----使用access_token  
     
 


 
     在线测试 
     
           authz   http://andaily.com/authz/   
           resources   http://andaily.com/rs/   
     
 

 
     Redis版本 
     
           Redis + MySQL   https://github.com/monkeyk/oauth2-shiro-redis   
           Redis   https://github.com/monkeyk/oauth2-shiro-redis/tree/redis   
     
 


 
     如何使用 
 
 
    项目是Maven管理的, 需要本地安装maven(开发用的maven版本号为3.1.0), 还有MySql(开发用的mysql版本号为5.6)
 
 
     下载 (或clone)项目到本地
 
 
    项目由三个模块(core,authz,resources)组成, core是一个Java项目(jar), authz与resources是Java Web项目(.war)
 
 
    创建MySQL数据库(如数据库名 oauth2_shiro), 并运行相应的SQL脚本(脚本文件位于others/database目录),
     
    运行脚本的顺序: oauth2-shiro.ddl -> initial-db.ddl
 
 
    依次修改authz模块的配置文件authz.properties(位于模块的src/main/resources目录)与resources模块的配置文件resources.properties(位于模块的src/main/resources目录);
    修改配置文件中的数据库连接信息(包括username, password等), 都连接到数据库oauth2_shiro
 
 
将本地项目导入到IDE(如Intellij IDEA)中,配置Tomcat(或类似的servlet运行服务器), 并启动Tomcat(默认端口为8080);
 
注意将项目的 contextPath(根路径) 设置为 'os'.
 
   另: 也可通过maven package命令将项目编译为war文件(os.war), 注意编译时每个模块的pom.xml文件中配置的数据库连接信息, 可在Maven命令中添加 -Dmaven.test.skip=true 忽略测试;
         将authz模块与resources模块生成的war放在Tomcat中并启动(注意: 这种方式需要将 authz.properties与resources.properties 加入到classpath中并正确配置数据库连接信息).
 
 
    参考 oauth_test.txt (位于others目录)的内容并测试之(也可在浏览器中访问相应的地址,如: http://localhost:8080/os/).
 
 
 



 
 支持的 grant_type 
 
说明 oauth2-shiro 项目支持的grant_type(授权方式)与功能
 
      authorization_code  -- 授权码模式(即先登录获取code,再获取token) 
      password  -- 密码模式(将用户名,密码传过去,直接获取token) 
      refresh_token  -- 刷新access_token 
      implicit(token)  -- 简化模式(在redirect_uri 的Hash传递token; Auth客户端运行在浏览器中,如JS,Flash) 
      client_credentials  -- 客户端模式(无用户,用户向客户端注册,然后客户端以自己的名义向'服务端'获取资源) 
 



 
 开发计划 
 
从 0.2版本开始将项目的所有计划的开发内容列出来, 方便大家跟进, 也欢迎你加入.
 
项目的开发管理使用开源项目  andaily-developer .
 
 
    计划加入Spring-Boot的实现
 
 
        
             
                Version:  0.3  [pending]
                 
                Date: 2016-07-16 / ------
             
             
                   (152) - oltu版本升级到1.0.2 并完成测试.   
                  (153) - 尝试添加并实现OIDC在 oauth2-shiro中  
                   (161) - 增加必要的代码注释与配置注释, 更易理解   
                   implicit模式不需要带上client_secret   
             
             
        
        
             
                Version:  0.2  [finished]
                 
                Date: 2016-05-26 / 2016-07-03
             
             
                   (66) - 更新首页UI, 参照spring-oauth-server   
                   (67) - client details overview   
                   (68) - client details testing   
                   (69) - user add/edit, overview   
                   (70) - 添加API使用说明, 举例各个场景    
                   (71) - 发布到测试服务器    
                   (72) - resources模块更新UI说明    
             
             
        
 


 
 Project Log 
 
     
           2015-05-17      Initial project, start push code (private)  
           2015-07-16       oauth2-shiro项目开发状态(7月)   
           2015-09-06       oauth2-shiro项目开发状态(8月)   
           2015-09-06      项目由 私有 变为 开源, 开发 resource 模块  
           2015-09-26      版本0.1 开发完毕, 发布  0.1-beta  版本  
           2015-10-07      重构项目结构, 发布  0.1-rc  版本  
           2016-05-26      开始开发  0.2  版本  
           2016-07-02      添加在线测试环境  
           2016-08-17      发布  0.2  版本  
           2017-01-21       加入到GitHub中, Git@OSC地址: http://git.oschina.net/mkk/oauth2-shiro  
     
 



 

 
     项目动态 
     
           oauth2-shiro 0.1-rc 发布  2015-10-07  
           oauth2-shiro 0.1-beta 发布  2015-09-26  
           oauth2-shiro项目开发状态(8月)  2015-09-06  
           oauth2-shiro项目开发状态(7月)  2015-07-16  
     
 

 
 
     姊妹项目 
     
           spring-oauth-server  Spring Security与OAUTH2的完整整合项目  
           spring-oauth-client  Oauth 客户端(client)测试项目  
     
 



 
 
    与Oauth2相关的技术文章请访问  http://andaily.com/blog/?cat=19  (不断更新与Oauth相关的文章)
 
 
     问答与讨论 
     
    与项目相关的，与Oauth相关的问题与回答，以及各类讨论请访问 
     http://andaily.com/blog/?dwqa-question_category=oauth 
 

 
 
     捐助 
     
    支付宝: monkeyking1987@126.com (**钊)
     
    明瑞 -- 5元
     
    Triton -- 8.8元
     
    半个鼠标 -- 10元
 

 
 
 关注更多我的开源项目请访问  http://andaily.com/my_projects.html 
 
 
 若需更多的商业技术支持请联系  sz@qc8.com 
 或访问  http://monkeyk.com/kso/ 
 
 
     
 


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)