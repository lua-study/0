# auto-code
欢迎使用auto-code代码自动生成引擎, 2.0重大升级.支持`单表`, `一对一`, `一对多` ,`多对多`代码生成  [源码地址](https://gitee.com/ztp/auto-code)

# 目录
1.  项目介绍 
    1.  项目的优势在哪里 
    2.  什么情况选择该项目 
    3.  为何会发起该项目 
    4.  如果您觉得项目还行.请点赞.您的支持是我最大的动力项目地址 
2.  集成教程 
    1.  使用教程 
        1.  准备工作 
        2.  单表生成 
        3.  一对一代码生成 one-to-one 
        4.  一对多 代码生成 one-to-Many 
        5.   多对多 代码生成 many-to-many 
    2.   生成代码注意事项 
        1.   spring-boot如何使用 
        2.   java-web 
3.  进阶篇 如何自定义方法 
    1.  单表如何自定义 
    2.  表关系自定义 


##  项目介绍 
###  项目的优势在哪里 

> 1.目前市面上的代码生成工具绝大多数仅仅支持生成单表,该项目支持 `单表`, `一对一`, `一对多` ,`多对多` 
代码生成.大大简化了开发的工作量

> 2.只要目前你的项目采用 springMVC+spring+mybatis架构的项目都适用(传统工程和springBoot工程都适用).
不管一次开发还是二次开发.该项目仅仅只是帮你生成单表以及多表的`增删改查`,不做任何底层的改动.

###  什么情况选择该项目 
> 1.该项目只生成接口(controller,service,serviceImpl,dao,xml),
不生成页面.所以如果项目是采用前后台分离,不需要写页面.该项目会适合你

> 2.如果还想生成页面请看该项目,这个项目基于本项目.扩展了页面生成.适合后台使用 [源码地址](https://gitee.com/ztp/auto-code-admin) 
 [演示地址](http://www.zengtengpeng.com/login/gotoLogin) 账号 `ztp`  密码 `111111`
 
###  为何会发起该项目?  

> 绝大多数时候我们都是在做`增删改查`.每次创建一张表.然后我们需要重新写一次增删改查,
写虽然简单,不过极度耗时(controller,server,serverImpl,dao,xml) 
    所以才有了该项目,该项目能帮助你减少70%的工作量,让你专注于业务的实现.

###  如果您觉得项目还行.请点赞.您的支持是我最大的动力[项目地址](https://gitee.com/ztp/auto-code) 

![start](http://images.zengtengpeng.com/auto-code/start.png)

##  集成教程 

> 集成非常简单,只需要在自己的web工程或者spring-boot工程引入jar包即可.jar包已经上传中央仓库,
不需要自己下载源码编译. 请直接在pom.xml写上下面的引用.就能在自己的工程中生成代码了.
```
     
         com.zengtengpeng 
         auto-code 
         2.0.1 
     
```

> spring-boot代码实例 [实例地址](https://gitee.com/ztp/auto-code-springboot-demo)

> 传统java-web代码实例 [实例地址](https://gitee.com/ztp/auto-code-web-demo)

###  使用教程 
####  准备工作 

>1 首先先准备数据库(理论上支持所有关系型数据库,目前只做了mysql的测试)

>2 创建数据库 auto_code (可以随意取名称,只要和下面yaml里面的数据库名称对应上就行)

>3 准备完毕,开始进入正题

####  单表生成 

>假设我们要生成一张单表
```sql
CREATE TABLE `test_code` (
  `id` int(11) NOT NULL AUTO_INCREMENT COMMENT '测试生成代码',
  `name` varchar(50) DEFAULT NULL COMMENT '名称',
  `age` int(3) DEFAULT NULL COMMENT '年龄',
  `status` int(2) DEFAULT NULL COMMENT '{"name":"状态","1":"启用","0":"禁用"}',
  `birthday` date DEFAULT NULL COMMENT '生日',
  `remarks` text COMMENT '备注',
  `create_time` datetime DEFAULT CURRENT_TIMESTAMP COMMENT '创建时间',
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=4 DEFAULT CHARSET=utf8 COMMENT='测试生成代码';
```

>1.先在资源根路径(src/main/resources)创建 auto-code_simple.yaml 文件,具体内容如下
```yaml
datasourceConfig:
    #驱动名称
    driverClassName: com.mysql.jdbc.Driver
    #数据库名称
    name: auto_code
    #jdbc链接
    url: jdbc:mysql://127.0.0.1:3306/auto_code
    #数据库用户名
    username: root
    #数据库密码
    password: 111111
globalConfig:
    #数据库表配置
    tableNames:
        #表名称
        - dataName: test_code
          #别名 不写默认采用驼峰命名法 test_code->TestCode
#          aliasName: SysLoginLog
          #如果用多张表,请按照如下写法,继续往下写.
#        - dataName: test_code2
#          aliasName: DDDDDDD
    #生成代码的项目路径
    parentPath: f:/core
    #生成代码的父包 如父包是com.zengtengpeng.test  controller将在com.zengtengpeng.test.controller下 bean 将在com.zengtengpeng.test.bean下 ,service,dao同理
    parentPack: com.zengtengpeng.test
    #是否覆盖生成文件 如果为true将会把以前的文件覆盖掉
    cover: false
    #xml存放的文件夹默认 mybatisMapper
    xmlPath: mybatisMapper
```

> 2.执行代码生成语句
```java
import com.zengtengpeng.autoCode.StartCode;

public class Demo1simple {
    public static void main(String[] args) {
        //lambda表达式写法 二选一
        StartCode startCode=t->{};
        //普通写法 二选一
//        StartCode startCode=new StartCode() {
//            @Override
//            public void custom(AutoCodeConfig autoCodeConfig) {
//
//            }
//        };
        startCode.start(StartCode.saxYaml("auto-code_simple.yaml"));
    }
}
```
>3.生成完毕 主要生成六个接口

    //根据id删除记录
    deleteByPrimaryKey
    
    //保存(主键为空则增加 否则 修改)
    save 
    
    //根据主键查询
    selectByPrimaryKey
    
    //根据条件查询(所有的实体属性都是条件,如果为空则忽略该字段)
    selectByCondition
    
    //分页查询 (所有的实体属性都是条件,如果为空则忽略该字段) 详见Page类.所以的实体都继承该类 默认page=1 pageSize=10
    selectAllByPaging
    
    //导出excel
    export
生成的文件如下:
![simple](http://images.zengtengpeng.com/auto-code/simple.png)

####  一对一代码生成 one-to-one (代码采用追加的方式.无需担心代码被覆盖)  

>假如 一个用户  test_user 一个用户 对应 test_class 一个班级
```sql
    CREATE TABLE `test_user` (
      `id` int(11) NOT NULL AUTO_INCREMENT COMMENT 'id',
      `name` varchar(50) DEFAULT NULL COMMENT '名称',
      `age` int(3) DEFAULT NULL COMMENT '年龄',
      `status` int(2) DEFAULT NULL COMMENT '{"name":"状态","1":"启用","0":"禁用"}',
      `birthday` date DEFAULT NULL COMMENT '生日',
      `remarks` text COMMENT '备注',
      `mun` decimal(20,2) DEFAULT NULL COMMENT '数字',
      `create_time` datetime DEFAULT CURRENT_TIMESTAMP COMMENT '创建时间',
      `update_time` datetime DEFAULT NULL ON UPDATE CURRENT_TIMESTAMP COMMENT '更新时间',
      PRIMARY KEY (`id`)
    ) ENGINE=InnoDB AUTO_INCREMENT=31 DEFAULT CHARSET=utf8 COMMENT='测试用户';

    CREATE TABLE `test_class` (
      `id` int(11) NOT NULL AUTO_INCREMENT COMMENT '班级id',
      `user_id` int(11) DEFAULT NULL COMMENT '用户id',
      `class_name` varchar(50) DEFAULT NULL COMMENT '班级名称',
      `quantity` int(11) DEFAULT NULL COMMENT '班级人数',
      `create_time` datetime DEFAULT CURRENT_TIMESTAMP,
      PRIMARY KEY (`id`)
    ) ENGINE=InnoDB AUTO_INCREMENT=6 DEFAULT CHARSET=utf8 COMMENT='班级'

```

>1.同理先在 资源根路径(src/main/resources)创建 auto-code_one-to-one.yaml 文件(名字随意定默认使用 auto-code.yaml),具体内容如下

    请注意relationConfig这里描述的是关系配置, 注意generate和existParentPackage字段.
    如果该表已经生成了.请将 generate置为 false 同时填写 existParentPackage 该表所对应的父包(一对多,多对多有实例)
    
```yaml
datasourceConfig:
    #驱动名称
    driverClassName: com.mysql.jdbc.Driver
    #数据库名称
    name: auto_code
    #jdbc链接
    url: jdbc:mysql://127.0.0.1:3306/auto_code
    #数据库用户名
    username: root
    #数据库密码
    password: 111111
globalConfig:
    #生成代码的项目路径
    parentPath: E:\resource\workspaceJDB\auto-code-springboot-demo
    #生成代码的父包 如父包是com.zengtengpeng.test  controller将在com.zengtengpeng.test.controller下 bean 将在com.zengtengpeng.test.bean下 ,service,dao同理
    parentPack: com.zengtengpeng.test
    #是否覆盖生成文件 如果为true将会把以前的文件覆盖掉
    cover: false
    #xml存放的文件夹默认 mybatisMapper
    xmlPath: mybatisMapper
    # 表关系配置  一对一 一对多 多对多 代码生成 采用追加的方式
    relationConfig:
        #主表
        primary:
            #数据库表名
            dataName: test_user
            #别名: 如果不设置将采用驼峰命名法 test_user=TestUser
            beanName: User
            #主键名称
            primaryKey: id
             #是否生成单表代码
#            generate: false
#如果单表代码已经生成,请填写代码的父包,没有则generate置为true 如 com.zengtengpeng.test.bean.TestUser  请填写 com.zengtengpeng.test
#            existParentPackage: com.zengtengpeng.test
            #备注
            remark: "用户"
        #外表
        foreign:
            #数据库表名
            dataName: test_class
            #别名: 如果不设置将采用驼峰命名法 test_user=TestUser
            beanName: Clazz
            #外键名称 就是已哪个字段和主表关联 填写数据库字段名称
            foreignKey: user_id
            #是否生成单表代码
#            generate: false
#如果单表代码已经生成,请填写代码的父包,没有则generate置为true 如 com.zengtengpeng.test.bean.TestUser  请填写 com.zengtengpeng.test
#            existParentPackage: com.zengtengpeng.test
            #备注
            remark: "班级"
```

> 2.执行代码

```java

import com.zengtengpeng.autoCode.StartCode;
import com.zengtengpeng.autoCode.config.AutoCodeConfig;
import com.zengtengpeng.relation.oneToOne.BuildOneToOne;
import com.zengtengpeng.relation.utils.RelationUtils;

import com.zengtengpeng.autoCode.StartCode;
import com.zengtengpeng.relation.utils.RelationUtils;

public class Demo2OneToOne {
    public static void main(String[] args) {
        //普通写法
//        RelationUtils.oneToOne(StartCode.saxYaml(), new StartCode() {
//            @Override
//            public void custom(AutoCodeConfig autoCodeConfig) {
//            }
//        }, new BuildOneToOne() {
//            @Override
//            public void custom(AutoCodeConfig autoCodeConfig) {
//            }
//        });
        //lambda表达式写法 二选一
        RelationUtils.oneToOne(StartCode.saxYaml("auto-code_one-to-one.yaml"), t->{}, rt -> {});
    }
}
```
> 3. 生成完毕 一对多会在单表的基础上再增加6个接口(采用追加代码的方式,不用担心代码覆盖问题) 主表3个 外表3个
ClazzController 新增
```
            /**
             * 级联查询(带分页) 用户--班级
             */
            @ResponseBody
            @RequestMapping("clazz/selectUserAndClazz")
            public DataRes selectUserAndClazz(Clazz clazz,HttpServletRequest request,HttpServletResponse response){
                return DataRes.success(clazzService.selectUserAndClazz(clazz));
            }
            /**
        	 * 级联条件查询 用户--班级
        	 */
        	@ResponseBody
        	@RequestMapping("clazz/selectUserAndClazzByCondition")
        	public DataRes selectUserAndClazzByCondition(Clazz clazz,HttpServletRequest request,HttpServletResponse response){
        		return DataRes.success(clazzService.selectUserAndClazzByCondition(clazz));
        	}
        	/**
        	 * 级联删除(根据主键删除) 用户--班级
        	 */
        	@ResponseBody
        	@RequestMapping("clazz/deleteUserAndClazz")
        	public DataRes deleteUserAndClazz(Clazz clazz,HttpServletRequest request,HttpServletResponse response){
        		return DataRes.success(clazzService.deleteUserAndClazz(clazz));
        	}
```
UserController 增加
```
                /**
            	 * 级联查询(带分页) 用户--班级
            	 */
            	@ResponseBody
            	@RequestMapping("user/selectUserAndClazz")
            	public DataRes selectUserAndClazz(User user,HttpServletRequest request,HttpServletResponse response){
            		return DataRes.success(userService.selectUserAndClazz(user));
            	}
            
            
            	/**
            	 * 级联条件查询 用户--班级
            	 */
            	@ResponseBody
            	@RequestMapping("user/selectUserAndClazzByCondition")
            	public DataRes selectUserAndClazzByCondition(User user,HttpServletRequest request,HttpServletResponse response){
            		return DataRes.success(userService.selectUserAndClazzByCondition(user));
            	}
            
            
            	/**
            	 * 级联删除(根据主键删除) 用户--班级
            	 */
            	@ResponseBody
            	@RequestMapping("user/deleteUserAndClazz")
            	public DataRes deleteUserAndClazz(User user,HttpServletRequest request,HttpServletResponse response){
            		return DataRes.success(userService.deleteUserAndClazz(user));
            	}
```
        	

生成的文件如下

![one-to-one](http://images.zengtengpeng.com/auto-code/one-to-one.png)

####  一对多 代码生成 one-to-Many (代码采用追加的方式.无需担心代码被覆盖) 

> 假如 test_user 一个用户 对应 test_addr 多个收货地址

```sql
    CREATE TABLE `test_user` (
      `id` int(11) NOT NULL AUTO_INCREMENT COMMENT 'id',
      `name` varchar(50) DEFAULT NULL COMMENT '名称',
      `age` int(3) DEFAULT NULL COMMENT '年龄',
      `status` int(2) DEFAULT NULL COMMENT '{"name":"状态","1":"启用","0":"禁用"}',
      `birthday` date DEFAULT NULL COMMENT '生日',
      `remarks` text COMMENT '备注',
      `mun` decimal(20,2) DEFAULT NULL COMMENT '数字',
      `create_time` datetime DEFAULT CURRENT_TIMESTAMP COMMENT '创建时间',
      `update_time` datetime DEFAULT NULL ON UPDATE CURRENT_TIMESTAMP COMMENT '更新时间',
      PRIMARY KEY (`id`)
    ) ENGINE=InnoDB AUTO_INCREMENT=31 DEFAULT CHARSET=utf8 COMMENT='测试用户';

    CREATE TABLE `test_addr` (
      `id` int(11) NOT NULL AUTO_INCREMENT COMMENT '用户收货地址id',
      `user_id` int(11) DEFAULT NULL COMMENT '用户id',
      `addr_name` varchar(10) DEFAULT NULL COMMENT '姓名',
      `phone` varchar(30) DEFAULT NULL COMMENT '手机号码',
      `addr` varchar(30) DEFAULT NULL COMMENT '收货地址',
      `status` int(11) DEFAULT NULL COMMENT '{"name":"状态","1":"启用","2":"删除"}',
      `create_time` datetime DEFAULT NULL COMMENT '创建时间',
      `update_time` datetime DEFAULT NULL COMMENT '更新时间',
      PRIMARY KEY (`id`)
    ) ENGINE=InnoDB AUTO_INCREMENT=2 DEFAULT CHARSET=utf8 COMMENT='用户收货地址'
``` 

>1.同理先在 资源根路径(src/main/resources)创建 auto-code_one-to-many.yaml 文件,具体内容如下
    
    由于TestUser已经在一对一生成过代码了.所以 generate: false
    同时写上已经存在的父包 existParentPackage: com.zengtengpeng.test
```yaml
    datasourceConfig:
        #驱动名称
        driverClassName: com.mysql.jdbc.Driver
        #数据库名称
        name: auto_code
        #jdbc链接
        url: jdbc:mysql://127.0.0.1:3306/auto_code
        #数据库用户名
        username: root
        #数据库密码
        password: 111111
    globalConfig:
        #生成代码的项目路径
        parentPath: E:\resource\workspaceJDB\auto-code-springboot-demo
        #生成代码的父包 如父包是com.zengtengpeng.test  controller将在com.zengtengpeng.test.controller下 bean 将在com.zengtengpeng.test.bean下 ,service,dao同理
        parentPack: com.zengtengpeng.test
        #是否覆盖生成文件 如果为true将会把以前的文件覆盖掉
        cover: false
        #xml存放的文件夹默认 mybatisMapper
        xmlPath: mybatisMapper
        # 表关系配置  一对一 一对多 多对多 代码生成 采用追加的方式
        relationConfig:
            #主表
            primary:
                #数据库表名
                dataName: test_user
                #别名: 如果不设置将采用驼峰命名法 test_user=TestUser
                beanName: User
                #主键名称
                primaryKey: id
                #是否生成单表代码
                generate: false
    #如果单表代码已经生成,请填写代码的父包,没有则不填写 如 com.zengtengpeng.test.bean.TestUser  请填写 com.zengtengpeng.test
                existParentPackage: com.zengtengpeng.test
                #备注
                remark: "用户"
            #外表
            foreign:
                #数据库表名
                dataName: test_addr
                #别名: 如果不设置将采用驼峰命名法 test_user=TestUser
                beanName: Addr
                #外键名称 就是已哪个字段和主表关联 填写数据库字段名
                foreignKey: user_id
                #是否生成单表代码 默认是true
                #            generate: true
                #如果单表代码已经生成,请填写代码的父包,没有则不填写 如 com.zengtengpeng.test.bean.TestUser  请填写 com.zengtengpeng.test
                #            existParentPackage: com.zengtengpeng.test
                #备注
                remark: "收货地址"
    
```

> 2.执行生成代码
```java
    import com.zengtengpeng.autoCode.StartCode;
    import com.zengtengpeng.relation.utils.RelationUtils;
    /**
     * 一对多生成实例 test_user 一个用户 对应 test_addr 多个收货地址
     */
    public class Demo3OneToMany {
        public static void main(String[] args) {
            //普通写法 二选一
    //        RelationUtils.oneToMany(StartCode.saxYaml(), new StartCode() {
    //            @Override
    //            public void custom(AutoCodeConfig autoCodeConfig) {
    //
    //            }
    //        }, new BuildOneToMany() {
    //            @Override
    //            public void custom(AutoCodeConfig autoCodeConfig) {
    //
    //            }
    //        });
            //lambda表达式写法 二选一
            RelationUtils.oneToMany(StartCode.saxYaml("auto-code_one-to-many.yaml"), t -> {}, rt -> {});
        }
    }
```

> 3.生成完毕 接口和一对一一样


####  多对多 代码生成 many-to-many (代码采用追加的方式.无需担心代码被覆盖) 
    
> 假如 test_user 多个用户 对应 test_role 多个角色

```sql
    CREATE TABLE `test_user` (
      `id` int(11) NOT NULL AUTO_INCREMENT COMMENT 'id',
      `name` varchar(50) DEFAULT NULL COMMENT '名称',
      `age` int(3) DEFAULT NULL COMMENT '年龄',
      `status` int(2) DEFAULT NULL COMMENT '{"name":"状态","1":"启用","0":"禁用"}',
      `birthday` date DEFAULT NULL COMMENT '生日',
      `remarks` text COMMENT '备注',
      `mun` decimal(20,2) DEFAULT NULL COMMENT '数字',
      `create_time` datetime DEFAULT CURRENT_TIMESTAMP COMMENT '创建时间',
      `update_time` datetime DEFAULT NULL ON UPDATE CURRENT_TIMESTAMP COMMENT '更新时间',
      PRIMARY KEY (`id`)
    ) ENGINE=InnoDB AUTO_INCREMENT=31 DEFAULT CHARSET=utf8 COMMENT='测试用户';

    CREATE TABLE `test_role` (
      `id` int(11) NOT NULL AUTO_INCREMENT COMMENT '测试角色',
      `name` varchar(100) NOT NULL COMMENT '角色名称',
      `status` int(2) DEFAULT '0' COMMENT '{"name":"状态","0":"启用","1":"禁用"}',
      `create_user_id` int(11) DEFAULT NULL COMMENT '创建者',
      `create_time` datetime DEFAULT CURRENT_TIMESTAMP COMMENT '创建时间',
      `update_user_id` int(11) DEFAULT NULL COMMENT '更新者',
      `update_time` datetime DEFAULT NULL ON UPDATE CURRENT_TIMESTAMP COMMENT '更新时间',
      `dels` int(2) DEFAULT '0' COMMENT '{"name":"是否删除","0":"正常","1":"删除"}',
      PRIMARY KEY (`id`)
    ) ENGINE=InnoDB AUTO_INCREMENT=5 DEFAULT CHARSET=utf8 COMMENT='测试角色';
    
    CREATE TABLE `test_user_role` (
      `id` int(11) NOT NULL AUTO_INCREMENT COMMENT '用户角色关系表',
      `user_id` int(11) DEFAULT NULL COMMENT '用户id',
      `role_id` int(11) DEFAULT NULL COMMENT '角色id',
      `create_time` datetime DEFAULT CURRENT_TIMESTAMP COMMENT '创建时间',
      PRIMARY KEY (`id`)
    ) ENGINE=InnoDB AUTO_INCREMENT=55 DEFAULT CHARSET=utf8 COMMENT='测试用户角色';
```

> 1.同理先在 资源根路径(src/main/resources)创建 auto-code.yaml 文件,具体内容如下
      
      1.由于TestUser已经在一对一生成过代码了.所以 generate: false 同时写上
      TestUser存在的父包 existParentPackage: com.zengtengpeng.test
      2.注意多对多的外表的 foreignKey 同样是该表的主键
      3.thirdparty为多对多的第三表primaryKey对应主表(primary)的primaryKey. 
      foreignKey对应外表(foreign)的foreignKey

```yaml
    datasourceConfig:
        #驱动名称
        driverClassName: com.mysql.jdbc.Driver
        #数据库名称
        name: auto_code
        #jdbc链接
        url: jdbc:mysql://127.0.0.1:3306/auto_code
        #数据库用户名
        username: root
        #数据库密码
        password: 111111
    globalConfig:
        #生成代码的项目路径
        parentPath: E:\resource\workspaceJDB\auto-code-springboot-demo
        #生成代码的父包 如父包是com.zengtengpeng.test  controller将在com.zengtengpeng.test.controller下 bean 将在com.zengtengpeng.test.bean下 ,service,dao同理
        parentPack: com.zengtengpeng.test
        #是否覆盖生成文件 如果为true将会把以前的文件覆盖掉
        cover: false
        #xml存放的文件夹默认 mybatisMapper
        xmlPath: mybatisMapper
        # 表关系配置  一对一 一对多 多对多 代码生成 采用追加的方式
        relationConfig:
            #主表
            primary:
                #数据库表名
                dataName: test_user
                #别名: 如果不设置将采用驼峰命名法 test_user=TestUser
                beanName: User
                #主键名称
                primaryKey: id
                #是否生成 单表 代码
                generate: false
                #如果单表代码已经生成,请填写代码的父包 如 com.zengtengpeng.test.bean.TestUser  请填写 com.zengtengpeng.test
                existParentPackage: com.zengtengpeng.test
                #备注
                remark: "用户"
            #外表
            foreign:
                #数据库表名
                dataName: test_role
                #别名: 如果不设置将采用驼峰命名法 test_user=TestUser
                beanName: Role
                #外键名称 就是已哪个字段和主表关联 填写数据库字段名
                foreignKey: id
                #备注
                remark: "角色"
            #第三表 -当生成多对多代码时该参数必填.否则会忽略该参数
            thirdparty:
                #数据库表名
                dataName: test_user_role
                #主键名称 该字段将和主表关联起来
                primaryKey: user_id
                #外键名称 该字段将和外表配置关联起来
                foreignKey: role_id
                #备注
                remark: "用户角色"
```
> 2 .执行代码
```java
import com.zengtengpeng.autoCode.StartCode;
import com.zengtengpeng.relation.utils.RelationUtils;

/**
 * 多对多生成实例 test_user 多个用户 对应 test_role 多个角色
 */
public class Demo4ManyToMany {
    public static void main(String[] args) {
        //普通写法
        /*RelationUtils.manyToMany(StartCode.saxYaml(), new StartCode() {
            @Override
            public void custom(AutoCodeConfig autoCodeConfig) {

            }
        }, new BuildManyToMany() {
            @Override
            public void custom(AutoCodeConfig autoCodeConfig) {

            }
        });*/
        //lambda表达式写法 二选一
        RelationUtils.manyToMany(StartCode.saxYaml("auto-code_many-to-many.yaml"), t->{}, rt -> {});
    }
}
```    

> 3.生成完毕 接口在一对一的基础上增加了2个方法
主表
```
//根据外表id查询主表表所有数据(带分页)
@RequestMapping("testUs/selectTestUsByTestRo")
	@ResponseBody
	public DataRes selectTestUsByTestRo(HttpServletRequest request,HttpServletResponse response,TestUs testUs){
		return DataRes.success(testUsService.selectTestUsByTestRo(testUs));
	}
```
外表
```
    /**
    	 * 根据主表id查询外表所有数据(带分页)
    	 */
    	@Auth("testRo/selectAllByPaging")
    	@RequestMapping("testRo/selectTestRoByTestUs")
    	@ResponseBody
    	public DataRes selectTestRoByTestUs(HttpServletRequest request,HttpServletResponse response,TestRo testRo){
    		return DataRes.success(testRoService.selectTestRoByTestUs(testRo));
    	}
```
###  生成代码注意事项  

    1.创建表结构时如果写上表与字段的注释将大大增加程序的可读性.我会将注释写到bean上面.
    2.配置文件 auto-code.yaml名称随意定.默认使用 auto-code.yaml 当使用 auto-code.yaml时
    StartCode.saxYaml("auto-code_many-to-many.yaml") 可以直接写成 StartCode.saxYaml().
    4.如果注释为json键值对字符串我将会在实体类生成一个字典方法
    如:  {"1":"启用","0":"禁用"} 将会在实体类里面生成:
        public String getStatus_(){
    		if(MyStringUtils.isEmpty(status)){
    			 return "";
    		}else if(status.equals("1")){
    			return "启用";
    		}else if(status.equals("0")){
    			return "禁用";
    		}
    		return "";
    
    	}


####  spring-boot如何使用  [实例地址](https://gitee.com/ztp/auto-code-springboot-demo)

> 1.集成mybatis-spring-boot-starter,spring-boot-starter-web 这里就不再阐述

>2.由于分页插件使用了 pageHelper 所以需要集成下,不集成将导致分页失效,集成非常简单 
 [官方SpringBoot集成地址](https://github.com/abel533/MyBatis-Spring-Boot) 

    1.加入pom.xml jar包
     
         com.github.pagehelper 
         pagehelper-spring-boot-starter 
         1.2.10 
     
    
    2.在application.properties加入配置
    #pagehelper插件
    #logging.level.com.example.demo.dao=DEBUG
    pagehelper.helperDialect=mysql
    pagehelper.reasonable=true
    pagehelper.supportMethodsArguments=true
    pagehelper.params=count=countSql
    pagehelper.page-size-zero=true
    
    3.至此集成完毕

####  java-web  [实例地址](https://gitee.com/ztp/auto-code-web-demo)

> 由于分页插件使用了 pageHelper 所以需要集成下,不集成将导致分页失效
 [官方传统web工程集成地址](https://github.com/abel533/Mybatis-Spring)

    1.由于工程中以及引入pageHelper的jar包所以直接在
    MyBatis-Configuration.xml中加入
     
         
         
     
    
    2.集成完毕
    

##  进阶篇 如何自定义方法  [代码地址](https://gitee.com/ztp/auto-code-springboot-demo)

###  单表如何自定义 
> 在 `com.zengtengpeng.autoCode.create`包下,有6个接口类 `BuildBean`,`BuildController`,`BuildDao`,`BuildService`,
`BuildServiceImpl`,`BuildXml`.每个接口底下都有个未实现的 `custom` 方法. 实现custom就可以,如下代码就是自定义Controller代码,其他的接口同理
```java
import com.zengtengpeng.autoCode.bean.BuildJavaField;
import com.zengtengpeng.autoCode.bean.BuildJavaMethod; import com.zengtengpeng.autoCode.config.AutoCodeConfig;
import com.zengtengpeng.autoCode.config.BuildJavaConfig;
import com.zengtengpeng.autoCode.create.BuildController;

import java.util.ArrayList;
import java.util.List;

/**
 * 重写controller 自定义配置
 */
public class TestBuildController implements BuildController {
    @Override
    public BuildJavaConfig custom(AutoCodeConfig autoCodeConfig) {
        BuildJavaConfig buildJavaConfig=new BuildJavaConfig();
        List  imports=new ArrayList<>();
        imports.add("java.util.HashMap");
        imports.add("java.util.Hashtable");
        imports.add("java.util.Collections");
        //自定义需要导入的类
        buildJavaConfig.setImports(imports);

        List  methods=new ArrayList<>();
        BuildJavaMethod method=new BuildJavaMethod();
        method.setContent("\nSystem.out.println(\"生成完毕\");");
        method.setMethodName("test");
        method.setMethodType("public");
        method.setReturnType("void");
        List  params=new ArrayList<>();
        params.add("String test");
        method.setParams(params);
        method.setRemark("测试生成方法");
        List  ann=new ArrayList<>();
        ann.add("@SuppressWarnings(\"\")");
        method.setAnnotation(ann);
        methods.add(method);
        //自定义方法 将在类生成如下方法
        //@SuppressWarnings("")
        //	public void test(String test){
        //
        //System.out.println("生成完毕");
        //	}
        buildJavaConfig.setBuildJavaMethods(methods);

        List  fileds=new ArrayList<>();
        BuildJavaField jf=new BuildJavaField();
        jf.setFiledType("private");
        jf.setReturnType("String");
        jf.setFiledName("test");
        jf.setRemark("测试生成字段");
        jf.setInit("\"初始化字段\"");
        ann=new ArrayList<>();
        ann.add("@SuppressWarnings(\"\")");
        jf.setAnnotation(ann);
        fileds.add(jf);
        //自定义字段 将在类生成如下字段
        //@SuppressWarnings("")
        //	private String test ="初始化字段";
        buildJavaConfig.setBuildJavaFields(fileds);

        //自定义继承 类单继承 接口多继承
        List  ex=new ArrayList<>();
        ex.add("Object");
        buildJavaConfig.setExtend(ex);

        //自定义 实现 类多实现, 接口没有实现
//                    buildJavaConfig.setImplement(null);

        return buildJavaConfig;
    }
}
```
> StartCode 为生成单表的总开关,里面有 `BuildBean`,`BuildController`,`BuildDao`,`BuildService`,
`BuildServiceImpl`,`BuildXml` 几个接口的默认实现.如需自定义,重写默认实现的方法.
```java
/**
 * 自定义单表方法
 */
public class CustomSimple {

    public static void main(String[] args) {
        StartCode startCode=new StartCode() {
            @Override
            public void custom(AutoCodeConfig autoCodeConfig) {
            }
            
            @Override
            public BuildController BuildController() {
                //自定义Controller方法
                return new TestBuildController();
            }

        };
        startCode.start(StartCode.saxYaml("auto-code_simple.yaml"));
    }
}
```
###  表关系自定义 

> 表关系在单表的基础上扩展了 主表,外表 代码在 `com.zengtengpeng.relation` 下的 `manyToMany`(多对多),`oneToMany`(一对多),
`oneToOne`(一对一)子包,每个子包有六个生成类的接口.重写也是只需要实现对应的接口的
`custom` 方法就行.下面举例重写一对一的controller方法
```java
import com.zengtengpeng.autoCode.bean.BuildJavaField;
import com.zengtengpeng.autoCode.bean.BuildJavaMethod;
import com.zengtengpeng.autoCode.config.AutoCodeConfig;
import com.zengtengpeng.autoCode.config.BuildJavaConfig;
import com.zengtengpeng.relation.oneToOne.BuildOneToOneController;

import java.util.ArrayList;
import java.util.List;

/**
 * 自定义one-to-one controller
 */
public class TestBuildOneToOneController implements BuildOneToOneController {

    @Override
    public void custom(AutoCodeConfig autoCodeConfig, BuildJavaConfig primaryBuildJavaConfig, BuildJavaConfig foreignBuildJavaConfig) {
        List  imports=new ArrayList<>();
        imports.add("java.util.HashMap");
        imports.add("java.util.Hashtable");
        imports.add("java.util.Collections");
        //自定义需要导入的类
        primaryBuildJavaConfig.setImports(imports);

        List  methods=new ArrayList<>();
        BuildJavaMethod method=new BuildJavaMethod();
        method.setContent("\nSystem.out.println(\"生成完毕\");");
        method.setMethodName("test");
        method.setMethodType("public");
        method.setReturnType("void");
        List  params=new ArrayList<>();
        params.add("String test");
        method.setParams(params);
        method.setRemark("测试生成方法");
        List  ann=new ArrayList<>();
        ann.add("@SuppressWarnings(\"\")");
        method.setAnnotation(ann);
        methods.add(method);
        //自定义方法 将在类生成如下方法
        //@SuppressWarnings("")
        //	public void test(String test){
        //
        //System.out.println("生成完毕");
        //	}
        primaryBuildJavaConfig.setBuildJavaMethods(methods);


        List  fileds=new ArrayList<>();
        BuildJavaField jf=new BuildJavaField();
        jf.setFiledType("private");
        jf.setReturnType("String");
        jf.setFiledName("test");
        jf.setRemark("测试生成字段");
        jf.setInit("\"初始化字段\"");
        ann=new ArrayList<>();
        ann.add("@SuppressWarnings(\"\")");
        jf.setAnnotation(ann);
        fileds.add(jf);
        //自定义字段 将在类生成如下字段
        //@SuppressWarnings("")
        //	private String test ="初始化字段";
        primaryBuildJavaConfig.setBuildJavaFields(fileds);

        //自定义继承 类单继承 接口多继承
        List  ex=new ArrayList<>();
        ex.add("Object");
        primaryBuildJavaConfig.setExtend(ex);
    }
}
```
> `BuildManyToMany`(构建多对多),`BuildOneToMany`(构建一对多),`BuildOneToOne`(构建一对一) 是各个表关系实现的总开关.
里面有 `Build...Controller` `Build...Bean` 等六个相关接口的具体实现.我们也是只要重写对应的方法就行
如下重写一对一的controller.只需要重写 `BuildOneToOne`下的 `buildOneToOneController`具体实现即可.其他的同理

```java
    import com.zengtengpeng.autoCode.StartCode;
    import com.zengtengpeng.autoCode.config.AutoCodeConfig;
    import com.zengtengpeng.demo.test.TestBuildOneToOneController;
    import com.zengtengpeng.relation.oneToOne.BuildOneToOne;
    import com.zengtengpeng.relation.oneToOne.BuildOneToOneController;
    import com.zengtengpeng.relation.utils.RelationUtils;
    
    /**
     * 多表自定义
     */
    public class CustomRelation {
        public static void main(String[] args) {
            //如果单表想要自定义请参见 CustomSimple 类. 里面是如果定义单表的
            StartCode startCode = t -> { };
    
            //多表自定义
            BuildOneToOne buildOneToOne = new BuildOneToOne() {
                @Override
                public void custom(AutoCodeConfig autoCodeConfig) {
    
                }
                @Override
                public BuildOneToOneController buildOneToOneController() {
                    //Controller autoCodeConfig 全局配置 primaryBuildJavaConfig主表的自定义配置  foreignBuildJavaConfig 外表的自定义配置
                    return new TestBuildOneToOneController();
                }
            };
            RelationUtils.oneToOne(StartCode.saxYaml("auto-code_one-to-one.yaml"), startCode, buildOneToOne);
        }
    }
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)