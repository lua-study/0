

### hrcms

   基于springBoot框架的内容管理系统，采用最新最主流的技术，后端采用spring boot,mybatis-plus,freemaker，shiro，redis，mysql，等,主要功能：消息队列，权限控制，自定义栏目文章，扩展，内容管理，通用日志记录等。

### 目录
* hrcms-web： 前端代码：地址：https://gitee.com/haor186/hrcms_web_V1.2.git  请使用webstorm或vscode
* hrcms： 后端代码： 请使用idea或Eclipse
* 健康监控： https://gitee.com/haor186/admin-server

### 后端：
- JDK：1.8
- 数据库：Mysql
- 项目构建工具：Maven
- MVC框架：SpringBoot
- ORM框架：MyBatisPlus
- 文档数据库: MongoDb
- 缓存：Redis
- 消息队列： AMQP(rabbitMq)实现
- JSON工具：Fastjson
- 数据库连接池：Druid 
- 模板引擎：Freemarker 
- 权限管理：ApacheShiro 

* * *

### 前端：
- Nodejs：12.1
- 底层框架: Vue
- 组件库：IView
- 富文本编辑器: vue-quill-editor
- Json编辑器: vue-json-editor



### 搭建步骤

请阅读项目中 hrcms_V1.2 ->  about 中的环境搭建手册!

请阅读项目中 hrcms_V1.2 ->  about 中的环境搭建手册!

请阅读项目中 hrcms_V1.2 ->  about 中的环境搭建手册!

### 鸣谢

- MybatisPlus   https://git.oschina.net/baomidou/mybatis-plus
- 各种中间件- -!

# 特点 
* 免费完整开源：基于开源协议，源代码完全开源，无商业限制,开发者承诺将HRCMS内容系统永久完整开源 
* 标签化建站：不需要专业的后台开发技能，只要使用系统提供的后台系统，就能轻松建设网站； 
* 丰富插件：支持文章复杂排版 
* 定期更新：承诺定期更新，分享更多好用等模版与插件； 
* 文档丰富：为了让用户更快速的使用HRCms系统进行开发，作者持续更新开发相关文档，如标签文档、使用文档、视频教程等； 
* 约定大于配置: 80%的中间集成配置 在后台系统中可视化配置 支持Redis、es、MongoDb、FastDFS、等等
* 松耦合： 后台权限管理系统与新闻模块松耦合 可以直接删除新闻模块单独使用
* 全文检索： 基于ES实现全站文章的全文快速检索
* 可视化数据：基于echarts和MongoDB 实现可视化海量数据的展示 二次开发成本低
# 面向对象
* 企 业：缺乏it技术帮助创立初期的公司或团队快速搭建产品的技术平台，加快公司项目开发进度；
* 开发者：帮助开发者快速完成承接外包的项目，避免从零搭建系统；
* 学习者：初学JAVA的同学可以下载源代码来进行学习交流；

# 开发环境
建议开发者使用以下环境，这样避免版本带来的问题
* Windows、Linux
* Eclipse、Idea
* Mysql≧5.7
* JDK≧8
* Tomcat≧8
* 中间件请阅读项目中的项目搭建文档
### 技术交流

* 作者微信:Johnston
* QQ:1261670412
包结构说明：
```
cn
  --haoran
    --common            公共配置
      --aspect          全局注解处理器
      --exception       全局异常处理
      --utils           工具类
      --validator       实体校验规则
        --group         规则组
      -xss              xss拦截
    --config            全局配置：跨域、拦截器、验证码、mybatisplus、redis、权限、接口文档swagger
    --datasource        多数据源配置（适合1.5.12，2.0需优化）
    --modules           业务模块
      --demo            业务包名
        --annotation    自定义注解
        --config        配置信息
        --controller    restful接口或controller
        --dao           mybatisplus生成的dao
        --entity        实体
        --dto           数据转换对象
        --form          表单封装（不是必须有，根据业务定）
        --interceptor   拦截器（注解拦截处理或额外的拦截器）
        --resolver      处理器（拦截处理方法）
        --service       
          --impl        服务接口实现类
        --utils         自定义工具类(命名规则：XxxUtils)
    --rule              规则引擎
      
```
#### 5. resources结构说明
```
resources
         --ftl                    freemarker模板（导出）
         --mapper                 mybatisplus映射文件
         --static                 swagger静态资源
         --application.yml        全局配置文件
         --application-dev.yml    开发环境配置
         --application-prod.yml   生产环境配置
         --application-test.yml   测试环境配置
         --banner.txt             启动banner配置
         --logback-spring.xml     全局日志配置
```

### 后端截图
![输入图片说明](https://images.gitee.com/uploads/images/2020/0206/214238_49e43c9f_5420658.png "FNRJ4``E~KQW4ENN3[N6TB1.png")
![输入图片说明](https://images.gitee.com/uploads/images/2020/0206/214250_a8eac817_5420658.png "H_$WF16`5_G8{A_(OOSP3PD.png")
![输入图片说明](https://images.gitee.com/uploads/images/2020/0206/214303_5c936a06_5420658.png ")(YMO415Y[4DOTRS8R@FD3U.png")
![输入图片说明](https://images.gitee.com/uploads/images/2020/0206/214315_ff4a3d42_5420658.png "@BZLUBX}GQJ2_J5G8YC{`3C.png")
![输入图片说明](https://images.gitee.com/uploads/images/2020/0206/214403_31ee89dd_5420658.png "CQ2WN8{~PA{3H`$I}(V4QT6.png")

### 前端截图

![输入图片说明](https://images.gitee.com/uploads/images/2020/0206/214338_0daaf8ed_5420658.png "WP4IY`SPQ5UC0[YO92C`$YS.png")
![输入图片说明](https://images.gitee.com/uploads/images/2020/0206/214354_20efaf04_5420658.png "EZIJXL8}%[G%$K1MNMM9LPT.png")
![输入图片说明](https://images.gitee.com/uploads/images/2020/0206/214418_ed09dd52_5420658.png "BF_M~2ER8{W2H57E%4QN4~3.png")

### 免责声明：
* 该项目用于生产环境中 出现任何问题与作者无关 作者可以提供有偿技术支持
* 如需求量级大 作者可提供有偿分布式基于spring cloud框架的版本


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)