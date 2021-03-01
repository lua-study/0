## RuoYi-fast-Oracle
#### 若依 Maven 单模块 Oracle 版本
基于 [RuoYi-fast MySQL](https://gitee.com/y_project/RuoYi-fast) ，参考 [RuoYi-Oracle](https://gitee.com/racsu/RuoYi-Oracle)

> 若依多模块 MySQL 版本 [RuoYi](https://gitee.com/y_project/RuoYi)  
若依单模块 MySQL 版本 [RuoYi-fast MySQL](https://gitee.com/y_project/RuoYi-fast)  
若依多模块 Oracle 版本 [RuoYi-Oracle](https://gitee.com/racsu/RuoYi-Oracle)  
如需其他版本，请移步 [项目扩展](http://doc.ruoyi.vip/ruoyi/document/xmkz.html)  `(不定时更新)`

#### 在线体验
> admin/admin123  

**演示地址**：http://ruoyi.vip  
**文档地址**：http://doc.ruoyi.vip  
**语雀地址**：https://www.yuque.com/ry  
**Issues地址**：https://gitee.com/y_project/RuoYi/issues?state=closed  
**Issues地址**：https://gitee.com/racsu/RuoYi-Oracle/issues?state=closed 


#### 交流及反馈
`bug`及其它问题请提`Issues`或者进群讨论

    该问题是怎么引起的？
    重现步骤
    报错信息
    
    相关的Issue
    原因/目的/解决的问题等
    描述（做了什么，变更了什么）
    测试用例

>   Issues 地址  
    https://gitee.com/y_project/RuoYi/issues  
    https://gitee.com/racsu/RuoYi-Oracle/issues  
    https://gitee.com/baha/RuoYi-fast-Oracle/issues
 
#### 若依交流群

若依 QQ 群： QQ群： [![加入QQ群](https://img.shields.io/badge/已满-1389287-blue.svg)](https://jq.qq.com/?_wv=1027&k=5HBAaYN)  [![加入QQ群](https://img.shields.io/badge/已满-1679294-blue.svg)](https://jq.qq.com/?_wv=1027&k=5cHeRVW)  [![加入QQ群](https://img.shields.io/badge/已满-1529866-blue.svg)](https://jq.qq.com/?_wv=1027&k=53R0L5Z)  [![加入QQ群](https://img.shields.io/badge/已满-1772718-blue.svg)](https://jq.qq.com/?_wv=1027&k=5g75dCU)  [![加入QQ群](https://img.shields.io/badge/已满-1366522-blue.svg)](https://jq.qq.com/?_wv=1027&k=58cPoHA)  [![加入QQ群](https://img.shields.io/badge/已满-1382251-blue.svg)](https://jq.qq.com/?_wv=1027&k=5Ofd4Pb)  [![加入QQ群](https://img.shields.io/badge/已满-1145125-blue.svg)](https://jq.qq.com/?_wv=1027&k=5yugASz)  [![加入QQ群](https://img.shields.io/badge/86752435-blue.svg)](https://jq.qq.com/?_wv=1027&k=5Rf3d2P)  点击按钮入群。  
若依 Oracle 版本交流群： [![oracle版本交流群](https://img.shields.io/badge/22271299-blue.svg)](https://shang.qq.com/wpa/qunwpa?idkey=e1ea16365440a9fa97ff72b0c73803e49a55dc68ae4c4181f3fb1da74928885e)  点击按钮入群。




**_改动内容_**

> application.yml
    
    # PageHelper分页插件
    pagehelper:
      helperDialect: oracle

> application-druid.yml
    
    driverClassName: oracle.jdbc.OracleDriver
    url: jdbc:oracle:thin:@127.0.0.1:1521/orcl
    username: ry
    password: ry
    
> pom.xml

     10.2.0.4.0 
     
         com.oracle 
         ojdbc14 
         ${oracle.version} 
     
     
     
         jeecg 
         jeecg Repository 
         http://maven.jeewx.com/nexus/content/repositories/jeecg 
         
             false 
         
     
    
> gen 模块

    参考 ruoyi-oracle，添加序列
        #if($pkColumn.increment)
        -- ${tableName}主键序列
        create sequence seq_${tableName}
        increment by 1
        start with 10
        nomaxvalue
        nominvalue
        cache 20;
        #end
    
    GenTable
        /** 菜单id **/
        private Long menuId;
        
    GenTableServiceImpl
        generatorCode()
        // 获取菜单id序列，用于生成菜单sql语句
        long menuId = genTableMapper.selectMenuId();
        table.setMenuId(menuId);
        
    参考 RuoYi-Oracle，修改为 Oracle 可用的格式，调整路径相关

> sql 文件和 xml 文件

    参考 RuoYi-Oracle，修改为 Oracle 可用的格式
    修改表 sys_oper_log 的 oper_param 和 json_result 为 varchar2(4000)
    `ry_yyyymmdd(更新日期).sql`，此文件中的 function find_in_set，请在 sql 窗口单独执行

> User.java 和 Menu.java
    
    return StringUtils.isEmpty(avatar) ? StringUtils.EMPTY : avatar;
    return StringUtils.isEmpty(perms) ? StringUtils.EMPTY : perms;
    处理数据库对应的列默认值 NULL
     
    
> ScheduleConfig.java

    prop.put("org.quartz.jobStore.txIsolationLevelSerializable", "false");
    
> 代码生成测试用 Oracle 数据，请参考 [若依文档-代码生成](http://doc.ruoyi.vip/ruoyi/document/htsc.html#%E4%BB%A3%E7%A0%81%E7%94%9F%E6%88%90)  
    (表对应的序列 seq_tableName，在生成的 Xxx.sql 文件中有生成)
    
    新建数据库表结构（单表-Oracle）
    create table sys_student (
      student_id           number(11),
      student_name         varchar2(30)             default '',
      student_age          number(3)      	        default null,
      student_sex          varchar2(1)    	        default '0',
      student_status       varchar2(1)    	        default '0',
      student_birthday     date,
      remark               varchar2(500)            default null 
    );
    alter table sys_student add constraint pk_sys_student primary key (student_id);
    comment on table  sys_student                   is '学生名称';
    comment on column sys_student.student_id      	is '学生主键seq_sys_student.nextval';
    comment on column sys_student.student_name    	is '学生名称';
    comment on column sys_student.student_age    	is '年龄';
    comment on column sys_student.student_sex    	is '性别（0男 1女 2未知）';
    comment on column sys_student.student_status    is '状态（0正常 1停用）';
    comment on column sys_student.student_birthday  is '生日';
    comment on column sys_student.remark            is '备注';
    
    新建数据库表结构（树表-Oracle）
    create table sys_product (
      product_id        number(20)                  not null,
      parent_id         number(20)                  default 0,
      product_name      varchar2(30)                default '',
      order_num         number(4)                   default 0,
      status            varchar2(1)                 default '0'
    );
    alter table sys_product add constraint pk_sys_product primary key (product_id);
    comment on table  sys_product                   is '产品表';
    comment on column sys_product.product_id        is '产品id主键seq_sys_product.nextval';
    comment on column sys_product.parent_id         is '父产品id';
    comment on column sys_product.product_name      is '产品名称';
    comment on column sys_product.order_num         is '显示顺序';
    comment on column sys_product.status            is '产品状态（0正常 1停用）';

> 杂项

    添加 PermissionUtils.getPrincipalProperty(property)



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)