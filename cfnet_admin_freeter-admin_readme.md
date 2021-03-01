 **飞特后台管理系统是接私活利器，企业级快速开发框架**
 
**项目说明** 

- 采用SpringBoot、MyBatis、Shiro、并整合了很多优秀的开源组如mybaits-plus、J2Cache。
- 有单独的后台，还有单独的接口框架，可以实现前后端分离协作开发，还有火爆的商场功能模块，jwt
- 提供了超级代码生成器，可以生成hibernate-validtor验证注解如非空字段的验证，swagger-ui注解，
多表分页查询sql,后端模块代码 （控制器 到 视图），移动端模块代码（接口）只需编写30%左右代码，
其余的代码交给系统自动生成，可快速完成开发任务。现已支持mysql、oracle代码生成。 
飞特的目标是接近人工智能。
- 支持MySQL、Oracle、SQL Server、PostgreSQL等主流数据库
- 支持j2cache 二级缓存
 

**具有如下特点** 
- 火爆的商场模块，后续会加入更多的商城模块
- 超级代码生成器，可直接生成到IDE中，eclipse和ij都可以
- 引入2Cache 是 OSChina 目前正在使用的两级缓存框架
- 灵活的权限控制，可控制到页面或按钮，满足绝大部分的权限需求
- 完善的部门管理及数据权限，通过注解实现数据权限的控制
- 完善的XSS防范及脚本过滤，支持白名单过滤,彻底杜绝XSS攻击
- 支持分布式部署，session存储在redis中
- 友好的代码结构及注释，便于阅读及二次开发
- 引入quartz定时任务，可动态完成任务的添加、修改、删除、暂停、恢复及日志查看等功能
- 页面交互使用layui,vue.js，极大的提高了开发效率
- 引入swagger文档支持，方便编写API接口文档

 

 **项目结构** 

:fa-minus: freeter-coding 
:fa-minus: freeter-admin 后台管理  
:fa-minus: freeter-common 公共模块 
:fa-minus: freeter-good 商品模块 
:fa-minus: freeter-user 会员模块 
:fa-minus: freeter-job  定时任务模块 
:fa-minus: freeter-api 移动端接口模块 
:fa-minus: freeter-generator 独立代码生成器模块 

  

 **商城模块** 

频道列表： 可以理解为一级分类， 特殊的分类 底下可以不挂分类也可以挂视频，图片等等。

商品分类：有两级分类  商品可以修改二级分类 一级分类可以修改 因为一级分类绑定了规格而二级分类没有。

商品规格： 可以设置通用规格 也可以与一级分类绑定设置规格。商品规格可以重置 可以删除

商品基础功能全部完成。

会员管理

 

 **技术选型：** 
- 核心框架：Spring Boot
- 安全框架：Apache Shiro
- 视图框架：Spring MVC
- 持久层框架：MyBatis
- 定时器：Quartz 2.3
- 数据库连接池：Druid
- 日志管理：logback
- 页面交互：layui
- 下拉框：bootstrap-select
- 文件上传：Bootstrap File Input
- 热部署 jrebel
- 验证框架 hibernate-validator
- mybatis加强工具 mybatis-plus  文档 http://mp.baomidou.com/#/?id=%E7%AE%80%E4%BB%8B
- 通用工具类 hutool 文档 http://hutool.mydoc.io/
- j2cache  https://gitee.com/ld/J2Cache
  

 **软件需求** 
- JDK1.8
- MySQL5.5+
- Tomcat8+
- Maven3.0+

 

 **本地部署**

1.git下载https://gitee.com/xcOschina/freeter-admin.git项目,完成后导入到ide中  
2.eclipse File import... Maven Existing Projects into Workspace 选择项目的根路径。 
3.IDE会下载maven依赖包，自动编译 如果有报错 请update project... jdk环境配置。 
4.执行doc/mysql-test.sql文件，初始化数据【按需导入表结构及数据】 
5.最后修改数据库连接参数,配置文件在src/main/resources/application.yml 
6.j2cache:
    config-location: /cache/j2cache-no.properties     
    open-spring-cache: true  

 :fa-star: j2cache-no.properties    就是不使用缓存  
 :fa-star: j2cache-redis.properties redis 使用二级缓存 
 :fa-star:j2cache-caffeine.properties 使用一级缓存 

