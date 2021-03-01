## izone-sboot
对于后台管理系统, github(gitee)有太多现成的脚手架，有些已经开发维护了很多年非常稳定(比如jeesite, ruoyi)， 那么再造轮子是否显得没有必要；对于这个问题有两种看法，一、对于初学者，再学习了网上的一些优秀项目之后打算自动动手开发一套， 主要目的是动手实践，顺便开源 二、不管是再健全的项目在使用者看来或多或少都会有不足，因为每个人看问题的角度不同，这种属于创新型的，有自己独到的见解 三、顺手型的， 比如作者对于项目使用了不同的架构， 但是想提供一个简单版本, 比如单体版本和分布式版本。所以对于是否重复造轮子这个问题对于不同的人有不同的见解， 但是不管怎么样，对于使用者而言何尝不是多了一种选择
#### [项目预览地址](http://izone.iteaj.com) 用户名：admin 密码：admin123456
#### 项目介绍目录
1. [项目介绍](#项目介绍)
2. [使用语言和框架](#语言和框架)
3. [最新版本更新日志](#更新日志)
#### 项目介绍
对于上面三种情况，这个项目属于后两种：市面上的一些项目不足点和一些见解在这个项目上主要体现在前端：
1. 对于一个后台管理系统，功能的变化很少，页面相对固定(甚至有些基本功能在上线之后就不会在改变)，但是传统开发方式一个功能不可避免的增删改查就需要四个页面设置更多，而对于现在流行的单页面开发方式也有很多不足的地方，比如新增一个功能就必须在开发之后重新编译、打包、发布。如果这个时候对于某个组件的修改涉及到了其他功能还需要完整的功能测试， 费事费力。此项目前端是基于vue和antd-vue自研的[多页面项目](https://gitee.com/iteaj/ivzone)，组件化，一个页级组件相当于一个页面(包含了增删改查详情)
2. 本项目属于另外一个分布式项目的单体版本, 且此[分布式项目](https://gitee.com/iteaj/izone)和普通的分布式有本质上的区别, 在部署上可以将多个应用打成同一个zip包一起发布， 在数据交互方面，不同应用之间可以使用同一个jvm进行数据交互(有别于rpc), 也可以使用rpc远程调用, 且提供应用在线启动、卸载、更新(基于蚂蚁金服sofa-ark框架，类加载隔离)

#### 语言和框架
1. 后端：java1.8、spring boot2、sofa boot(蚂蚁金服)、mybatis、mybatis-plus、shiro、thymeleaf、hikaricp
2. 前端：vue2.6、antd、axios、qs、moment、validate
3. 数据： mysql5.7+
4. 开发工具：idea
#### 更新日志
当前最新版本1.1.1
1. 更新ivzone到最新版[ivzone更新日志](https://gitee.com/iteaj/ivzone/wikis/%E7%89%88%E6%9C%AC%E6%9B%B4%E6%96%B0%E6%97%A5%E5%BF%97?sort_id=2131566)
2. 新增403 404 500 等错误页面
3. 新增代码生成器, 支持多模块, 直接导入到项目路径
4. 新增演示环境拦截
5. 修改其他bug

#### 项目说明
1. 虽然是单体项目, 但是项目结构使用maven多模块定义, 分为dao层、service层、view层、公用的static模块和启动模块bootstrap；dao、service、view模块属于pom模块，他们的子模块才是具体的业务模块，结构图如下：
![项目结构](https://images.gitee.com/uploads/images/2020/0421/112815_aa08898e_1230742.jpeg "1587439669(1).jpg")
2. 环境使用maven的环境定义配合spring的profile, 这样做的好处是减少环境相关配置文件![环境配置](https://images.gitee.com/uploads/images/2020/0421/113451_53993420_1230742.jpeg "1587440060(1).jpg")

#### 参与贡献

1. Fork 本项目
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