# base4web

#### 项目介绍
基于springBoot的可依赖web项目（Java8 + springBoot2.0）

#### 软件架构
软件架构说明


#### 安装教程

0.开发环境使用UTF-8编码

1.clone

2.运行数据库初始化sql（resources/sql/baseframework.sql）

3.修改配置文件数据库连接信息

4.确认本地redis已安装,修改对应的配置文件密码（必须有密码，因为设置中发送了AUTH（authentication，身份验证）请求）

5.初始用户admin 密码 mima123?

#### 使用说明

1.redis缓存，使用注解形式，另外可以注入JedisService做自定义缓存操作
    
    1、JedisService注入说明
       JedisService有两个实现分别是JedisServiceImpl和JedisClusterServiceImpl
       单机时使用 @Autowired
                @Qualifier("JedisServiceImpl")
       
       集群时使用记得去掉com.base.web.core.util.jedis.impl.JedisClusterServiceImpl类上面的注解的注释
        注入时使用 @Autowired
                 @Qualifier("JedisClusterServiceImpl")
                

    2、注解使用说明
    
       通用属性解释：
          value属性：要使用缓存的名称
           key属性：使用SpEL表达式自定义缓存Key，
          例如：#name—以参数name作为自定义缓存Key，
               #result.name—以返回值结果的name属性作为自定义缓存Key
               #p0" 指定传入的第一个参数作为定义缓存Key

       CacheConfig（cacheNames = "users"）注解在类上，统一该类下的缓存名字为"users"

       Cacheable 方法级注解，将查询结果缓存到redis中，如果没有缓存则会执行方法并将返回值缓存，如果有缓存时，不会执行方法而是直接返回缓存中的值

       CachePut 方法级注解，不管有没有缓存都会执行方法并将结果缓存起来（用于更新缓存）

       CacheEvict 方法级注解，指定key，删除缓存数据，allEntries=true,方法调用后将立即清除缓存

2.通用mapper代码生成插件使用说明

    1、修改generatorConfig.xml数据库连接信息
    
    2、修改generatorConfig.xml实体类、dao层、xml文件位置

    3、修改generatorConfig.xml表名和实体类名

    4、idea使用右边maven工具找到插件中的mybatis-generator,双击运行，eclipse自行百度

    5、service依赖该接口就可以实现对单表基本的增删改查操作，复杂操作写法和写原始mybatis一样，添加方法和xml文件的实现即可

    6、实体类 的类型规范要求

         1、表名默认使用类名,驼峰转下划线(只对大写字母进行处理),如UserInfo默认对应的表名为user_info。

         2、表名可以使用@Table(name = "tableName")进行指定,对不符合第一条默认规则的可以通过这种方式指定表名.

         3、字段默认和@Column一样,都会作为表字段,表字段默认为Java对象的Field名字驼峰转下划线形式.

         4、可以使用@Column(name = "fieldName")指定不符合第3条规则的字段名

         5、(重点)使用@Transient注解可以忽略字段,添加该注解的字段不会作为表字段使用.

         6、建议一定是有一个@Id注解作为主键的字段,可以有多个@Id注解的字段作为联合主键.

         7、默认情况下,实体类中如果不存在包含@Id注解的字段,所有的字段都会作为主键字段进行使用(这种效率极低).

         8、实体类可以继承使用,可以参考测试代码中的tk.mybatis.mapper.model.UserLogin2类.

         9、由于基本类型,如int作为实体类字段时会有默认值0,而且无法消除,所以实体类中建议不要使用基本类型.


3.通用service使用说明（实体类需要满足上述类型规范要求）

    1、com.base.web.core.basic.service.Demo 自定义接口使用例子

    2、com.base.web.core.basic.service.ImplDemo 自定义接口实现使用例子

    3、com.base.web.core.basic.service.NoInterfaceDemo 不需要写接口的service层例子

