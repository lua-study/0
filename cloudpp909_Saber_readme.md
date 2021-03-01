  
   
    
    
    

## SpringBlade微服务开发平台
* 采用前后端分离的模式，前端开源两个框架：[Sword](https://gitee.com/smallc/Sword) (基于 React、Ant Design)、[Saber](https://gitee.com/smallc/Saber) (基于 Vue、Element-UI)
* 后端采用SpringCloud全家桶，并同时对其基础组件做了高度的封装，单独开源出一个框架：[BladeTool](https://github.com/chillzhuang/blade-tool)
* [BladeTool](https://github.com/chillzhuang/blade-tool)已推送至Maven中央库，直接引入即可，减少了工程的臃肿，也可更注重于业务开发
* 集成Sentinel从流量控制、熔断降级、系统负载等多个维度保护服务的稳定性。
* 注册中心、配置中心选型Nacos，为工程瘦身的同时加强各模块之间的联动。
* 使用Traefik进行反向代理，监听后台变化自动化应用新的配置文件。
* 极简封装了多租户底层，用更少的代码换来拓展性更强的SaaS多租户系统。
* 借鉴OAuth2，实现了多终端认证系统，可控制子系统的token权限互相隔离。
* 借鉴Security，封装了Secure模块，采用JWT做Token认证，可拓展集成Redis等细颗粒度控制方案。
* 稳定生产了一年，经历了从Camden -> Greenwich的技术架构，也经历了从fat jar -> docker -> k8s + jenkins的部署架构
* 项目分包明确，规范微服务的开发模式，使包与包之间的分工清晰。

## 架构图
 

## 工程结构
``` 
SpringBlade
├── blade-auth -- 授权服务提供
├── blade-common -- 常用工具封装包
├── blade-gateway -- Spring Cloud 网关
├── blade-ops -- 运维中心
├    ├── blade-admin -- spring-cloud后台管理
├    ├── blade-develop -- 代码生成
├── blade-service -- 业务模块
├    ├── blade-desk -- 工作台模块 
├    ├── blade-log -- 日志模块 
├    ├── blade-system -- 系统模块 
├    └── blade-user -- 用户模块 
├── blade-service-api -- 业务模块api封装
├    ├── blade-desk-api -- 工作台api 
├    ├── blade-dict-api -- 字典api 
├    ├── blade-system-api -- 系统api 
└──  └── blade-user-api -- 用户api 
```

## 官网
* 官网地址：[https://bladex.vip](https://bladex.vip)
* 问答社区：[https://sns.bladex.vip](https://sns.bladex.vip)
* 会员计划：[SpringBlade会员计划](https://gitee.com/smallc/SpringBlade/wikis/SpringBlade会员计划)
* 交流群：`477853168`

## 在线演示
* Sword演示地址：[https://sword.bladex.vip](https://sword.bladex.vip)
* Saber演示地址：[https://saber.bladex.vip](https://saber.bladex.vip)

## 项目地址
* 后端Gitee地址：[https://gitee.com/smallc/SpringBlade](https://gitee.com/smallc/SpringBlade)
* 后端Github地址：[https://github.com/chillzhuang/SpringBlade](https://github.com/chillzhuang/SpringBlade)
* 后端SpringBoot版：[https://gitee.com/smallc/SpringBlade/tree/2.0-boot/](https://gitee.com/smallc/SpringBlade/tree/2.0-boot/)
* 前端框架Sword(基于React)：[https://gitee.com/smallc/Sword](https://gitee.com/smallc/Sword)
* 前端框架Saber(基于Vue)：[https://gitee.com/smallc/Saber](https://gitee.com/smallc/Saber)
* 核心框架项目地址：[https://github.com/chillzhuang/blade-tool](https://github.com/chillzhuang/blade-tool)

## 技术文档
* [SpringBlade开发手册](https://gitee.com/smallc/SpringBlade/wikis/SpringBlade开发手册)

## 用户权益
* 允许免费用于学习、毕设、公司项目、私活等。
* 代码文件需保留相关license信息。
* 禁止直接将本项目挂淘宝等商业平台出售。
* 非界面代码50%以上相似度的二次开源，二次开源需先联系作者。

## 如何启动
```
$ git clone https://gitee.com/smallc/Saber.git
$ cd Saber
# 安装
$ yarn install
# 启动
$ yarn run serve     
```

# 界面

## [BladeX](https://bladex.vip/#/vip) 工作流一览
 
     
           
           
     
     
           
           
     
     
           
           
     
 

## [Sword](https://gitee.com/smallc/Sword) 界面一览
 
     
           
           
     
     
           
           
     
     
           
           
     
     
           
           
     
     
           
           
     
 

## [Saber](https://gitee.com/smallc/Saber) 界面一览
 
     
           
           
     
     
           
           
     
     
           
           
     
 

## 监控界面一览
 
     
           
           
     
     
           
           
     
     
           
           
     
     
           
           
     
     
           
           
     
     
           
           
     
 

## 关注我们
![](https://images.gitee.com/uploads/images/2019/0330/065148_f0ada806_410595.jpeg)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)