# ApiStarter

#### 项目背景

#### 项目介绍
基于SpringBoot的Java应用开发基础通用脚手架,包含
1. Restful Api框架封装
2. 基于Vue + Element Ui的PC端后台管理系统
    1. 后台用户管理
    2. 后台资源,角色,权限管理
3. 项目文档
    1. 项目部署文档
    2. 相关技术基础扩展文档

#### 项目目标
针对Java 服务器应用开发,降低学习成本,提高开发效率.

#### 系统架构图
![Image Text](./docs/imgs/ApiStarter.jpg)

#### 管理系统Demo
![Image Text](./docs/imgs/main.png)

#### 目录结构

```
ApiStarter
├─api-starter-admin 后台管理系统
│  ├─build  打包编译文件
│  ├─public 公共文件
│  └─src 资源文件
│      ├─api ajax api接口
│      ├─assets 
│      │  └─404_images 图片资源
│      ├─components 组件
│      │  ├─Breadcrumb
│      │  ├─Hamburger
│      │  └─SvgIcon
│      ├─icons 菜单图标
│      │  └─svg
│      ├─layout 布局文件
│      │  ├─components
│      │  │  └─Sidebar
│      │  └─mixin
│      ├─router 路由
│      ├─store Vue store
│      │  └─modules
│      ├─styles 全局样式文件
│      ├─utils 工具类
│      └─views 页面
│          ├─dashboard 主页
│          ├─login 登录页
│          └─system 后台页面
│              ├─resources 资源页
│              ├─roles 角色页
│              └─users 用户页
├─api-starter-admin-api 管理系统后端
├─api-starter-api api接口项目
├─api-starter-core 核心模块
├─api-starter-dao 数据访问模块
├─api-starter-service 业务模块
├─api-starter-util 工具模块
└─docs 
    └─guide 文档

```

#### 快速安装
```
1. 克隆项目到本地Ide
2. 安装数据库,更新application-dev/prod.yml数据源账号密码配置,导入/docs/init.sql文件,初始化数据库
3. 配置Maven环境,拉取jar包
4. 安装lombok插件,重启idea
5. 执行api-starter-admin-api目录下ApiAdminApplication类main函数,启动项目管理系统服务端
6. 安装node.js
7. 进入api-starter-admin目录,cmd命令行执行npm install
8. 执行 npm run dev 浏览器访问 localhost:9525访问后台管理系统
9. 执行api-starter-api目录下ApiApplication类main函数,启动restful Api服务端
10. 使用postman访问Api接口获得响应
```

#### [请求流程&技术扩展](./docs/guide/请求流程.md)

#### 软件环境
    
技术|描述|
---|---|
SpringBoot|项目框架
JWT|Token管理工具
Mybatis|持久层框架
Mysql | 数据库 
Maven | 项目构建管理
logback | 日志管理
PageHelper mybatis|分页插件

#### 开发工具及常用插件
```
1. idea
    1. lombok 代码简洁插件
    2. cloud toolkit 服务端一键部署插件
2. vscode
    1. ESLint 代码规范
    2. Vetur vue插件
    3. Beautify 保存代码自动格式化代码插件
    4. HTML Snippets 简化标签输入
    5. Chinese (Simplified) Language vscode汉化
```