4.多数据源使用说明（Spring Boot 2.X 版本不再支持配置继承，多数据源的话每个数据源的所有配置都需要单独配置，否则配置不会生效）

    1、在配置文件中配置数据源信息，参考本项目的master与cluster的配置格式（目前未使用cluster数据源）

    2、在com.base.web.dao中添加一个新的包作为新数据源dao层的包，每个数据源有独立的dao层接口
    
    3、在com.base.web.model中添加一个新的包作为新数据源实体类的包

    4、resources/mappers下添加对应的xml文件包

    5、编写数据源配置类，参考com.base.web.core.config.datasource.MasterDataSourceConfig，注意该类中的@Primary注解在新的数据源中不用添加

 
5.shiro开关及路径拦截配置说明

    1、shiro开关，配置文件中shiro-filter.use字段用于配置是否使用shiro，使用时设置为true

    2、路径配置(配置顺序为最终过滤器的顺序)

         配置文件中编写多个shiro-filter.filters.***.urls属性，其中*** 为过滤器名称，字段值为需要过滤的url，多个路径用逗号分隔
   
6.Swagger2使用说明(建议结合restful使用,restful规范自行百度)

    1、在配置文件中修改文档信息的相关配置
    
    2、所有接口建议写在com.base.web.restful.controller目录下
    
    2、在对应controller上添加注解（例子:com.base.web.restful.controller.RestfulApiController）
    
    3、常用注解使用说明(需要用到其他到可自行百度)
         
         @Api：用在请求的类上，表示对类的说明
             tags="说明该类的作用，可以在UI界面上看到的注解"
             value="该参数没什么意义，在UI界面上也看到，所以不需要配置"
          
         @ApiOperation：用在请求的方法上，说明方法的用途、作用
             value="说明方法的用途、作用"
             notes="方法的备注说明"
          
         @ApiParam 该注解用在方法的参数中
             name="参数名称"
             value="参数值"
             required="是否必须，默认false"
             defaultValue="参数默认值"
             type="参数类型"

7.kafka使用说明

    0、配置文件中修改kafka代理地址

    1、注入KafkaProducer,调用send方法即可向kafka推送消息
    
    2、在com.base.web.core.util.kafka.KafkaConsumer为不同主题添加不同的消费者逻辑      

8.生成可依赖jar包说明

    -1、注释application.properties中到配置文件选择(也可不注释,新项目中可写相同配置覆盖)，调试时不注释

     0、修改打包方式为jar,调试时设置为war

     1、打包设置，pom文件中已设置，可跳过（查看隔壁那个生成可依赖jar.txt）

     2、运行install将模块安装到本地maven库（打包时运行package）

     3、新建一个war包类型的springBoot Web项目，删除新建项目的启动类,依赖该项目jar，保存springBoot parent以及test依赖，删除其他依赖
     
     4、新项目的包结构必须与该项目一致，将com.base.web作为根路径，才能被扫描到

     5、新项目如果使用单元测试需要引入spring-boot-starter-test依赖并使用@SpringBootTest(classes = MainApplication.class)，MainApplication为本项目启动类
    
     6、将该项目配置文件拷贝到新项目中，做个性化配置(不做新配置可不拷贝)

     7、新环境使用该项目resources/sql中的sql文件初始化数据库
     
     8、新增业务需要在com.base.web下新建业务包存放该业务的controller和service层（否则无法记录日志）
        
        1、若数据源与该项目相同则
            com.base.web.dao.master下新建对应的包放mybatis接口
            com.base.web.model.master下新建对应的包放实体类
            resources/mappers/master下新建对应的包放xml文件
        
        2、若数据源与该项目不同
            com.base.web.dao,com.base.web.model,resources/mappers下仿照master创建文件夹放对应文件
     
     9、新项目如果要使用通用mappr生成插件
          1、将本项目的resources/generatorConfig.xml拷贝到新项目中
          2、将本项目pom文件中的插件配置拷贝到新项目中
         
     10、本项目已引入layui相关资源，并进行了部分封装，新项目中可直接使用，使用方法与本项目相同
     
     11、启动新项目,运行成功则可开始新项目的开发之旅

    



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)