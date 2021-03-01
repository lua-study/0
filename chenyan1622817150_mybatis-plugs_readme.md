# mybatis-plugs


![Image text](src/main/resources/mybatis-plugs-logo.png)
#### 介绍
1.对mybatis进行扩展增强

2实现mybatis的CRUD简化操作 不用在书写基本的增删改查sql 全部通过BaseMapper 实现
#### 软件架构
软件架构说明

1.不对mybatis做任何修改 只做mybatis的扩展增强

2.代码自动生成，根据表名可快速生成xxxMapper.java、xxxService.java、xxxServiceImpl.java、xxxController.java、xxxMapper.xml

3.增加swagger配置方便前台调用接口

4.增加logback日志记录系统运行情况 

5.增加druid数据源监控sql运行情况

6.本系统采用前后端完全分离的模式：前端采用vue.js框架 项目地址：https://gitee.com/wdyun/enhancevue

#### 安装教程

1. maven建立springboot项目
2. 加入依赖：
引入jar包
maven 方式

<![Image text](src/main/resources/maven.png)

gradle方式：
compile("com.enbatis:mybatis-plugs:1.0.4")

请关注maven仓库最新版本：https://search.maven.org/search?q=enbatis

3.新建springboot项目
4.修改yml文件配置mybatis

<![Image text](src/main/resources/use.png)


            
      
3. 建立mysql数据库

#### 使用说明

1. 配置资源文件appliication.yml
   ![Image text](src/main/resources/yarm.png)
2. 启动类加上mapper包的扫描
3. mapper继承BaseMapper、service继承BaseService
4. 启动启动类即可编程使用
5. 运行启动类MybatisPlugsApplication.java 在浏览器输入http://localhost:8080/swagger-ui.html#/即可查看swagger

6项目演示地址：http://www.enbatis.com/   用户名：admin  密码：111111
效果演示
   ![Image text](src/main/resources/login.png)


   ![Image text](src/main/resources/首页.png)
    
   
   ![Image text](src/main/resources/menu.png)
      
      
         






#### 参与贡献

1. Fork 本仓库
2. 新建 Feat_xxx 分支
3. 提交代码
4. 新建 Pull Request


#### 码云特技

1. 使用 Readme\_XXX.md 来支持不同的语言，例如 Readme\_en.md, Readme\_zh.md
2. 码云官方博客 [blog.gitee.com](https://blog.gitee.com)
3. 你可以 [https://gitee.com/explore](https://gitee.com/explore) 这个地址来了解码云上的优秀开源项目
4. [GVP](https://gitee.com/gvp) 全称是码云最有价值开源项目，是码云综合评定出的优秀开源项目
5. 码云官方提供的使用手册 [https://gitee.com/help](https://gitee.com/help)
6. 码云封面人物是一档用来展示码云会员风采的栏目 [https://gitee.com/gitee-stars/](https://gitee.com/gitee-stars/)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)