#### Tomcat配置
```
本项目使用内置Tomcat,通过application.yml的server进行Tomcat相关配置
单实例单应用 (一个tomcat 一个web应用)				缺点:浪费资源
单实例多应用 (一个tomcat多个应用)					缺点:升级一个应用要挂掉整个Tomcat,维护麻烦
多实例单应用 (多个tomcat都部署一个应用)			缺点:某个应用升级失败会导致用户访问到不同的版本实例		nignx反向代理-->服务器安装OpenSSL模块实现Https协议
多实例多应用 (多个tomcat部署多个不同的应用)		    

配置名称                                        描述
server.tomcat.internalProxies                   正则表达式匹配可信IP地址。
server.tomcat.protocolHeader                    保持传入协议的报头，通常称为X-Forwarded-Proto
server.tomcat.protocolHeaderHttpsValue          协议值,指明是否开启SSL支持
server.tomcat.portHeader                        用于重写原始端口值的HTTP报头的名称X-Forwarded-Port
server.tomcat.remoteIpHeader                    提取远程IP的HTTP报头的名称。例如，`X-FORWARDED-FOR`
server.tomcat.basedir                           Tomcat的基本目录。如果未指定，则使用临时目录
server.tomcat.backgroundProcessorDelay          
server.tomcat.maxThreads                        最大工作线程数
server.tomcat.minSpareThreads                   最小工作线程数
server.tmocat.maxHttpHeaderSize                 HTTP消息报头的最大大小(以字节为单位）
server.tomcat.redirectContextRoot               是否将请求context重定向到其他PATH
server.tomcat.useRelativeRedirects              
server.tomcat.uriEncoding                       用于解码URI的字符编码
server.tomcat.maxConnections                    最大socket连接到tomcat的连接数
server.tomcat.acceptCount                       当前连接数超过maxConnections的时候，还可接受的连接数，即tcp的完全连接队列(accept队列)的大小.

TomcatWebServerFactoryCustomizer类实现了WebServerFactoryCustomizer-->实现了WebServerFactoryCustomizer
在TomcatWebServerFactoryCustomizer中进行了一系列的application.yml中Tomcat属性配置到程序配置的转化过程
```
    
    
#### SpringBoot配置文件加载顺序
```
1. 开发者工具 `Devtools` 全局配置参数;
2. 单元测试上的 `@TestPropertySource` 注解指定的参数;
3. 单元测试上的 `@SpringBootTest` 注解指定的参数;
4. 命令行指定的参数，如 `java -jar springboot.jar --name="Java"`;
5. 命令行中的 `SPRING_APPLICATION_JSONJSON` 指定参数, 如 `java -Dspring.application.json='{"name":"Java"}' -jar springboot.jar`
6. `ServletConfig` 初始化参数;
7. `ServletContext` 初始化参数;
8. JNDI参数(如 `java:comp/env/spring.application.json`)
9. Java系统参数(来源：`System.getProperties()`)
10. 操作系统环境变量参数;
11. `RandomValuePropertySource` 随机数，仅匹配：`ramdom.*`;
12. JAR包外面的配置文件参数(`application-{profile}.properties(YAML）`）
13. JAR包里面的配置文件参数(`application-{profile}.properties(YAML）`）
14. JAR包外面的配置文件参数(`application.properties(YAML）`）
15. JAR包里面的配置文件参数(`application.properties(YAML）`）
16. `@Configuration`配置文件上 `@PropertySource` 注解加载的参数;
17. 默认参数(通过 `SpringApplication.setDefaultProperties` 指定)   
数字小的优先级越高，即数字小的会覆盖数字大的参数值
```

#### 版本及更新信息
1. 版本: 0.1
    1. 前后分离
    2. 后端框架封装
    
2. 版本: 1.0
    1. 项目模块化
    2. 增加后台管理系统
    3. 进度: 开发中
### 开发者
推荐 : QQ群 : 546556883
1. 微信: weixin54321a
2. QQ: 735376047

### 鸣谢
本项目后台管理系统基于vue-admin-template开发,项目需要关注的技术栈包括
1. [vue](https://cn.vuejs.org/)
2. [vuex](https://vuex.vuejs.org/zh/)
3. [Vue Router](https://router.vuejs.org/zh/)
3. [element ui](https://element.eleme.cn/2.0/#/zh-CN)等
4. 如需前端学习文档,请移步[vue-admin-template](https://panjiachen.github.io/vue-element-admin-site/zh/guide/),特别感谢.

#### 特别鸣谢
感谢每一位浏览至此的小伙伴,无论是学习,还是基于项目二次开发,能为大家带来便利,便是本项目最大的价值.
如果在使用过程中有疑问或建议,欢迎微信,QQ,issue等任意方式提出,作者会及时解决并持续更新.

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)