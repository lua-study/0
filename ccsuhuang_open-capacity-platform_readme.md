# [![Fork me on Gitee](https://gitee.com/owenwangwen/open-capacity-platform/widgets/widget_5.svg)](https://gitee.com/owenwangwen/open-capacity-platform)open-capacity-platform 微服务能力开放平台 
[![star](https://gitee.com/owenwangwen/open-capacity-platform/badge/star.svg?theme=white)](https://gitee.com/owenwangwen/open-capacity-platform/stargazers)
[![Fork me on Gitee](https://gitee.com/owenwangwen/open-capacity-platform/widgets/widget_6.svg)](https://gitee.com/owenwangwen/open-capacity-platform)
[![fork](https://gitee.com/owenwangwen/open-capacity-platform/badge/fork.svg?theme=white)](https://gitee.com/owenwangwen/open-capacity-platform/members)

简称ocp是基于layui+springcloud的企业级微服务框架(用户权限管理，配置中心管理，应用管理，....),其核心的设计目标是分离前后端，快速开发部署，学习简单，功能强大，提供快速接入核心接口能力，其目标是帮助企业搭建一套类似百度能力开放平台的框架；



# **项目地址** #
http://59.110.164.254:8066/login.html 用户名/密码：admin/admin

# 技术介绍  #
 
 
	 
           
		   
     
 

- 基于layui前后端分离的企业级微服务架构
- 兼容spring cloud netflix & spring cloud alibaba
- 优化Spring Security内部实现，实现API调用的统一出口和权限认证授权中心
- 提供完善的企业微服务流量监控，日志监控能力 
- 提供完善的压力测试方案
- 提供完善的灰度发布方案
- 提供完善的微服务部署方案，支持shell部署和docker两种方式

# 技术文档 #

### 试读 :
(https://www.kancloud.cn/owenwangwen/open-capacity-platform/content)


### 正式文档 :
(https://www.kancloud.cn/owenwangwen/open-capacity-platform) 


### 欢迎进群（群内领资料）

`一键加群`
           

 
	 
              

 

# 项目组织结构分析   #
![输入图片说明](https://images.gitee.com/uploads/images/2019/0509/110555_5f9dd329_869801.png "屏幕截图.png")


 

## open-capacity-platform能力开放平台管理    

 
	 
           
           
     
	 
           
           
     
     
           
           
     
     
           
           
     
     
           
           
     
     
           
           
     
     
 



 
# 容器化部署   


 
	 
           
           
     
	 
           
           
     
	 
           
           
     
	 
           
           
     
     
           
           
     
	 
           
           
      
 
 

# api-gateway vs new-api-gateway #
内网测试网关/api-user/users/current
## zuul-->api-gateway ##

 
	 
           
           
     
	 
           
           
     
     
 
 
## spring cloud gateway -->new-api-gateway ##


 
	 
           
           
     
	 
           
           
     
     
  

#  灰度发布功能演示   
 
ocp灰度发布功能(参考dev分支) 
a.先启动 register-center 注册中心的 eureka-server 注册服务  
b.在启动 api-gateway 网关服务 
c.再启动 oauth-center 认证中心 oauth-server 认证服务 
d.在启动 business-center 业务中心的 对应服务 user-center 
d.启动gray-center的discovery-console  
e.启动gray-center的discovery-console-desktop    
 
灰度管理UI  
用户名:admin      
密码  :admin  


 
	 
           
           
     
	 
           
           
     
     
 


请参考
[https://github.com/Nepxion/Docs/blob/master/discovery-doc/README_QUICK_START.md](https://github.com/Nepxion/Docs/blob/master/discovery-doc/README_QUICK_START.md)，感谢军哥分享  

#   链路跟踪 
 
	 
           
           
     
	 
           
           
     
     
 

# 系统监控 #
 
	 
           
           
     
 

# 用户权益 #
- 允许免费用于学习、毕设、公司项目、私活等。




# 禁止事项 #
- 代码50%以上相似度的二次开源。
- 注意：若禁止条款被发现有权追讨9999的授权费。

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)