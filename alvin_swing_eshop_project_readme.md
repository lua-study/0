# eshop商城平台
[基础环境及配置清单](https://blog.csdn.net/qq_41788977/article/details/103246954)
![商城平台封面](https://images.gitee.com/uploads/images/2019/1111/231309_4f6a741b_4932754.png "new封面.png")
***
## 介绍
   eshop商城项目是作者为了研究电商平台领域内的几大热门技术：高并发的系统架构、分布式的集群部署以及SOA服务治理等成熟的技术，利用业余时间编写的实践项目，最终目标是建设一个成熟的电商平台，以此来专研、完备、升级自我的技能树，如果你也是喜欢实践的技术爱好者，不妨也加入进来，一同完成这个作品。

   eshop基于SOA架构，通过阿里开源技术Dubbo框架进行服务治理，使用Nginx服务器来做静态资源缓存、反向代理及负载均衡，可以支持亿级访问数据量的商城系统。

![商城功能点](https://images.gitee.com/uploads/images/2019/1017/202628_0bd8ac50_4932754.png "eshop-function004.png")

   eshop商城具备电商运营常见的几大功能模块，集成了现有比较流行的热门技术。通过这个项目可以将分布式、负载均衡等热门技术落实到实际的项目中来，可以更加深入的了解电商平台网站的运营流程。

***
## 技术选型

   现行系统架构
   

   临时制作的简易版商城系统架构及所应用到的主要技术 :bowtie: 

 1. Spring、SpringMVC、Mybatis、Dubbo（Zookeeper)
 2. JSP、JSTL、jQuery、jQuery plugin、EasyUI、KindEditor、CSS+DIV
 3. Mysql、MyCat、Redis(Cluster)
 4. Solr(SolrCloud)
 5. Nginx、VSFTPD、Tomcat
 6. jsonp
 7. Nexus、Maven

***
## 系统前台&后台功能
 &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;前台功能&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; 	 |   &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;后台功能&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; 
 :----:          | :----:
 门户		 | 系统管理
 商品搜索	 | 商品管理
 商品展示	 | 活动管理
 购物车		 | 商品推荐
 注册&登录	 | 订单管理
 订单提交	 | CMS*
 支付		 | CRM**
 会员中心	 | 采购管理
 客户服务	 | 财务管理
 公告		 | 统计报表
 帮助中心	 | 网络管理
 社区		 | WMS***

   __*CMS__ (Content Management System)内容管理

   __**CRM__ (Customer Relationship Management)客户关系管理

   __***WMS__ (Warehouse Management System)仓储管理系统

***
## 运行说明

  1.项目目录

     eshop_project

       eshop_common            项目公用模块存放工具类及连接配置信息

       eshop_service           dubbo服务列表

       eshop_service_impl      dubbo provider提供服务实现，数据缓存，数据持久化等

       eshop_webmanage         商城后台管理
       
       eshop_item              商城商品服务

       eshop_portal            商城前台
       
       eshop_search            商品搜索服务

       eshop_redis             商城平台缓存服务
    
       eshop_passport          前台统一登录（SSO）服务
       
       eshop_cart              购物车
    
       eshop_order             商品订单

       持续进行中...

  2.附件  

       tip.txt 记录在项目编写时产生的问题

       父项目src：“Fixed BUG LOG 解决问题记录.docx”文件列出解决问题的详细信息

       父项目src：file文件夹，存放sql等备用文件

***
## 参与贡献

1. Fork 本仓库
2. 本地导入maven项目，更改eshop_common下common.properties redis集群及zookeeper连接信息，eshop_service_impl下db.properties mysql数据库连接信息
3. 新建 Feat_xxx 分支
4. 提交代码
5. 新建 Pull Request

***
## 已优化点

     1.将集成在Dubbo服务中的redis缓存移出作为单独模块维护，减轻Dubbo访问压力
     2.引入Solr搜索引擎，提升商品信息检索速率，单独创建search项目作为商品搜索服务
     3.利用VSFTPD+Nginx作为商城图片服务器，独立业务模块之外方便维护
     4.mybatis二级缓存及懒加载的应用，提升数据检索效率 
     5.优化PageHelper分页插件，提升大数据量查询时分页效率
     6.实时缓存同步时，往往会降低主业务响应速度，对于此类操作可利用多线程技术来解决 

***
## 待优化点

     1.JSP页面带来的效率下降：使用JSP作为前台展示页面很难动静分离，所有动静态资源均以HTTP协议从服务器获取，页面加载较慢

***
## 码云特技

   1. 使用 Readme\_XXX.md 来支持不同的语言，例如 Readme\_en.md, Readme\_zh.md
   2. 码云官方博客 [blog.gitee.com](https://blog.gitee.com)
   3. 你可以 [https://gitee.com/explore](https://gitee.com/explore) 这个地址来了解码云上的优秀开源项目
   4. [GVP](https://gitee.com/gvp) 全称是码云最有价值开源项目，是码云综合评定出的优秀开源项目
   5. 码云官方提供的使用手册 [https://gitee.com/help](https://gitee.com/help)
   6. 码云封面人物是一档用来展示码云会员风采的栏目 [https://gitee.com/gitee-stars/](https://gitee.com/gitee-stars/)

***

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)