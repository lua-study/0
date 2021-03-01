# boot-master

#### 项目介绍
boot-master基于SpringBoot2.2.0版本，整合项目中常用技术,帮助您快速上手使用SpringBoot，欢迎大家提意见，您的宝贵意见，是我们进步的动力。
最新代码请查看[boot-win](https://gitee.com/bootstrap2table/boot_master/tree/feature/boot-win)  本地部署：&nbsp;[离线版本](http://106.12.24.186:8081/nexus/content/groups/public/com/qdone/swagger/1.0.0/swagger-1.0.0.jar).

 

#### 在线演示
[HAdmin演示](https://bootstrap2table.gitee.io)  &nbsp;[SOLR](http://106.12.75.109:8888/solr)  &nbsp;[WIN10演示](http://106.12.24.186:9090) &nbsp;[ZKUI演示](http://106.12.24.186:9999) &nbsp;[XXL_JOB](http://106.12.24.186:8484/xxl-job-admin)
#### 极速入门
[精简版本](https://gitee.com/bootstrap2table/boot_master/tree/feature/boot-single)   &nbsp;[入门配置](https://gitee.com/bootstrap2table/boot_master/wikis/welcome)   &nbsp;[分布式事务](https://gitee.com/bootstrap2table/boot_master/tree/feature/jta/druid)  &nbsp;[SpringCloud](https://gitee.com/bootstrap2table/spring-cloud)   &nbsp;[Dubbo](https://gitee.com/bootstrap2table/api-master)


#### 技术选型
    ● 系统核心框架：SpringBoot
    ● 定时任务调度：ElasticJob+Zookeeper
    ● 数据持久框架：MyBatis
    ● 数据库连接池：Alibaba Druid
    ● 系统监控插件：JavaMelody+Druid
    ● 系统缓存框架：Redis-cluster
    ● 系统前端框架：Freemaker+AdminLte
    ● 搜索引擎框架：Solr/SolrCloud+RedisSearch
    ● 分布式线程锁：Redisson
    ● 分布式限流器：Redisson
    ● 系统消息队列：ActiveMq
    ● 安全授权框架：JwtToken+AES 
    ● 接口文档工具：SWAGGER2+swagger2markup
    ● 全文检索工具：RedisSearch
    ● 日志查询处理：RediSQL
    ● 代码分析插件：Sonar
    ● 项目文件服务：Gitea
    ● 项目文档工具：Swagger+RAP
    ● 项目管理工具：禅道

 
#### **项目特点**  
> * 利用REDISSON实现多个服务之间的远程调用，发送方发送指令成功，接收方确认会处理。 
> * 用户操作日志写入REDIS，通过SWAGGER在线文档直接查看REDIS日志。 
> * http协议在线访问swaggerJSON地址，可以直接生成swagger离线makdown和html文档。  
> * 配置App模块，针对相同接口重复提交，直接拒绝访问(针对多读情况，可手动关闭限制)。 
> * 配置接口限流器，接口端直接拒绝超过允许数量的请求，减轻服务器端在高并发环境下的压力。 
> * 配置坦克大战小游戏，让您在学习之余可以愉快的放松休息。 
> * 配套[代码生成工具](https://github.com/apple987/AutoCode):快速生成前后端代码，极大的提高开发效率。 
> * 引入[ApacheCommons](https://gitee.com/bootstrap2table/boot_master/blob/master/src/test/java/com/qdone/DemoApacheCommonsTest.java)工具包，大幅简化开发中的io,file,collection,jexl等处理过程 。 
> * 引入APP模块，根据token作为登录令牌，支持token自动续期，极大的方便了APP接口开发。 
> * 引入[HibernateValidator](https://gitee.com/bootstrap2table/boot_master/blob/master/src/main/java/com/qdone/module/controller/TestController.java)校验框架，轻松实现后端校验。 
> * 引入druid,javaMelody监控系统各项指标，分析系统瓶颈。 
> * 前端采用freemarker模板化引擎,页面采用bootstrap-table灵活强大的表格插件。 
> * 前端使用layui弹出层框架，极大的简化了弹出层的开发过程。
> * 前端采用JqueryValidate插件,快捷方便进行数据验证。 
> * 后端配置swagger在线文档，极大的降低前后端项目成员的沟通成本，快速同步文档。  
> * 配置druid,fastjson,cors,xss,redis-cluster等组件服务。 
> * 配置全局异常处理，通用日志打印,pagehelper分页。 
> * 配置redisson集群模式,使用分布式锁，保证并发的数据一致性。 
> * 配置全局errorPage和welcomeFile完善全局异常处理，优化异常处理代码。 
> * 配置devtools热部署，针对page目录下的css,js,html页面资源修改之后，项目不需要重新启动。 
> * 配置elastic-job定时器，强悍的分布式定时任务配置。 
> * 配置fileupload(默认配置最大100MB)，下载文件，生成二维码，二维码打印，mail发邮件等功能。 
> * 配置https安全协议，提高系统安全性,配置log4j日志，系统出现异常自动发送邮件。 
> * 配置poi和csv简单导出excel功能点,poi目前是多sheet智能导出。 
> * 前端使用vkbeautify插件,页面格式化json,xml,css,sql数据显示。 
> * 配置[activeMq](https://gitee.com/bootstrap2table/boot_master/blob/master/src/test/java/com/qdone/DemoApplicationTests.java)支持同时发送队列和主题消息。 
> * 配置[solr和solrCloud](https://gitee.com/bootstrap2table/boot_master/blob/master/src/main/java/com/qdone/module/app/SolrDataController.java)支持分词搜索查询。 
> * 配置LOG4JDBC格式化打印Mybatis执行sql日志，快捷定位脚本错误 


#### **项目结构**
```
boot-master
│ 
├─doc  项目SQL语句
│ 
├─common 公共配置
│ 
├─framework 框架配置
│ 
├─modules 功能模块
│  ├─app API接口模块(APP调用)
│  ├─controller 系统模块
│  ├─mapper  mybatis的sql文件
│  ├─model   数据库实体类
│  └─service 业务逻辑层
│ 
├─StartUpApplication 项目启动类
│  
├──resources
│  ├─page 页面资源
│  │  ├─static 静态资源
│  │  │  ├─css  css样式
│  │  │  ├─js   js文件 
│  │  │  ├─images   图片文件 
│  │  │  ├─adminLTE 模板组件  
│  │  │  └─plugins  前端插件
│  │  │
│  │  └─view  前端页面
│  │     ├─error 系统错误页
│  │     ├─inc   公共资源页面
│  │     └─其他   系统功能页面
│  │
│  ├─application.properties 配置文件
│  ├─banner.txt  自定义启动图标
│  ├─mybatis_config.xml mybatis配置项
│  └─secure.jks  ssl安全证书
```
#### **软件环境** 
- JDK1.8
- MySQL5.5+
- Maven3.0+
 
#### **环境配置:** 
- 1.项目依赖redis-cluster集群,zookeeper,activeMq,solr工具,目前工具运行环境(win7 x64)。 
- 2.doc目录里面有初始化sql，运行项目前，请先创建mysql(编码UTF-8)。 
- 3.工具地址:https://pan.baidu.com/s/1Bm7udGJc40xEENFgnJjsIw
- 4.SolrCloud: https://pan.baidu.com/s/1RbC4zS8izz9Ge8wuIdplXQ
- 5.配置文档：https://gitee.com/bootstrap2table/boot_master/wikis/welcome
	 
#### **启动说明:**
- 1.创建mysql数据库isec实例,运行doc目录里面的sql文件。 
- 2.启动redis集群(127.0.0.1:6379~6384，密码:qdone)。 
- 3.启动activeMq(默认单机版)。 
- 4.启动solr(默认单机版)。 
- 5.启动zookeeper(默认单机版本2181)。 
- 6.运行StartUpApplication启动项目，浏览器访问http://localhost 
- 7.Sonar代码分析，请在eclipse或者idea工具： 
    maven命令:sonar:sonar -Dsonar.host.url=http://ip:port -Dsonar.login=X -Dsonar.password=X -Dsonar.scm.provider=git 
#### **注意事项：**
- 1.目前启动2台实例，发送队列消息时，存在一个队列对应多个消费者，某一消费者可能读取不到队列消息的情况。 
- 2.代码配置有通用和特定队列的两种监听器，当向相同队列发送消息时，专门监听该队列的监听器会处理此消息。 
- 3.开源分布式定时任务架构有很多，常用Elastic-job,XXL_JOB,light-task-scheduler。 
- 4.REDISSON可以做远程调用，发布订阅功能，可以实现类似MQ的轻量级功能。 
- 5.使用XXL-JOB时，需要在自己的业务方法里处理完毕之后，需要将handler异常抛出，便于admin捕获处理。 
- 6.系统风格有[AdminLTE](https://gitee.com/bootstrap2table/boot_master/tree/feature/boot-simple)和[Win10](https://gitee.com/bootstrap2table/boot_master/tree/feature/boot-win)两种，鉴于服务器原因，此处只是展示[Win10](http://106.12.24.186:9090)页面。 

#### **懒人部署:**
- 1.下载&nbsp;[swagger.jar](http://106.12.24.186:8081/nexus/content/groups/public/com/qdone/swagger/1.0.0/swagger-1.0.0.jar)
- 2.百度网盘[swagger.jar](https://pan.baidu.com/s/1yGzkIe4PG0-sAdUT0UCQ1w),提取码:jq7s
- 2.本地进入下载目录，执行:java -jar swagger-1.0.0.jar
- 3.浏览器访问:http://localhost:9090/main
	
#### **友情链接：**
- GitHub：https://github.com/apple987/boot_walk  
- mycat版本: https://gitee.com/bootstrap2table/boot_master/tree/feature/mycat 
- sharding-jdbc版本: https://gitee.com/bootstrap2table/boot-sharding 
- jtaDruid版本: https://gitee.com/bootstrap2table/boot_master/tree/feature/jta/druid 
- 代码生成： https://github.com/apple987/AutoCode 
- 阿里GTS： https://github.com/seata/seata 

#### **问题反馈：**
- 意见反馈：https://gitee.com/bootstrap2table/boot_master/issues
- 作者姓名：付为地 
- 作者QQ: 1335157415 
- 作者邮箱: m15171479289@163.com 
- 加入QQ群： 
![boot-qq](https://images.gitee.com/uploads/images/2019/0112/104238_654d4e4e_1006985.jpeg "QQ群") 

### 项目截图
**项目启动效果图：** 
![boot-start](https://images.gitee.com/uploads/images/2019/0112/104238_7ab41d58_1006985.png "项目启动") 	
**Https跳转效果图：** 
![boot-ssl](https://images.gitee.com/uploads/images/2019/0112/104238_658957a1_1006985.png "初始化") 
**登陆页面效果图：** 
![boot-login](https://images.gitee.com/uploads/images/2019/0112/104238_1fcc2e3c_1006985.jpeg "登陆页面") 
**欢迎页面效果图：** 
![boot-welcome](https://images.gitee.com/uploads/images/2019/0112/104238_2a1f82df_1006985.jpeg "欢迎页面") 
**学生管理效果图：** 
![boot-index](https://images.gitee.com/uploads/images/2019/0112/104238_174d64cf_1006985.png "学生管理") 
**接口文档效果图：** 
![boot-swagger](https://gitee.com/uploads/images/2019/0506/103033_adea4493_1006985.png "swagger在线文档") 
**登录接口效果图：** 
![boot-applogin](https://images.gitee.com/uploads/images/2019/0112/104240_b52faf90_1006985.jpeg "app登陆接口") 
**获取用户效果图：** 
![boot-appGetUser](https://gitee.com/uploads/images/2019/0506/103033_527e984d_1006985.jpeg "app获得登陆信息接口") 
**邮件异常效果图：** 
![boot-emailError](https://gitee.com/uploads/images/2019/0506/103032_351aaaea_1006985.jpeg "邮件发送异常") 
**发送消息效果图：** 
![boot-runmq](https://gitee.com/uploads/images/2019/0506/103032_fcf9f466_1006985.jpeg "发送MQ消息") 
**接收消息效果图：** 
![boot-mq](https://gitee.com/uploads/images/2019/0506/103032_b65dfcce_1006985.jpeg "MQ队列和订阅") 
**职员列表效果图：** 
![boot-selectStaff](https://gitee.com/uploads/images/2019/0506/103033_9f4be254_1006985.jpeg "职员信息列表") 
**添加职员效果图：** 
![boot-insertStaff](https://gitee.com/uploads/images/2019/0506/103033_bb7cd3c3_1006985.jpeg "添加职员信息") 
**验证失败效果图：** 
![boot-insertError](https://gitee.com/uploads/images/2019/0506/103033_fc1c8e91_1006985.jpeg "validate验证信息") 
**AlibabaDurid效果图：** 
![boot-durid](https://gitee.com/uploads/images/2019/0506/103034_9a0b2cde_1006985.png "durid监控") 
**JavaMelody效果图：** 
![boot-javaMelody](https://gitee.com/uploads/images/2019/0506/103034_87f896fc_1006985.png "javaMelody监控") 
**生成二维码效果图：** 	
![boot-qrcode](https://gitee.com/uploads/images/2019/0506/103034_519b6c5b_1006985.png "生成二维码") 
**打印二维码效果图：** 
![boot-print](https://gitee.com/uploads/images/2019/0506/103034_1427e1da_1006985.png "打印二维码") 
**Solr操作效果图：** 
![boot-solr](https://gitee.com/uploads/images/2019/0506/103036_948552a3_1006985.png "solr导入数据") 
**文本上传效果图：** 
![boot-upload](https://gitee.com/uploads/images/2019/0506/103035_df507501_1006985.jpeg "文本上传") 
**上传出错效果图：**
![boot-uploadError](https://gitee.com/uploads/images/2019/0506/103036_bc0b458c_1006985.jpeg "文件上传异常") 
**限流生效效果图：**
![boot-ratelimter](https://gitee.com/uploads/images/2019/0506/103036_7c0504a0_1006985.jpeg "限流接口请求") 

	

		
        

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)