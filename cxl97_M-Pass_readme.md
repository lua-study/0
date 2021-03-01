 
	   
 
 
	 
		  
	 
	 
		  
	 
         
		 
	 
         
		 
	 
	 
		  
	 
	 
		  
	 
	  
	      
	  
 

基于SpringBoot2.x、SpringCloud并采用前后端分离的企业级微服务,多租户系统架构微服务开发平台 mPaaS（Microservice PaaS）为租户业务开发、测试、运营及运维开源框架，能有效降低技术门槛、减少研发成本、提升开发效率，协助企业快速搭建稳定高质量的微服务应用;同时还集合各种微服务治理功能和监控功能。模块包括:企业级的认证系统、开发平台、应用监控、慢sql监控、统一日志、单点登录、Redis分布式高速缓存、配置中心、分布式任务调度、接口文档、代码生成等等

[TOC]

    ______  ___     ________                      
    ___   |/  /     ___  __ \_____ _______________
    __  /|_/ /________  /_/ /  __ `/_  ___/_  ___/
    _  /  / /_/_____/  ____// /_/ /_(__  )_(__  )
    /_/  /_/        /_/     \__,_/ /____/ /____/  

## 项目总体架构图 
**如果您对此项目感兴趣，请点右上角 "Star" 支持一下谢谢**
![项目架构图](https://images.gitee.com/uploads/images/2019/1018/020143_0d434b4a_1468963.jpeg "mPass_Springcloud微服务架构.jpg")

 :anger:  :facepunch:   _系统处于开发阶段

**核心功能**：
- **快速开发**：工程化的开发框架可以自动生成初始化代码，框架还提供模块化开发模式，适用于多人协作开发。
- **性能优化**：支持运营活动投放一站式全流程创建管理，加载智能化投放能力，最大可能提升运营效率和转化效果，助力业务增长。
- **数字化运营闭环**：所有组件都经历了高并发，大流量的检验，对弱网，保活，容器等都有深度的优化，能够兼容复杂的客户端情况
- **使用方式灵活**：框架与组件并没有强依赖，可分可合，灵活机动。各组件可以独立的提供强大的功能，也可以互相配合优化使用体验，发挥更大的作用

### 基础业务模块
- [x] [注册配置服务](https://gitee.com/ibyte/M-Pass/tree/master/starter-mpass/starter-mpass-nacosx) mPass服务注册、配置中心服务
- [x] [聚合基础服务](https://gitee.com/ibyte/M-Pass/tree/master/starter-mpass/starter-mpass-server) 业务聚合服务,可自由服务聚合、独立部署
- [x] [监控系统服务](https://gitee.com/ibyte/M-Pass/tree/master/sys-manage/sys-monitor) 监控系统基础业务调整(包含：日志等级调整、基础服务状态与服务使用状态)
- [x] [对象存储服务](https://gitee.com/ibyte/M-Pass/tree/master/sys-manage/sys-attach) 业务服务附件存储(包含：本地，oss、bos、obs、odo、tos)
- [x] [组织架构服务](https://gitee.com/ibyte/M-Pass/tree/master/sys-manage/sys-org) 组织架构元素（包含：机构、部门、岗位、群组、人员）
- [ ] [任务调度服务](https://gitee.com/ibyte/M-Pass/tree/master/sys-manage/sys-job) 任务集中调度服务

### 项目开发更新进度
**如果您对此项目感兴趣，请点右上角 "Star" 支持一下谢谢**
- [查看更新记录请移步](https://gitee.com/ibyte/M-Pass/tree/master/update-record)
- [x] [二零一九年十月更新记录](https://gitee.com/ibyte/M-Pass/blob/master/update-record/UPDATE-RECORD-2019-10.md)
- [x] [二零一九年十一月更新记录](https://gitee.com/ibyte/M-Pass/blob/master/update-record/UPDATE-RECORD-2019-11.md)
- [x] [二零一九年十二更新记录](https://gitee.com/ibyte/M-Pass/blob/master/update-record/UPDATE-RECORD-2019-12.md)
- [x] [二零二零年一月更新记录](https://gitee.com/ibyte/M-Pass/blob/master/update-record/UPDATE-RECORD-2020-01.md)
- [x] [二零二零年二月更新记录](https://gitee.com/ibyte/M-Pass/blob/master/update-record/UPDATE-RECORD-2020-02.md)
- [ ] [二零二零年三月更新记录](https://gitee.com/ibyte/M-Pass/blob/master/update-record/UPDATE-RECORD-2020-03.md)

### 业务模块SQL
- [注册配置服务](https://gitee.com/ibyte/M-Pass/blob/master/update-record/server-sql/mpass-nacosx)
- [组织架构服务](https://gitee.com/ibyte/M-Pass/blob/master/update-record/server-sql/sys-manage/sys-org)

## 运维架构图
![输入图片说明](https://images.gitee.com/uploads/images/2019/1025/005728_9d45ec29_1468963.png "ops.png")

## 项目详细部署图
![输入图片说明](https://images.gitee.com/uploads/images/2019/1025/005737_ba969737_1468963.png "deploy.png")

## 服务简述
#### 对象存储服务
![存储机制](https://images.gitee.com/uploads/images/2019/1128/200848_8ac7f86d_1468963.png "mpass 存储机制.png")
#### 组织架构服务
![组织架构基础数据模型](https://images.gitee.com/uploads/images/2019/1230/173721_27c0e789_1468963.png "组织架构基础模型.png")

**交流群**
 
     
         QQ群：mPaaS开源社区 
         微信交流群：微信群(加微信入群) 
         微信公众号：码农架构  
     
     &nbsp; 
     
           
           
           
     
 


**如果您觉得有帮助，请点右上角 "Star" 支持一下谢谢**

**如果您对此项目感兴趣，请点右上角 "Star" 支持一下谢谢**

**如果需要帮助请留言或者加微信，晚上22：00后统一回复解决**

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)