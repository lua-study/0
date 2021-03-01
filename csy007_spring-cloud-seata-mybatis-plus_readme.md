# seata mybatis plus demo

![介绍](doc/1.png)

## 依赖
依赖 | 版本
---|---
Spring Boot |  2.2.2.RELEASE  
Spring Cloud | Hoxton.SR1
spring-cloud-alibaba | 2.1.1.RELEASE
Mybatis Plus | 3.3.0
seata | 0.9.0
seata-server | 1.0.0
   

## 运行项目
1. ide需要安装`lombok`插件
2. 新建两个数据库，执行[sql.sql](sql.sql)文件
3. 修改`seata-user`和`seata-account`项目的`application.yml`数据库配置和nacos配置
4. 修改`seata-user`和`seata-account`项目的`registry.conf`的配置
5. 下载并启动nacos[https://github.com/alibaba/nacos/releases](https://github.com/alibaba/nacos/releases)
6. 下载seata-server
    * lanzou下载[https://www.lanzous.com/i8i4isb](https://www.lanzous.com/i8i4isb)
    * github下载[https://github.com/seata/seata/releases](https://github.com/seata/seata/releases)
7. 修改config/file.conf和config/registry.conf
    * `config/file.conf`这里的vgroup_mapping.**my_test_tx_group** = "default"要和`application.yml`里的
`spring.cloud.alibaba.seata.tx-service-group`一致
    ![file.conf.png](doc/file.conf.png)
    * 修改`config/registry.conf`的nacos地址
    ![reg.png](doc/reg.png)
8. 启动seata-server,window执行`bin/seata-server.bat`,linux或mac执行`bin/seata-server.bat`
9. 启动`seata-account`和`seata-user`服务
10. 浏览器访问[http://localhost:7788/index.html](http://localhost:7788/index.html)即可查看效果

## 相关文档
* [seata官方文档](http://seata.io/zh-cn/docs/overview/what-is-seata.html)
* [nacos官方文档](https://nacos.io/zh-cn/docs/what-is-nacos.html)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)