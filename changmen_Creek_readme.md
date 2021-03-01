# 写在前面的话
很高兴大家关注这个项目，这个项目可借鉴之处是它是一个企业级别的架构方案。但是任何东西都是要更新变化的，所以该项目中有很多点都已经无法满足眼前流行技术，所以下一步会对框架层面进行技术升级，但是总的架构思想是不会变的。架构如下：
前端：webpack+eggjs+vue全家桶+vant（移动端）+elementUI(PC端)
后端：springboot+mybatis+maven
数据库：mysql+redis+mongodb
部署：docker容器
项目已经在企业开发中，还是很稳定的，项目整理中，敬请期待哈！！
# 前言
Creek(小溪)-dam(水坝)不仅仅一个架构，而是整个开发体系，并且努力打造一套从 `前端自动化架构 - 后端分布式架构 - 企业级基础项目 - 全栈式自动化运维 - 系统监测` 的全方位企业级开发解决方案。（不是企业，我只是个人项目）

# 项目介绍
Creek-dam是提供一整套全栈架构方案，从前端基于nodejs整个自动化构建体系，到后端Java的分布式体系，再到python自动化运维平台，努力打造快速构建，前端分离，持续集成一键部署。 
技术体系如下： 
  （1）Creek是一套前端实现基于`nodejs+express+fis3+boostrap+Handlebars+jquery+seajs`实现了一整套架构体系。 
      企业级版本基于`nodejs+eggjs+webpack+vuejs`体系架构。  
  （2）dam是一套后端是基于sca规范SOA的分布式敏捷开发系统架构，框架使用了`SpringFramework+mybatis+mysql+redis`等常见后端技术 
  （3）nova是使用jdango搭建一套从项目打包及部署，服务平台日志监控，多应用及服务器管理，自动化构建系统的运维平台 
  （4）code-factory是一个代码自动生成项目
### 技术选型
（1）核心框架：Spring Framework 
（2）缓存：redis + ehcache 
（3）权限框架：Springscurity 
（4）视图框架：servlet 
（5）持久层框架：MyBatis  
（6）数据库：mysql  
（7）定时器：Quartz  
（8）前端web框架：jquery、bootstrap、seajs 、nodejs 、express，fis3,pm2,bower 
（9）移动端架构：nodejs 、express、fis3、vue（全家桶）
（10）运维平台：jdango,celery,fabric 
（11）周边技术：Sinopia，svn 
（12）自动化代码生成器：freemarker 

### 项目功能

（1）权限管理：在nodejs端封装权限creek-scurity组件,可控件菜单权限、按钮权限、机构部门权限（数据权限） 
（2）CAS单点登陆:在nodejs端封装权限creek-oss-client/creek-oos-server组件,实现多个系统统一登陆登出。 
（3）缓存：使用redis+ehcahe整合shiro自定义sessionDao实现分布式集群共享session，redis可采用单机方式，也可以集群哨兵模式。可以灵活的切换模式 
（4）支付：实现微信/支付宝/银联支付功能支付第三方公共平台 
（5）消息服务器：使用redis实现订阅/发布消息机制 
（6）短信：实现短信群发，可动态切换服务商，可动态定制相应短信模板短信第三方公共平台 
（7）微信：实现微信公共号管理，微信小程序管理等相关微信第三方公共平台 
（8）爬虫：集成Java比较流行两个爬虫框架 
（9）内容管理系统：可动态完成内容的添加、修改、删除、暂停、恢复及日志查看等功能 
（10）quartz定时任务：可动态完成任务的添加、修改、删除、暂停、恢复及日志查看等功能 
（11）Java-RPC：自己封装dam-ieds框架级别远程服务包，可以使用分布式部署 
（12）代码自动生成：使用freemarker生成前端后端项目 
（13）nova平台：项目打包及部署，服务平台日志监控，多应用及服务器管理，自动化构建系统环境
### 软件环境

