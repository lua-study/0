#  **emsite-parent**  【技术QQ群：456742016】
### 框架简介

- emsite框架是基于众多优秀的开源项目，高度整合封装而成的高效，高性能，强安全性的开源Java EE分布式全自动快速开发框架平台。
  系统自带全自动增量发版功能.
- emsite目前包括以下五大模块，系统管理（SYS）模块、代码生成（GEN）模块、全自动增量发版（PATCH）模块、运营日志分析模块（规划中）、系统监控预警模块（规划中）
### 
    1、系统管理模块，包括组织架构（用户管理、机构管理、区域管理）、菜单管理、角色权限管理、字典管理等功能； 
    2、代码生成模块，完成重复的工作；
    3、全自动增量发版，轻松完成版本快速迭代;
- emsite框架拥有 **全自动增量发版子项目模块** [emsite-patch],该模块可以对git/svn管理的项目进行增量代码生成用于增量发版。总共包含四种生成方案：
### 
    1、git服务器分支提交分析；
    2、git提交日志分析；
    3、svn服务器分支提交分析；
    4、svn提交日志分析；
### 框架规划   
- emsite采用dubbo作为服务层框架，后台将集成单点登录、oauth2.0、storm+kafka消息处理系统、kafka+flume+storm+hdfs+hadoop作为日志分析系统、配置中心、分布式任务调度系统、服务器实时监控系统、搜索引擎系统(elasticsearch)，各大功能将作为模块化集成到本项目。
- emipre团队后期两款产品：
###
    1、在线客服开源系统；
    2、统一微信公众号管理平台；

