#springboot-activiti

###项目本地部署###
1. 进入项目根目录，执行`gradle build` 安装`spring boot`依赖
2. 安装`js`依赖: `npm install`
3. 执行`bower install` 安装`angular js`依赖
4. 执行`gulp serve` 编译前台页面
5. 打开 http://localhost:9001 进行访问

### 项目介绍
1. 后台框架基于Spring Boot，Spring Security
2. 工作流使用Activiti
3. 前台框架基于Angular js

### 注意事项
1. 项目分为测试环境和生成环境，在`application.yml`中配置`active: dev`或`active: prod`
2. 工作流Activiti没有创建自带的用户权限表，而是由我们自己创建用户权限视图，创建脚本在`import.sql`中
3. 项目首次启动时，`activiti.cfg.xml`中` `
value值应设为`true`,以后启动更改为`none`,否则会因activiti表已存在导致启动失败
4. 本项目是在jhipster项目基础上构建，具体可参考github：https://github.com/jhipster/generator-jhipster

###下面是项目部分截图
![screenshot 1](http://git.oschina.net/wyy396731037/springboot-activiti/raw/master/1.png "在线编辑流程图")
![screenshot 2](http://git.oschina.net/wyy396731037/springboot-activiti/raw/master/2.png "流程模板管理")
![screenshot 3](http://git.oschina.net/wyy396731037/springboot-activiti/raw/master/3.png "流程跟踪")
![screenshot 4](http://git.oschina.net/wyy396731037/springboot-activiti/raw/master/4.png "代办任务管理")


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)