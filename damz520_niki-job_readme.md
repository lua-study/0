# 作者niki java

#### 介绍
niki job 是基于spring+quartz实现的定时任务中间件，不管是你是单机，还是多机都可以兼容。

#### 软件架构
软件架构说明 spring + quartz


#### 安装教程和使用说明

hello:
       欢迎对接niki job 公共组件定时任务jar包。
       以下为使用说明：

                定时任务组件基于spring quartz 实现，分为单机版和多机分布式版。顾名思义，单机版就是只在一个机器上跑。
                多机版就是分布式多台机器跑，如果某台机器有问题自动在其它机器上跑。
				
                1，首先定时任务基于你的表数据配置。你需要有一个表例如以下sql
                CREATE TABLE `job` (
                  `job_id` bigint(20) NOT NULL AUTO_INCREMENT COMMENT '任务id',
                  `class_name` varchar(200) DEFAULT NULL COMMENT 'spring bean全名称',
                  `job_name` varchar(64) DEFAULT NULL COMMENT '任务名称',
                  `job_group` varchar(64) DEFAULT NULL COMMENT '任务类型',
                  `cron` varchar(100) DEFAULT NULL COMMENT 'cron表达式',
                  `status` tinyint(4) DEFAULT NULL COMMENT '任务状态  1：正常  0：暂停',
                  `remark` varchar(255) DEFAULT NULL COMMENT '备注',
                  `create_time` datetime DEFAULT NULL COMMENT '创建时间',
                  `update_time` datetime DEFAULT NULL COMMENT '修改时间',
                  PRIMARY KEY (`job_id`)
                )COMMENT='定时任务';

                2，如果你只有一个项目需要跑定时任务，只需要在startjob中把JOB_GROUP_NAME默认值，设置成你的数据库里面的job_group。
                如果你跟其他组共用一个数据库表，通过job_group来区分各个组的数据，你只需要跑你的定时即可！
				
                重点1：如果你有2个或者2个以上项目都需要用此包就把 startjob 抽出来，放在你们各自的项目中，把我这个中间件的startjob要删掉，各自项目启动各自的startjob
				
                然后把DynamicJob中sql select job_name,cron,class_name,job_group,state from  job where job_group = ?
                sql 换你的表就可以了，如果你的定时任务表就用我的sql就不用换。
				然后把com.niki.job 让spring扫描到！


			3，以下为分布式使用环境说明
				重点：我的中间件默认是的多机版，并且使用自己单独的数据源，如果你也是多机，并且定时任务用自己数据眼可以改改数据库配置直接启动。
				
				单机：1，先找到com.niki.job.QuartzConfiguration 类，把单机模块注释打开，并把下面2个多机模块注释起来
					   2，找到schedulerFactoryBean.setConfigLocation(new ClassPathResource("/quartz.properties")); 这一行把quartz.properties换成quartz-signle.properties


				多机使用项目数据库：配置文件保持不变还是quartz.properties，把单机的代码和多机自用数据源代码注释掉就可以了，直接启动
				
				多机使用自有数据库：本中间件默认是此配置，单机和多机共用项目数据源注释掉即可！
				
				
				
 ###### 如有不懂可以私信我或者微信我: dcykefu	帮助解答。	

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)