### emsite生态圈
    01、emsite框架（独立主分支master）
    02、emsite微信公众号管理平台（独立分支wxdev）
    03、emsite在线客服开源系统(独立项目:[emipre-ons-talk-parent](https://gitee.com/hackempire/empire-ons-talk-parent))
    04、emstie框架springboot+springcloud版本（独立项目：[emsite-cloud](https://gitee.com/hackempire/emsite-cloud)）
    05、emsite框架soa框架（独立项目，远程RPC服务框架【服务熔断、降级、限流、异步、分布式、全链路监控】）
    06、增量部署项目,支持git/gitee/svn（独立项目:[patch-generator](https://gitee.com/hackempire/patch-generator-parent)）
    07、增量部署桌面版项目,支持git/gitee/svn（独立项目:[patch-generator-desk](https://gitee.com/hackempire/patch-generator-desk)）
    08、全能监控项目地址（独立项目:[omnipotent-monitoring](https://gitee.com/hackempire/omnipotent-monitoring)）
    
### 框架调整计划表【欢迎有志者加盟】
**一阶段：** 

    01、文档整理更新,数据库初始化excel和emsite-mysql.sql脚步同步更新[2018-02-07---2018-02-11]----已完成
    02、JavaMelody和druid监控的分布式支持扩展[2018-02-07---2018-02-22]----执行中(ing)
    03、代码优化之vo、dto层分离[2018-02-23---2018-03-10]----已结束
    04、poi文件导出、导入优化解耦[2018-03-06---2018-03-15]----延期执行
    05、分布式任务调度系统集成[2018-03-01---2018-03-05]----延期执行
    06、kafka+flume+storm+hdfs+hadoop日志分析系统模块功能开发、当前日志系统架构优化[2018-03-13---2018-04-01]----延期执行
    07、框架部署结构动静分离调整[ngnix+httpd]，框架文件系统图片资源服务器架构调整[fastDFS][2018-04-01---2018-04-10]----延期执行
    08、增量部署系统模块开发【SVN增量方案、GIT增量方案】----已完成
    09、Apache ActiveMQ/Apache RocketMQ内部消息系统集成
    10、emsite框架配置优化，集成配置中心
    11、cas单点登录、jwt权限集成
    12、微信公众号第三方平台基础功能开发（公众号管理、自定义菜单管理、粉丝管理、群发管理、素材管理）----计划执行
    13、微信接口调用监控功能开发
    14、在线客服开源系统
        a.openfire+smack+微信h5+swing/javafx(待定)+sip服务器集成(待定)+软硬电话集成+智能机器人
        备选技术：
        xmpp:Jabber、openfire
        sip：Asterisk、Cipango、FreeSwitch、SIPServer2008、opensips、Kamailio、OpenSER、sipXecx、miniSipServer、Brekeke、
                 GNU SIP Witch、Mobicents、Mysipswitch、SailFin、SIP Express Router、sipX、Yate、YXA
        智能机器人：图灵机器人、百度AI机器人、青云客智能聊天机器人
    15、微信公众平台插件开发（大转盘、在线门店、微信论坛、微信商城）
    16、Solr/Elasticsearch搜索引擎系统集成
    17、Swagger2系统开放Api接口文档测试系统集成
    18、系统架构部署文档、部署视频教程、wiki文档、系统模块分析文档完善等
    19、Jenkins持续集成方案整理
    20、远程RPC服务框架开发【服务熔断、降级、限流、异步、分布式、全链路监控】
    21、产品全线上线、开启框架培训社区、开启框架交流论坛
    22、springboot+springcloud框架版本开发----计划执行
    23、Mybatis分页插件PageHelper集成、分页功能解耦----已完成
    24、内容管理模块功能删除----已完成
 **二阶段** 

    25、emsite后台管理系统UI全新升级（备选方案：https://adminlte.io）
    26、前后端分离架构调整,框架版本2.0（node.js、bigpipe、KnockoutJS/AngularJS/vueJS/ReactJS待定）
    27、dao层优化，集成mybatis-plus----已搁置
    28、Activiti工作流+在线OA系统模块开发----已搁置
    
### emsite框架最新动态

    1.经项目组研究讨论，由于JavaMelody/druid等分布式扩展后只支持内外IP访问各台服务器，且如需要支持外网分布式监控，需要增加监        
      控域名和Nginx搭配，故该条规划已搁置，转由zabbix server、Tomcat-manager、lambda probe进行全方位监控，后期将开放以上三
      个监控方案的文档至项目QQ群；另外本项目后期将考虑jmx自建部分组件的监控体系,敬请期待[2018-02-18]
    2.重大喜讯：阿里巴巴已将dubbo项目已正式成功捐献给apache基金会孵化，由于apache目前还没比dubbo更处理更有力的分布式服务框架
      (soa)，故预测dubbo将在不久成为apache顶级项目，且同spring cloud平分soa分布式服务的半壁江山[2018-02-18]
    3.重要通知：由于本次dto和vo层改造忘记拉分支，所以将会直接在主分支上进行，提交的代码皆为可允许的代码！如果想拉改造之前的代码
      请进入项目标签中下载[2018-03-08]
    4.最新通知：emsite-cloud项目正式立项（进入技术调研筹备阶段），将采用目前最火的技术springboot+springcloud来实现，项目地址
      https://gitee.com/hackempire/emsite-cloud[2018-03-08]
    5.经架构分析，后台管理系统部分不适合做dto层拆分.emsite架构将采用前后端架构分离，前台(如微信h5功能)使用dto层作为数据传输对象，
      后台(如微信的数据管理)采用之前的entity作为数据传输对象.另外前后台API隔离，前台部分新开发dubbo接口、dto等.[2018-03-20]
    6.框架完成升级到jdk1.8，spring4.2.2.RELEASE，maven打包插件升级到最新版本，全自动增量发版功能[2018-04-07]
    7.增量打包桌面版已开发完毕，正式发布版本2.0,请关注patch-generator-desk
      项目地址:https://gitee.com/hackempire/patch-generator-desk[2018-05-01]
### 内置功能

    1、用户管理：用户是系统操作者，该功能主要完成系统用户配置。
    2、机构管理：配置系统组织机构（公司、部门、小组），树结构展现，可随意调整上下级。
    3、区域管理：系统城市区域模型，如：国家、省市、地市、区县的维护。
    4、菜单管理：配置系统菜单，操作权限，按钮权限标识等。
    5、角色管理：角色菜单权限分配、设置角色按机构进行数据范围权限划分。
    6、字典管理：对系统中经常使用的一些较为固定的数据进行维护，如：是否、男女、类别、级别等。
    7、操作日志：系统正常操作日志记录和查询；系统异常信息日志记录和查询。
    8、连接池监视：监视当期系统数据库连接池状态，可进行分析SQL找出系统性能瓶颈。
 
### 为何选择emsite

    1、使用 Apache License 2.0 协议，源代码完全开源，无商业限制。
    2、使用目前主流的Java EE开发框架，简单易学，学习成本低。
    3、数据库无限制，目前支持MySql、Oracle，可扩充SQL Server、PostgreSQL、H2等。
    4、模块化设计，层次结构清晰。内置一系列信息管理的基础功能。
    5、操作权限控制精密细致，对所有管理链接都进行权限验证，可控制到按钮。
    6、数据权限控制精密细致，对指定数据集权限进行过滤，七种数据权限可供选择。
    7、提供在线功能代码生成工具，提高开发效率及质量。
    8、提供常用工具类封装，日志、缓存、验证、字典、组织机构等，常用标签（taglib），获取当前组织机构、字典等数据。
    9、兼容目前最流行浏览器（IE7+、Chrome、Firefox）。
    10、最流行的分布式解决方案。
    11、dubbo已正式进入apache基金会孵化，前程似锦，可以说已与spring cloud分别坐拥分布式服务框架的半壁江山.
### 技术选型
1、后端

    a、核心框架：Spring Framework 4.2.2
    b、分布式服务框架：dubbo2.5.8、dubbo-admin、dubbo-monitor
    c、分布式协调组件：zookeeper3.4.6
    d、服务跟踪：Hydra(京东)
    e、分布式配置：apollo（携程）/disconf（百度）/diamond（阿里）
    d、安全框架：Apache Shiro 1.2
    e、视图框架：Spring MVC 4.2.2
    f、服务端验证：Hibernate Validator 5.2
    g、布局框架：SiteMesh 2.4
    h、任务调度：Spring Task 4.2.2
    i、持久层框架：MyBatis 3.2
    j、数据库连接池：Alibaba Druid 1.0
    k、缓存框架：Ehcache 2.6、Redis
    l、日志管理：SLF4J 1.7、Log4j
    m、数据库管理工具(备份、初始化):dbunit（当前使用）、Flyway
    n、工具类：Apache Commons、Jackson 2.2、Xstream 1.4、Dozer 5.3、POI 3.9
    o、监控架构：zabbix server、Tomcat-manager、lambda probe、cat
    p、持续集成方案：Jenkins
2、前端

    a、JS框架：jQuery 1.9。
    b、CSS框架：Twitter Bootstrap 2.3.1（稳定后台，UI方面根据需求自己升级改造吧）。
    c、客户端验证：JQuery Validation Plugin 1.11。
    d、富文本在线编辑：CKEditor
    e、在线文件管理：CKFinder
    f、动态页签：Jerichotab
    g、手机端框架：Jingle
    h、数据表格：jqGrid
    i、对话框：jQuery jBox
    j、下拉选择框：jQuery Select2
    k、树结构控件：jQuery zTree
    l、日期控件： My97DatePicker
3、平台

    a、服务器中间件：在Java EE 5规范（Servlet 3.0、JSP 2.1）下开发，支持应用服务器中间件 有Tomcat 7+、Jboss 7+、
       WebLogic 10+、WebSphere 8+。
    b、数据库支持：目前仅提供MySql或Oracle数据库的支持，但不限于数据库，平台留有其它数据库支持接口， 你可以很方便
       的更改为其它数据库，如：SqlServer 2008、MySql 5.5、H2等
    c、开发环境：Jdk1.7+(默认jdk1.8)、（Eclipse Java EE 4.3|sts-3.6.2.RELEASE|myeclipse10）、Maven 3.2+、Git
### 安全考虑

    a、开发语言：系统采用Java 语言开发，具有卓越的通用性、高效性、平台移植性和安全性。
    b、分层设计：（数据库层，数据访问层，业务逻辑层，展示层）层次清楚，低耦合，各层必须通过接口才能接入并进行参数校
       验（如：在展示层不可直接操作数据库），保证数据操作的安全。
    c、双重验证：用户表单提交双验证：包括服务器端验证及客户端验证，防止用户通过浏览器恶意修改（如不可写文本域、隐藏
       变量篡改、上传非法文件等），跳过客户端验证操作数据库。
    d、安全编码：用户表单提交所有数据，在服务器端都进行安全编码，防止用户提交非法脚本及SQL注入获取敏感数据等，确保数据安全。
    e、密码加密：登录用户密码进行SHA1散列加密，此加密方法是不可逆的。保证密文泄露后的安全问题。
    f、强制访问：系统对所有管理端链接都进行用户身份权限验证，防止用户
    g、服务监控：系统采用dubbo的服务全链路监控技术、可以做到精准定位服务情况
### 快速体验

    a、具备运行环境：JDK1.7+、Maven3.2+（建议3.5.3）、MySql5+或Oracle10g+。
    b、下载emsite-parent项目，导入第三方ckfinder插件jar包到本地maven库
    c、修改src\main\resources\emsite.properties文件中的数据库设置参数。
    d、根据修改参数创建对应MySql或Oracle数据库用户和参数。
    e、新建数据库emsite[字符集utf8 -- UTF-8 Unicode，排序规则utf8-bin],运行db\init-db.bat脚本，即可导入表结构及演示数
       据(linux操作系统：在控制台中切换至项目根目录，运行命令：mvn antrun:run -Pinit-db);或者直接在数据库工具中运行emsite 
       web项目db目录下的emsite_mysql.sql文件。
    f、启动redis,zookeeper组件
    g、启动emsite-service-dbs数据服务层项目,使用eclipse maven启动命令:clean  tomcat7:run（校验：http://localhost:端口/emsite-    
       service-dbs出现HelloWorld页面）
    h、启动emsite web服务器项目，运行目录下bin\run-tomcat7.bat或bin\run-jetty.bat 或使用eclipse maven启动命令:clean 
       tomcat7:run（第一次运行，需要下载依赖jar包，请耐心等待，校验：http://localhost:端口/emsite出现后台登录页面）。
    i、最高管理员账号，用户名：emsite 密码：admin  
### 常见问题

    a、用一段时间提示内存溢出，请修改JVM参数：-Xmx512m -XX:MaxPermSize=256m
    b、有时出现文字乱码：修改Tomcat的server.xml文件的Connector项，增加URIEncoding="UTF-8"
    c、为什么新建菜单后看不到新建的菜单？因为授权问题，菜单管理只允许最高管理员账号管理（最高管理员默认账号：emsite密码：admin）。 
    d、第三方ckfinder导入方案[ckfinder包放在emsite项目下lib文件夹中]
       mvn install:install-file -DgroupId=com.ckfinder -DartifactId=ckfinder   -Dversion=2.3 -Dpackaging=jar -        
       Dfile=D:/thirdxsd/ckfinder-2.3.jar

       mvn install:install-file -DgroupId=com.ckfinder -DartifactId=ckfinderplugin-fileeditor -Dversion=2.3 -Dpackaging=jar -
       Dfile=D:/thirdxsd/ckfinderplugin-fileeditor-2.3.jar

       mvn install:install-file -DgroupId=com.ckfinder -DartifactId=ckfinderplugin-imageresize -Dversion=2.3 -Dpackaging=jar -    
       Dfile=D:/thirdxsd/ckfinderplugin-imageresize-2.3.jar

       mvn install:install-file -DgroupId=com.empire -DartifactId=patch-generator -Dversion=0.0.1-SNAPSHOT -Dpackaging=jar -    
       Dfile=D:/thirdxsd/patch-generator-0.0.1-SNAPSHOT.jar
    
    e、项目类文件报错或者jar包不存在
       解决方法:
       1.eclipse点击project->clean->选择emsite所有模块->ok 
       2.选择emsite-parent父项目->右键->debug as->maven -clean
       3.选择emsite-parent父项目->右键->debug as->maven -install
       4.选中报emsite其它jar模块引入失败的项目->右键->maven->update project->选中online、force Update of Snapshots/Releases、
         update project configuration from pom.xml、Refresh workspace resources from local filesystem、clean project等选项
         ->点击ok
       5.更新完成然后重复上面2、3步骤，问题解决
    f、maven报错Project configuration is not up-to-date with pom.xml错误解决方法(导入项目之后发现有一个如下的错误：Project     
       configuration is not up-to-date with pom.xml. Run project configuration)    
       update
       其实这个问题解决非常简单：
       在项目上右键——【Maven】——【Update Project Configuration……】
       这时会打开一个（Update Maven Dependencies）的对话框，然后勾选住出错的项目，点击Ok，这样就搞定了。
    g、dubbo服务链追踪与监控
       下载dubbo-monitor或dubbo-admin监控项目进行部署
    h、项目spring配置文件spring-context-dubbo.xml报错dubbo标签不支持,请用开发工具关联在emsite项目lib文件夹下面的dubbo.xsd.
    i、更换其它数据库需修改配置文件emsite.property中数据库连接配置,如果添加子项目模块并且修改为其它数据库，需要新建Global并且覆盖
       emsite-service-common-api中Global类的jdbcType方法用于支持数据库分页插件.
    j、项目启动报dubbo配置的service无法启动，删除emsite->webapp->web-info->classes文件夹下面的所有文件
    k、如果在jdk8中用maven-tomcat插件运行项目报无效的1.8目标，请在环境中M2_HOME为最新apache-maven-3.5.3，并且将eclipse中jdk配置
       Default VM agrments设置：-Dmaven.multiModuleProjectDirectory=M2_HOME

### 项目结构：
   
    01、emsite-parent----------------maven-parent模块            
    02、emsite-service-common-api----common-service-api
    03、emsite-service-common-dbs----common-service-dbs
    04、emsite-service-api-----------core-service-api
    05、emsite-service-dbs-----------core-service-dbs
    06、emsite-----------------------emsite-web后台管理
    07、emsite-patch-----------------emsite增量发版模块
   
    
### 运行效果： 
![输入图片说明](https://gitee.com/uploads/images/2018/0202/143744_7016b877_302505.png "QL_HX_CFH3XM9}}2O$4E5V9.png")
![输入图片说明](https://gitee.com/uploads/images/2018/0202/143757_4a2f2fbe_302505.png "{XI07R%C`~Z3]QW~W@@GV7R.png")
![输入图片说明](https://gitee.com/uploads/images/2018/0202/143805_b21e58a0_302505.png "BFQ4DY62930{X$`}B8CTX(W.png")
![输入图片说明](https://gitee.com/uploads/images/2018/0202/143814_657153ba_302505.png "A{VU)DC0ME4@T36M}(OV3VQ.png")
### 运行内存：
spring-tool-suite（sts开发工具）JVM配置如下：
```
     -vmargs
     -Dosgi.requiredJavaVersion=1.6
     -Xverify:none
     -Xms1536m
     -Xmx1536m
     -Xmn512m
     -XX:NewSize=512m
     -XX:MaxNewSize=512m
     -XX:PermSize=256m
     -XX:MaxPermSize=256m
     -XX:+DisableExplicitGC
     -Xnoclassgc
     -XX:+UseParNewGC
     -XX:+UseConcMarkSweepGC
     -XX:CMSInitiatingOccupancyFraction=85
     -XX:+PrintGCDetails
     -XX:+PrintGCDateStamps
     -Xloggc:d:/sts-3.6.2.RELEASE/gc.log
     -Dorg.eclipse.swt.browser.IEVersion=10001
     -Dcon.sun.management.jmxremote
```
1.emsite-service-dbs内存效果图：
![dbs内存图](https://gitee.com/uploads/images/2018/0208/193238_e6bde688_302505.png "Z6}5MTA7T])`LW}7ZHD]BAL.png")
2.emsite内存效果图
![输入图片说明](https://gitee.com/uploads/images/2018/0208/193337_aa42796e_302505.png "@%TMX_U@`ERWV9H1W{X@)7O.png")

### 增量打包：
![增量打包运行图](https://gitee.com/uploads/images/2018/0501/235404_6ab02b4a_302505.png "_BJ8NS6R@(3MWDPSPJ6MQ5U.png")

### 相关项目

1.  [前端模板AdminLTE](https://github.com/almasaeed2010/AdminLTE)
1.  [vue-element-admin](https://github.com/PanJiaChen/vue-element-admin)
1.  [分布式服务框架Dubbo](https://github.com/apache/incubator-dubbo)
1.  [Emsite-patch-generator](https://gitee.com/hackempire/patch-generator-parent)
1.  [Emsite-patch-desk](https://gitee.com/hackempire/patch-generator-desk)




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)