7.在freeter-coding目录下，执行mvn clean install
 
8、如何运行
- Eclipse或IDEA运行AdminApplication.java，则可启动项目【freeter-admin】
- freeter-admin访问路径：http://localhost:8080/freeter-admin/index.html
- 账号密码：admin/admin

 

- Eclipse、IDEA运行ApiApplication.java，则可启动项目【freeter-api】
- freeter-api访问路径：http://localhost:8081/freeter-api/swagger-ui.html

 

- Eclipse、IDEA运行GeneratorApplication.java，则可启动项目【freeter-generator】
- freeter-generator访问路径：http://localhost:8082/freeter-generator


 

 
 
 **后端项目演示**
- 演示地址： 
47.106.39.83:8080/freeter-admin/login.htm 
- 账号密码：admin/admin

 **移动端接口项目演示**
- 演示地址： 
47.106.39.83:8081/freeter-api/swagger-ui.html 
 
 **超级代码生成器项目演示**
- 演示地址： 
47.106.39.83:8082/freeter-generator/#generator.html 
 



**如何交流、反馈、参与贡献？** 
- 开发文档：https://gitee.com/xcOschina/freeter-admin.git
- 官方免费QQ群：806251058   
- gitee仓库：https://gitee.com/xcOschina/freeter-admin.git
- github仓库：暂不考虑，支持国产
- 如需关注项目最新动态，请Watch、Star项目，同时也是对项目最好的支持
- 技术讨论、二次开发等咨询、问题和建议，请移步到官方免费QQ群，我会在第一时间进行解答和回复！
- 微信扫码并关注【飞特开源】，获得项目最新动态及更新提醒，暂未开放 
- 点击链接加入群聊【飞特开源技术交流】：https://jq.qq.com/?_wv=1027&k=5DJ0G9i

 
 
 

**代码生成器：**
![输入图片说明](http://img.cnadmart.com/20180621/9b7b21a26bb74536985b073488eae307.png "在这里输入图片标题")

 


**商城移动端接口：**
![输入图片说明](http://img.cnadmart.com/20180623/8ed6b37c0e354b219a76a2389fa733f5.png "在这里输入图片标题")
 

**商城后端：商城图片演示**
![输入图片说明](http://img.cnadmart.com/20180623/e1732d3dd44e4513a88cf4589b4960df.png "在这里输入图片标题")
 
![输入图片说明](http://img.cnadmart.com/20180623/87fc8c561d02475db2008b1bf6963cf0.png "在这里输入图片标题")
 

![商城图片演示](http://img.cnadmart.com/20180626/0ddb036d612f4271b59984543e7f9555.jpg "在这里输入图片标题")

![商城图片演示](http://img.cnadmart.com/20180626/6deb7f146d32440db019012f5475a3cd.jpg "在这里输入图片标题")

![商城图片演示](http://img.cnadmart.com/20180626/09e0f2cbe22943308e40f06286905d40.jpg "在这里输入图片标题")

 

**后端模块自动生成的实体类：**

    @TableName("cn_good") 
    @ApiModel(value = "Good")
    public class GoodEntity  implements Serializable {

	private static final long serialVersionUID = 1L;


	public GoodEntity() {
		
	}
	
	public GoodEntity(T t) {
		try {
			BeanUtils.copyProperties(this, t);
		} catch (IllegalAccessException | InvocationTargetException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
	}

	/**
	 * 商品ID
	 */
	
	@TableId 					
	@ApiModelProperty(value = "商品ID",hidden = true)
	private Integer goodId;
	
	/**
	 * 商品名称
	 */
				
	@NotBlank (message = "商品名称不能为空") 			
	@ApiModelProperty(value = "商品名称")
	private String goodName;
	

**mapper 有外键自动生成多表关联语句：**

` 
	
SELECT  student.* FROM t_student  student 			   
        left join t_professional  professional on  professional.professional_id = student.professional_id 		   
        left join t_school  school on  school.school_id = student.school_id         
          1=1 ${ew.sqlSegment} 
	 


特别鸣谢：

人人开源 / renren-generator

baomidou / mybatis-plus

 红薯 / J2Cache

![捐赠](http://img.cnadmart.com/20180621/f4bb4447a6894653b2da80fcd745390a.jpg "捐赠") 

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)