## 6.0.0 项目入口是springrain-system-web,基于Istio实现微服务,正在整理文档.
## 6.0.0 基于VUE前后端分离,使用JWT认证.前端项目是[springrain-vue](https://gitee.com/chunanyong/springrain-vue)

## 实现了什么?
* 不增加学习成本,像单体一样开发分布式微服务.
* 不修改业务代码,可以实现单体,分层,微服务多种部署模式切换.
* 集成seata分布式事务实现. 

## 实现思路
* 启动加载springbean时,先检查本地是否有实现,如果没有就启动GRPC远程调用.开发人员无感知.
* 基于seata分布式事务实现.支持有注解和无注解(开发人员无感知,理论上有不同步风险,个人感觉做好日志,风险不大)混合使用.
* 基于Istio实现微服务的发现,监控,熔断,限流.开发人员无感知.

## 限制
* 接口和实现的命名强制规范.
* 一个RPC接口只能有一个实现.
* 分布式事务,一定要避免A服务update表t,RPC调用B服务,B服务也update表t.这样A等待B结果,B等待A释放锁,造成死锁.
* 分布式无注解比较方便,理论上有不同步风险,个人感觉做好日志,风险不大
* Service层不可以使用Servlet API,例如 HttpRequest

## 体验单体到分层切换
* 修改springrain-system-web依赖springrain-system-service,不再依赖springrain-system-serviceimpl.
* springrain-system-serviceimpl添加springrain-grpc-server依赖,启用org.springrain.SystemServiceImplApplication的@SpringBootApplication注解
* seata-server的conf目录下file.conf,修改vgroup_mapping.my_test_tx_group = "default" 为 vgroup_mapping.seata_tx_group = "default",启动seata-server服务.
* 启动springrain-system-serviceimpl
* 启动springrain-system-web
* 访问http://127.0.0.1:8080/api/checkHealth

### 项目名为springrain[春雨]我的个人博客是 http://www.weicms.net  
### 文档
https://gitee.com/chunanyong/springrain/tree/master/springrain-system/springrain-system-web/doc   
### 代码生成器
https://gitee.com/chunanyong/springrain/tree/master/springrain-gencode   
### sql脚本
https://gitee.com/chunanyong/springrain/tree/master/springrain-system/springrain-system-web/sql   


springrain是spring/springboot的封装,springboot开发范例.

springrain是一个Maven项目,包含spring core,spring jdbc,spring mvc.

springrain自带代码生成器,能够生成对表的增删改查的逻辑代码,以及前台页面样式和js文件

项目只依赖spring,没有hibernate,struts,ibatis.

使用jwt认证.

数据库调优可以使用druid输出慢sql,比分析xml中的语句更直观,springrain所有的sql语句都使用Finder封装管理,只要查看Finder的引用即可.

一些测试案例：

```java
//就极简而言,一个数据库只需要一个Service,就可以管理这个数据库的任意一张表 
//@Test  查询基本类型
public void testObject() throws Exception{
       // Finder finder=new Finder("select id from t_user where 1=1 ");
        Finder finder=Finder.getSelectFinder(User.class,"id").append(" WHERE 1=1 "); 
         finder.append("and id=:userId ").setParam("userId", "admin");
        String id = baseDemoService.queryForObject(finder, String.class);
        System.out.println(id);

}

//@Test 查询一个对象
public void testObjectUser() throws Exception{
        //Finder finder=new Finder("select * from t_user where id=:userId order by id"); 
Finder finder=Finder.getSelectFinder(User.class).append(" WHERE id=:userId order by id desc "); 
        finder.setParam("userId", "admin");
        User u = baseDemoService.queryForObject(finder, User.class);
        System.out.println(u.getName());

}
//@Test 查询分页
public void testMsSql() throws Exception{
        //Finder finder=new Finder("select * from t_user order by id");
        Finder finder=Finder.getSelectFinder(User.class).append(" order by id desc ");
        Listlist = baseDemoService.queryForList(finder, User.class, new Page(2));
        System.out.println(list.size());
        for(User s:list){
         System.out.println(s.getName());
         }
}



//@Test 调用数据库存储过程
public void testProc() throws Exception{
        Finder finder=new Finder();
        finder.setParam("unitId", 0);
        finder.setProcName("proc_up");
        Map queryObjectByProc = (Map) baseDemoService.queryObjectByProc(finder);
        System.out.println(queryObjectByProc.get("#update-count-10"));
        

}

//@Test 调用数据库函数
public void testFunction() throws Exception{
        Finder finder=new Finder();
        finder.setFunName("fun_userId");
        finder.setParam("userId", "admin");
        String userName= baseDemoService.queryForObjectByByFunction(finder,String.class);
        System.out.println(userName);
}

```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)