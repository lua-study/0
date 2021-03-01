# flyray-targe

#### 项目介绍
flyray-targe
代号为：天盾 ，基于rbac模型的基础框架

基于该系统可以开发自己的业务场景模块

[火源链](http://www.huoyuanshequ.com/) ：使发行的token对应实体价值，打造一个实体通证经济生态圈



![项目进度](flyray-doc/qq.png)


# 业务架构

![项目进度](flyray-doc/云平台系统架构图.jpg)


# 技术架构

![项目进度](flyray-doc/TechnologyArchitecture.png)

# 网关设计

![项目进度](flyray-doc/gate.png)
![项目进度](flyray-doc/gateFunction.jpg)

# 体验小程序

![项目进度](flyray-doc/xcx.jpg)

# 工程依赖关系

![项目进度](flyray-doc/dp.jpg)

# 对账处理

![项目进度](flyray-doc/reconciliation_process.jpg)

# 区块链架构

![项目进度](flyray-doc/640.webp)

# 管理后台UI

![项目进度](flyray-doc/login.png)

![项目进度](flyray-doc/index.png)

![项目进度](flyray-doc/dept.png)

![项目进度](flyray-doc/role0.png)

![项目进度](flyray-doc/role.png)



#### 项目代码自动生成步骤

1、修改builder目录下的数据库地址和表名

2、eclipse选中项目右键 run as maven build

3、Goals: mybatis-generator:generate

4、执行 run



# 启动指南



## 须知



## 后端工程启动

### 环境须知

- mysql一个，redis一个，rabbitmq一个，consul一个

- jdk1.8

- IDE需安装lombok插件



### 组织结构



flyray-pirate

```
├    flyray-center  -- 注册中心 改为consul 之后 该工程废弃

├    flyray-pirate-config  -- 上传到git上的配置文件 具体配置看 flyray-config 下的bootstrap.yml qq群文件有

├    flyray-config    -- 配置中心

├    flyray-auth   -- 配置中心   

├         ├──  flyray-auth-server --授权中心

├		 ├──  flyray-auth-client

├         └──  flyray-auth-common 

├    flyray-modules -- 功能模块	

├       ├── flyray-admin   -- 运营后台

├       ├── flyray-generator   --代码生成模块

├       ├── flyray-search  --搜索服务

├       ├── flyray-crm-core -- crm模块

├       ├── flyray-pay-core -- 支付模块

├       ├── flyray-biz -- 业务场景模块

├       └── flyray-mq  --消息中心

├    flyray-gate  -- 服务网关

├       ├── flyray-gate-zuul   --zuul的实现 

└       └── flyray-gateway-v2    -- spring cloud gateway 的实现     


```



### 运行步骤

- 运行数据库脚本：依次运行数据库：flyray-admin/db/init.sql、flyray-auth-server/db/init.sql、

- 修改配置数据库配置：flyray-admin/src/main/resources/application.yml、flyray-gate/src/main/resources/application.yml

- 按`顺序`运行main类：CenterBootstrap（flyray-center）、ConfigBootstrap（flyray-config）、AuthBootstrap（flyray-auth-server）、AdminBootstrap（flyray-admin）、GatewayServerBootstrap（flyray-gateway-v2）



## 前端工程地址

[点击查看地址](https://gitee.com/boleixiongdi/flyray-targe-admin-ui)



##感谢

感谢以下贡献者



##关于作者



```javascript

  var autho = {

    nickName  : "博羸",

    site : "http://www.boleixiongdi.com"

  }

```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)