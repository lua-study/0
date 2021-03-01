#oauth2-shiro-redis

 
  Integrate  oauth2-shiro  with  Redis 
 
 
    GitHub地址:  https://github.com/monkeyk/oauth2-shiro 
 


 
     说明 
     该项目具有  oauth2-shiro  的所有功能, 并添加了对 Redis 的支持 
     从 oauth2-shiro fork 的版本: 0.1-rc 
     项目使用的 Redis 版本信息
         
        spring-data-redis   -> 1.5.2.RELEASE
         
        jedis  ->  2.7.3
     

 


 
     功能变化 
     相比 oauth2-shiro 项目, 添加并支持更多的功能与配置 
     
          支持Redis连接属性更多的设置, 详见配置文件  resources.properties ,  authz.properties   
          提供对 ClientDetails 的操作支持, 详见  ClientDetailsService.java   
          重构 ClientDetails, 使其支持 序列化(Serializable)  
          添加配置属性  remove.token.expired , 支持当检测到 access_token 过期时删除对应的 AccessToken 数据  
          根据需要可去掉MYSQL数据库支持, 只使用Redis, 详见 branch:  redis   
          重构 OAUTH2 业务实现的代码, 使结构,代码更清晰, 可读更强  
     
 


 
     使用注意 
     authz 与 resources 模块中配置的 Redis 必须是同一个Redis的连接信息, 方可正常工作 
     在项目中,使用Redis做缓存, 提高性能,同时也将数据存入MYSQL数据库; 也支持去掉MYSQL,只使用Redis(需要修改配置实现) 

 


 
     Project Logs 
     记录项目的变化与发展历程 

     
          2015-10-21     从oauth2-shiro fork源代码到本项目中  
          2015-10-27     创建branch:  redis , 只支持Redis操作  
          2016-07-08     oauth2-shiro-redis 开源  
  2017-01-21     加入GitHub https://github.com/monkeyk/oauth2-shiro-redis  
     
 


 
     技术支持联系方式 
     Email:   sz@monkeyk.com 
 
 
     
 


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)