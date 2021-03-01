# quartz

#### 项目简介
1. 基于quartz的二次集成
2. 支持集群
3. 支持其它web项目进行功能开发
4. 动态控制定时任务启动、暂停、重启、删除、添加、修改
5. 支持多数据库
6. 支持自实现Scheduler、Job、Trigger监听，系统自动注册
7. 数据源使用阿里Druid

#### 使用教程

1. 引入依赖
2. 修改jdbc.properties数据源配置
3. 继承AbstractQuartzTask，实现自己的定时任务
4. 功能开发
5. 任务展示
6. 调用接口控制任务

#### 配置示例
```xml
 
     
     
     
 

 
 
     
     
     
 

  

 
     
     
     
         
             
             
         
     
 
-->

 
  

 
  

 
 
     
     
      
      
     
      
      
     
       -->
     
     
     
     
     
     
     
         
             
         
     
    -->
     
         
             
         
     
 

 
      
 
```

#### 使用说明

1. QuartzTaskHandler 任务处理接口，其中有添加、修改、删除、暂停、重启等功能
2. AbstractSchedulerListener Scheduler监听，可自行实现自己需要的Scheduler监听
3. AbstractJobListener Job监听，可自行实现自己需要的Job监听
4. AbstractTriggerListener Trigger监听，可自行实现自己需要的Trigger监听

#### 版权说明
quartz使用 [Apache License 2.0](https://gitee.com/xbd521/quartz/blob/master/LICENSE "Apache License 2.0") 协议





 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)