#HeartBeat
 
     
     心跳检测应用服务器(如Tomcat,Jetty)的JAVA WEB应用程序.
     
     
     如何实现?
      
     使用HttpClient对指定的服务器(application-instance) URL 按频率(10秒,20秒...) 发起请求并记录响应的信息(连接耗时,是否连接成功,是否有异常,响应数据包大小),
     若检测到不正常(响应码不是200,抛出异常...)时则发送邮件给指定的地址,当检测恢复正常时也发送提醒邮件.
      
     将来会添加更多的实时提醒方式接口,如微信,短信
     
 

 
     框架及版本 
     
         Spring Framework - 3.2.2.RELEASE 
         Quartz - 2.2.1 
         Hibernate - 4.1.7.Final 
          Flat UI  
         Maven - 3.1.0 
     
 

 
     特点 
     
         无侵入 
         独立部署 
         可同时监测多个应用服务器 
         使用简洁,灵活 
         提醒方式及时,多样(目前仅实现邮件提醒,将来会加入微信提醒,短信提醒等) 
     
 

 
     运行环境 
     
         JRE 1.7 + 
         MySql 5.5 + 
         Tomcat 7 + 
     
 

 
     如何使用? 
     
         项目是Maven管理的, 需要在电脑上安装maven(开发用的版本号为3.1.0), MySql(开发用的版本号为5.5) 
         下载(或clone)项目到本地 
         
            创建MySQL数据库(默认数据库名:heart_beat), 并运行相应的SQL脚本(脚本文件位于others/database目录),
             
            运行脚本的顺序: HeartBeat.ddl -> quartz_mysql_innodb.sql
         
         修改HeartBeat.properties(位于src/main/resources目录)中的数据库连接信息(包括username, password等) 
         
            将本地项目导入到IDE(如Intellij IDEA)中,配置Tomcat(或类似的servlet运行服务器), 并启动Tomcat(默认端口为8080)
             
               另: 也可通过maven package命令将项目编译为war文件(HeartBeat.war),
                     将war放在Tomcat中并启动(注意: 这种方式需要将HeartBeat.properties加入到classpath中并正确配置数据库连接信息).
         
     
 

 
     Change-Log 
     
         
             
                2014-10-17   ----    Initial project
             
         
         
             
                2015-02-13   ----    Move development to  coding.net 
             
         
         
             
                2015-03-01   ----    Back to OSC and update documents; Add 0.1 branch
             
         
         
             
                2015-03-14   ----    Monitoring log add response data size;Add list of monitoring reminder logs; Update page styles; Add 0.2 branch
             
         
     
 


 
     程序运行主要截图 
     
         
             
                Monitoring
                 
                 
                 
             
         
         
             
                Instance - Monitoring details
                 
                 
                 
             
         
         
             
                Instance - Overview
                 
                 
                 
             
         
         
             
                Instance - Create
                 
                 
                 
             
         
         
             
                Monitoring-Log
                 
                 
                 
             
         
     
 




 
 
    More Open-Source projects see  http://andaily.com/my_projects.html 
     
    From  andaily.com 
     
    Email  monkeyk@shengzhaoli.com 
 

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)