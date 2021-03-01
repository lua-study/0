#HeartBeat
 
     
     心跳检测各类应用服务器(如Tomcat,Jetty),WEB服务器(如 Apache,Nginx) 的JAVA WEB应用程序.
     
     
     如何实现?
      
     使用HttpClient对指定的服务器(application-instance) URL 按频率(10秒,20秒...) 发起请求并记录响应的信息(连接耗时,是否连接成功,是否有异常,响应数据包大小),
     若检测到不正常(响应码不是200,抛出异常...)时则发送邮件给指定的地址,当检测恢复正常时也发送提醒邮件.
      
     将来会添加更多的实时提醒方式接口,如微信,短信
     
 

 
     使用的框架及版本 
     
         Spring Framework - 3.2.2.RELEASE 
         Quartz - 2.2.1 
         Hibernate - 4.1.7.Final 
         HttpClient - 4.3.5 
          Flat UI  
         Maven - 3.1.0 
     
 

 
     下载 
    从0.3版本开始, 每一个版本的下载文件都在项目的 'dist' 目录.
     
          HeartBeat-0.3.zip  
         最新版本下载:  HeartBeat-0.4.zip  
     
 

 
     特点 
     
         无侵入,独立部署 
         可同时监测多个应用服务器 
         请求方式支持GET,POST; URL支持http与https, 可指定请求content-type, 添加请求参数(固定参数或随机参数) 
         添加安全设置,可控制用户注册,设定用户权限等 
         使用简洁,灵活 
         提醒方式及时,多样(目前仅实现邮件提醒,将来会加入微信提醒,短信提醒等) 
     
 

 
     运行环境 
     
         JRE 1.7 + 
         MySql 5.5 + 
         Tomcat 7 + 
     
 

 
     在线测试 
     https://andaily.com/hb/ 
 

 
     如何使用? 
     
         项目是Maven管理的, 需要在电脑上安装maven(开发用的版本号为3.1.0), MySql(开发用的版本号为5.5) 
         下载(或clone)项目到本地 
         
            创建MySQL数据库(默认数据库名:heart_beat), 并运行相应的SQL脚本(脚本文件位于others/database目录),
             
            运行脚本的顺序: HeartBeat.ddl -> quartz_mysql_innodb.sql
         
         
            修改HeartBeat.properties(位于src/main/resources目录)中的数据库连接信息(包括username, password等)
             
             NOTE: 为了确保能收到提醒邮件,请将配置文件中的  mail.develop.address  配置为你的邮件地址;
            若在生产环境,请将  mail.develop.environment  值修改为 false (true表示为开发环境) 
         
         
            将本地项目导入到IDE(如Intellij IDEA)中,配置Tomcat(或类似的servlet运行服务器), 并启动Tomcat(默认端口为8080)
             
             
               另: 也可通过maven package命令将项目编译为war文件(HeartBeat.war),
                     将war放在Tomcat中并启动(注意: 这种方式需要将HeartBeat.properties加入到classpath中并正确配置数据库连接信息).
                      
                     或直接在项目的'dist'目录下载完整版安装包.
         
     

     
        注意: 由于昨天(2015-08-06)发现项目默认发送邮件地址no-reply-hb@andaily.com被人非法使用导致该邮箱被禁用了(因为安全检测发现非法的IP登录),若发现邮件发送不正常,
        请将默认的邮件地址配置修改为你自己的邮件配置信息(位于HeartBeat.properties文件中),不要再使用默认的no-reply-hb@andaily.com邮箱.
         
     
 



 
     邮件配置说明 
     
        HeartBeat项目使用的邮件服务器使用SSL连接, 所以在配置邮件(javaMailSender, HeartBeat.xml文件)时, 使用了SSL连接配置,包括 mail.smtp.auth 与 mail.smtp.socketFactory.class ;
         
        若在使用中配置邮件后不工作, 请检查配置(如使用的邮件服务器是否支持SSL)并编写单元测试来测试邮件发送能正常工作(项目的邮件单元测试在 MailTransmitterTest.java 文件中,
        记得将测试的emailAddress设置为自己邮箱).
         
         另:  强烈建议使用SSL连接邮件服务器 
     
     
        在项目的配置文件 HeartBeat.properties 中, 可配置邮件为开发环境或生产环境,具体参数为 mail.develop.environment 
        与 mail.develop.address , 若将 mail.develop.environment  = true为生产环境, false为开发环境; 开发环境时的邮件只为
        发给 mail.develop.address 配置的邮箱,不会发给真正的邮件接收者; 生产环境时 mail.develop.address 配置不启作用.
     
 


 
 开发计划 
 
从 0.5版本开始将项目的所有计划的开发内容列出来, 方便大家跟进, 也欢迎你加入.
 
项目的开发管理使用开源项目  andaily-developer .
 
 
        
             
                Version:  0.5  [planning]
                 
                Date: ------
             
             
                  (70) - Why set archived = 1 in mysql application_instance table(Fix issue #6)  
                  (83) - 对于注册的用户, 登录后只能管理自己 创建的instances  
                  (112) - #12 请求参数BUG(设置Url参数时未进行非空验证)  
                  ......  
             
        

 
 


 
     Change-Log 
     
         
             
                2014-10-17   ----    Initial project
             
         
         
             
                2015-02-13   ----    Move development to  coding.net 
             
         
         
             
                2015-03-01   ----    Back to OSC and update documents; Add 0.1 branch
             
         
         
             
                2015-03-14   ----    Monitoring log add response data size;Add list of monitoring reminder logs; Update page styles; Add 0.2 branch
             
         
         
             
                2015-03-15   ----    0.3 branch is developing
             
         
         
             
                2015-04-02   ----    Add 0.3 branch and publish it
             
         
         
             
                2015-04-06   ----    0.4 branch is developing
             
         
         
             
                2015-05-01   ----    Publish 0.4 version
             
         
     
 


 
     程序运行主要截图 
     
         
             
                Monitoring
                 
                 
                 
             
         
         
             
                Instance - Monitoring details
                 
                 
                 
             
         
         
             
                Instance - Overview
                 
                 
                 
             
         
         
             
                Instance - Create
                 
                 
                 
             
         
         
             
                Monitoring-Log
                 
                 
                 
             
         
         
             
                Monitoring-Reminder-Log
                 
                 
                 
             
         
         
             
                Search
                 
                 
                 
             
         
     
 


 
 
     相关链接 
     
          应用服务器心跳检测 Java HeartBeat  
          心跳检测服务器是否正常的开源项目  
     
 

 
 
    More Open-Source projects see  http://andaily.com/my_projects.html 
     
    From  andaily.com 
     
    Email  monkeyk@shengzhaoli.com 
 

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)