# 当前工程为Spring-Cloud-Alibaba 项目模板

一、Project结构
===
  根据微服务应用开发框架及规范定义以下project工程结构，请参照以下目录结构建立对应微服务工程，便于工程统一管理。
    

```
├── micor--中心名称  
├── micro-common --中心公共module  
├── micro-service--对外控制层(Controller)或视图(View)层、命名规则：中心- 后端(service)/前端web 
│   ├──src
│       └──main
│            ├──java
│            │   └── com.公司简拼.中心  
│            │        ├── controller  -- controller对外http接口层  
│            │        └── Application 启动入口main函数  
│            │       └── service --数据操作和逻辑 
│            └──resources
│                    ├──logback.xml         
│                    ├──...     --各类配置文件
│                    └──application.yml      --mybatis mapper.xml放的位置
├── micro-archive--以业务子域为一个module 
│   ├──src
│       └──main
│            ├──java
│            │   ├──com.公司简拼.中心.业务域
│            │       ├── client   --远程接口调用
│            │       ├── dal      --数据库表对应的数据结构  
│            │       ├── dao     --dal 中的数据操作
│            │       ├── dto     --传输层的数据结构
│            │       ├── entity  --通用的数据结构 
│            │       └── service --数据操作和逻辑 
│            └──resources
│                    └──mapper      --mybatis mapper.xml放的位置
└── pom.xml  
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)