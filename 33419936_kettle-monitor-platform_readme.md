
#### 介绍
Kettle是一款国外开源的ETL工具，纯java编写，可以在不同系统平台上运行，绿色无需安装，数据抽取高效稳定，操作简单快捷，提供了丰富的组件来满足不同类型的数据间的转换等。本工具基于kettle的开源版本进行一个开发，提供了kettle任务执行常用的一些功能。满足绝大情况下kettler任务执行管理及执行日志查看功能。 kettle-monitor-platform采用了[Ruoyi](https://gitee.com/y_project/RuoYi)的后台管理系统，在此基础上进行相关功能的开发。基于kettle的（kettle-8.3.0.0-371）版本上进行开发。主要采用spring-boot，mybatis,durid,thymeleaf,kettle-8等技术。


#### 功能简介

  1. 转换管理:配置管理转换，可编辑转换名称及选择参数、执行
  2. job管理：配置管理job，可编辑job名称及选择参数、执行
  3. 参数信息配置：配置转换和任务执行时需要的变量参数
  4. 服务节点：配置kettle的节点，管理节点是否有效
  5. 参数组分类管理: 配置管理参数的分组，一个组下可以有多个参数
  6. 执行日志查看： 查看执行的任务明细和停止正在执行的任务
  7. 定时任务：在线（添加、修改、删除)转换、job及其他的任务调度包含执行结果日志

#### 开发环境

1.  环境准备
 JDK >= 1.8 (推荐1.8版本)
 Mysql >= 5.5.0 (推荐5.7版本)
 Maven >= 3.0
 Tomcat >= 8.4

2.  创建一个数据库，然后执行doc文件夹的下的几个sql脚本
3.  修改配置ruoyi-admin模块下的resource目录下配置文件application-dev.yml下的数据库连接

![配置文件](https://images.gitee.com/uploads/images/2020/0506/211619_61a668ba_7509799.png "配置文件.png")

4.  开发环境idea启动ruoyi-admin模块下的 com.deodar.KettleMonitorApplication  
5.  在tomcat下部署启动是需要复制kettle的simple-jndi目录到{tomcat_home}\bin目录下，不然报错，目录找不到
6.  项目访问地址： http://127.0.0.1:8080/kettle-monitor
#### 系统截图
![监控首页](https://images.gitee.com/uploads/images/2020/0502/212602_2f8ed7e6_7509799.png "监控首页.png")

![转换管理](https://images.gitee.com/uploads/images/2020/0502/212635_ee44d631_7509799.png "转换管理.png")

![job管理](https://images.gitee.com/uploads/images/2020/0502/212705_b6947eb4_7509799.png "job管理.png")

![服务节点](https://images.gitee.com/uploads/images/2020/0502/212743_deb110bb_7509799.png "服务节点.png")

![执行日志查看](https://images.gitee.com/uploads/images/2020/0502/212833_79471482_7509799.png "执行日志查看.png")

![转换明显](https://images.gitee.com/uploads/images/2020/0502/212900_c1d5bef3_7509799.png "转换明显.png")

![job明细](https://images.gitee.com/uploads/images/2020/0502/212924_d802b590_7509799.png "job明细.png")

![定时任务](https://images.gitee.com/uploads/images/2020/0502/212949_df3caf7b_7509799.png "定时任务.png")



#### 交流
QQ: 欢迎加入qq交流群 750935994

#### 感谢
- 感谢[若依](https://gitee.com/y_project/RuoYi)后台管理系统
- 感谢[kettleweb](https://gitee.com/wind137/kettleweb)web版数据集成平台


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)