（1）JDK1.8 
（2）MySQL5.7.17 
（3）Tomcat8.5 
（4）redis 3.07 
（5）mongodb 3.7.0 
（6）nginx 1.8.1 
（7）nodejs 4.5 
（8）express >4 
（9）Sinopia 私有npm中间件 
（10）bower+svn私有组件库 
（11）python 2.7.3 
（12）jdango 1.0.2 
（13）celery  
（14）gateOne(堡垒机)  
（14）elipse+vscode+pycharm(开发工具)
# 软件架构
## 整体架构体系
![整体架构体系](https://images.gitee.com/uploads/images/2018/0719/121026_a83f4154_346157.png "前后端架构图.png")
## 前端架构体系
### 前后端分离
![前后端分离](https://images.gitee.com/uploads/images/2018/0713/174104_f4f8573e_346157.png "1.png")
### 前端架构体系
![前端架构体系](https://gitee.com/uploads/images/2018/0624/214711_0571d11d_346157.png "creek大前端服务体系.png")
### 后端架构体系
![后端架构](https://images.gitee.com/uploads/images/2018/0713/180915_5c194c87_346157.png "微服务架构图.png")
## 版本发布流程图
### 前后端打包流程图
![前后端打包流程图](https://images.gitee.com/uploads/images/2018/0713/174406_c1b1782a_346157.png "2.png")
### nova自动化发布流程图
![版本发布流程图](https://images.gitee.com/uploads/images/2018/0713/160553_cc39a896_346157.png "版本发布流图.png")
### 企业基础服务效果图
![输入图片说明](https://images.gitee.com/uploads/images/2018/0713/164424_35f99939_346157.png "爱奇艺20180713164227.png")
Creek项目目录结构如下：

```
creek
  - 404                        响应404错误
  - 500                        响应500错误
  - bin                        node服务器的启动脚步
  - components                 前端组件
  - doc                        平台文档内容，不会被发布
  - modules                    自定义node模块(暂用)
  - static                     框架级别的公用静态资源
      |- jquery                jQuery库 
      |- jquery-plugins        基于jQuery的插件，如ztree等
      |- bootstrap             bootstrap框架
      |- bootstrap-plugins     基于bootstrap的插件，如datetimepicker
      |- images                框架级别的图片
      |- mixins                less的混入函数库
      |- biz                   业务跨包共用的静态内容
          |-style              业务跨包共用的样式文件(css/less)
          |-images             业务跨包共用的图片资源
  - web                        不需要权限即可以访问的站点内容
      |- [module]              业务代码包
          |- style             业务包内共用的样式文件(css/less)
          |- images            业务包内共用的图片资源
  - apps                       需要进行权限控制的站点内容
      |- [module]              业务代码包
          |- style             业务包内共用的样式文件(css/less)
          |- images            业务包内共用的图片资源
  - app.js                     服务器入口文件
  - favicon.ico                页面标题logo(暂存)
  - fdp-config.js              环境配置文件
  - fis-config.js              fis工具配置文件
  - install.bat                用于安装node模块依赖的脚本文件
  - package.json               node包配置文件
  - readme.md                  平台文档入口，不会被发布
  - release.bat                用于发布前端代码的脚本文件
  - start.bat                  用于启动服务器的脚本
```
dam项目目录结果

```
  - dam                        web项目包工程
  - dam-app                    java技术包，负责框架基础日志类，工程类，文件类
    |- aop                     日志切面  
    |- asynctask               多线程类
    |- service                 基础服务类，公共类，服务治理抽象类
    |- servlet                 web服务接口入口，文件上传服务类
    |- utils                   依赖的第三工具，excel,pdf,md5加密等工具类         
  - dam-portal                 java技术包，负责门户相关服务
    |- common                  公共服务包
      |- service               公共服务类，调用其他子系统接口代理类，切面类
      |- dao                   公共服务类，数据处理
      |- utils                 公共服务类，封装常用工具 
    |- service                 业务服务类，各种应用接口
    |- servlet                 web服务接口入口，文件上传服务类
    |- interface               接口类，暴露给其他子系统接口
  - dam-exception              java技术包，负责全局异常处理
     |- common                  公共服务包
      |- service               公共服务类，调用其他子系统接口代理类，切面类
      |- dao                   公共服务类，数据处理
      |- utils                 公共服务类，封装常用工具 
    |- service                 业务服务类，各种应用接口
    |- servlet                 web服务接口入口，文件上传服务类
    |- interface               接口类，暴露给其他子系统接口
  - dam-ieds                   java技术包，负责服务治理
     |- common                  公共服务包
      |- service               公共服务类，调用其他子系统接口代理类，切面类
      |- dao                   公共服务类，数据处理
      |- utils                 公共服务类，封装常用工具 
    |- service                 业务服务类，各种应用接口
    |- servlet                 web服务接口入口，文件上传服务类
    |- interface               接口类，暴露给其他子系统接口
  - dam-spider                 java技术包，负责爬虫，集成webmagic和webcollector
     |- common                  公共服务包
      |- service               公共服务类，调用其他子系统接口代理类，切面类
      |- dao                   公共服务类，数据处理
      |- utils                 公共服务类，封装常用工具 
    |- service                 业务服务类，各种应用接口
    |- servlet                 web服务接口入口，文件上传服务类
    |- interface               接口类，暴露给其他子系统接口 
  - dam-redis                  java技术包，负责消息服务管理
     |- common                  公共服务包
      |- service               公共服务类，调用其他子系统接口代理类，切面类
      |- dao                   公共服务类，数据处理
      |- utils                 公共服务类，封装常用工具 
    |- service                 业务服务类，各种应用接口
    |- servlet                 web服务接口入口，文件上传服务类
    |- interface               接口类，暴露给其他子系统接口
  - dam-rmqconsumer            java技术包，负责消息服务管理，消费者 
     |- common                  公共服务包
      |- service               公共服务类，调用其他子系统接口代理类，切面类
      |- dao                   公共服务类，数据处理
      |- utils                 公共服务类，封装常用工具 
    |- service                 业务服务类，各种应用接口
    |- servlet                 web服务接口入口，文件上传服务类
    |- interface               接口类，暴露给其他子系统接口
  - dam-rmqproducer            java技术包，负责消息服务管理，生产者
     |- common                  公共服务包
      |- service               公共服务类，调用其他子系统接口代理类，切面类
      |- dao                   公共服务类，数据处理
      |- utils                 公共服务类，封装常用工具 
    |- service                 业务服务类，各种应用接口
    |- servlet                 web服务接口入口，文件上传服务类
    |- interface               接口类，暴露给其他子系统接口
  - dam-timer                  java技术包，负责定时任务
     |- common                  公共服务包
      |- service               公共服务类，调用其他子系统接口代理类，切面类
      |- dao                   公共服务类，数据处理
      |- utils                 公共服务类，封装常用工具 
    |- service                 业务服务类，各种应用接口
    |- servlet                 web服务接口入口，文件上传服务类
    |- interface               接口类，暴露给其他子系统接口
  - dam-ucenter                java基础服务包，负责用户，权限
     |- common                  公共服务包
      |- service               公共服务类，调用其他子系统接口代理类，切面类
      |- dao                   公共服务类，数据处理
      |- utils                 公共服务类，封装常用工具 
    |- service                 业务服务类，各种应用接口
    |- servlet                 web服务接口入口，文件上传服务类
    |- interface               接口类，暴露给其他子系统接口
  - dam-pay                    java基础服务包，负责第三方支付业务
     |- common                  公共服务包
      |- service               公共服务类，调用其他子系统接口代理类，切面类
      |- dao                   公共服务类，数据处理
      |- utils                 公共服务类，封装常用工具 
    |- service                 业务服务类，各种应用接口
    |- servlet                 web服务接口入口，文件上传服务类
    |- interface               接口类，暴露给其他子系统接口
  - dam-wechat                 java基础服务包，负责微信第三方业务
     |- common                  公共服务包
      |- service               公共服务类，调用其他子系统接口代理类，切面类
      |- dao                   公共服务类，数据处理
      |- utils                 公共服务类，封装常用工具 
    |- service                 业务服务类，各种应用接口
    |- servlet                 web服务接口入口，文件上传服务类
    |- interface               接口类，暴露给其他子系统接口
  - dam-sms                    java基础服务包，负责短信第三方业务
     |- common                  公共服务包
      |- service               公共服务类，调用其他子系统接口代理类，切面类
      |- dao                   公共服务类，数据处理
      |- utils                 公共服务类，封装常用工具 
    |- service                 业务服务类，各种应用接口
    |- servlet                 web服务接口入口，文件上传服务类
    |- interface               接口类，暴露给其他子系统接口
  - dam-cms                    java基础服务包，负责内容管理
     |- common                  公共服务包
      |- service               公共服务类，调用其他子系统接口代理类，切面类
      |- dao                   公共服务类，数据处理
      |- utils                 公共服务类，封装常用工具 
    |- service                 业务服务类，各种应用接口
    |- servlet                 web服务接口入口，文件上传服务类
    |- interface               接口类，暴露给其他子系统接口
  - lib                        web项目依赖的jar
  
```

### 私有仓库
![私有仓库](https://images.gitee.com/uploads/images/2018/0713/000012_6924e3e0_346157.png "私有仓库.png")
## 项目如何开发
### 从物理上划分的前后端
该项目是面向企业和个人用户的，如何划分前后端开发，看自己能力
![物理划分的前后端](https://images.gitee.com/uploads/images/2018/0719/130520_882906c4_346157.png "physically-partition.png")
### 从职责上划分的前后端
![职责上划分的前后端](https://images.gitee.com/uploads/images/2018/0719/130609_905be2a4_346157.png "functional-partition.png")
### 从功能上划分的前后端
![功能上划分的前后端](https://images.gitee.com/uploads/images/2018/0719/130732_b78687d3_346157.png "sys-architecture.png")
### 安装教程

creek环境要求：node4.5.0  
    1、使用Sinopia搭建私有的npm仓库 [传送门](https://segmentfault.com/a/1190000005790827)    
    
    2、fis3使用（自动化构建，推送静态文件）[传送门](http://fis.baidu.com/)                                                                         

    3、bower使用（同seajs理前端组件库） [传送门](https://bower.io/)                                                             

    4、pm2使用 （服务状态管理) [传送门](https://wohugb.gitbooks.io/pm2/content/index.html)                                        

    5、nodemon使用 （调试与检测文件）[传送门](https://www.cnblogs.com/chris-oil/p/6239097.html)                                

    6、express使用 （node的web框架）[传送门](http://www.expressjs.com.cn/)
dam环境要求：jdk1.7
   1.spring使用 
   2.mybatis使用
   3.mysql使用
   4.redis使用
   5.nginx使用

nova环境要求：python2.7
   1.python使用
   2.django使用
   3.fabric使用
   4.celery使用

### 使用说明
####　creek在线说明
[在线文档](https://www.zaodei.com/book/creek/index.html)

私有仓库：[传送门](http://118.24.181.144:4873/)

####　dam在线说明
正在整理。。。。

####　nova在线说明
nova在线地址 ：[传送门](https://github.com/haohandongku/nova)

### 相关文章
 1、creek-dam的性能测试报告 [地址](https://www.zaodei.com/jpress/c/482)
    
### 框架体系任务与计划
1）前端框架体系，并写出文档
文档设计内容：
    1.服务器端搭建（nodejs_express_fis3）

   2.项目目录结构

   3.项目部署（测试环境，本地环境）

   4.项目调试

   2）后端架构体系，并写出文档

文档设计内容：
             1.框架搭建（spring+mybatis+mysql+redis+SOA架构体系）

             2.项目目录结构

             3.项目部署

             4.项目调试

   3）基础项目
             
             1.用户中心构建(java搭建)         

             2.授权中心搭建（使用nodejs）   

  4) 产品项目搭建

             1.短信第三方系统（支持常见开发商天翼，阿里云等）

             2.支付第三方系统（支持微信，支付宝，银联）

             3.微信第三方平台（支持微信公共号，微信小程序管理）

 5）运维系统搭建  （django项目）

             1.部署nodejs项目（内测和生产搭建架构图）

             2.部署java项目架构图

             3.集群搭建（nodejs集群，java集群）

### 项目目标
该项目体系资料正在整理当中，前端项目框架成型三年多了，后端框架成型五年多了，能够支撑很强业务能力，已上线项目已经有二三十多个了，项目覆盖web应用，微信公共号，开放平台等等业务场景!项目会从架构搭建---->到三个企业级别项目（第三方微信平台，第三方短信平台，第三方支付平台）协同开发--->项目自动化部署来进行部署开发！！预计框架级别7月底搞完（基础版本），基础项目8月底搞完，还请持续关注！！

2018/08/30  这边刚换新工作，有点忙，业务系统开发和本系统开发文档需要推迟到9月后开发了，还请谅解！ qq咨询：1142261327

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)