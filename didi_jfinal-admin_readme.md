### jfinal-admin 后台框架 
基于JFinal的后台管理系统，采用了简洁强大的JFinal作为web框架，模板引擎用的是beetl，数据库用mysql，前端bootstrap框架。

- 演示地址 http://jad.yxyun.win/jadmin
- 密码 123456
- api文档 https://apidoc.gitee.com/supyuan/jfinal-admin/

### 特性
1. 内置用户和权限系统
2. mysql、oracle等多数据库支持
3. 支持引入第三方前端库
4. 基于jfinal_cms深度精简
5. 集成spring(可选)
6. 菜单权限、功能权限双重保障

### 部署重要说明
需要jdk7及以上环境支撑，需要maven最好用idea部署，系统默认密码123456


### 最新更新
- 1.菜单栏xss漏洞修复
- 2.废弃dubbo注解的方式集成spring，提供spring集成开关配置默认关闭
- 3.角色授权bug修复
- 4.合并任务调度（QuickJob [QuickJob ](https://gitee.com/supyuan/QuickJob)）
- 5.新增 XSS 脚本处理功能，示例 : ${nameHtml,xss}
- 6.修复个别情况下，当前页数大于总页数时，分页的 bug
- 7.权限控制精准到功能按钮
- 8.全新登录界面
- 9.全新404、500页面
- 10.任务调度合并到system模块，修复登录404的问题、beetl模板升级到2.7.14
- 11.seo优化，basePath端口是80的时候不显示
- 12.任务管理bug修复
- 13.des加密密钥问题修复

### 更新日志
- 2018年7月12日
- 功能更新 
      修复任务调度配置时执行类参数获取不正确的bug 修复DES秘钥初始化的bug 
- 次要调整 
      系统提示美化更新，操作提示改为layer.msg；
- 2018年4月18日
- 细节调整 
      任务调度合并到system模块，修复登录404的问题、beetl模板升级到2.7.14 
- 次要调整 
      seo优化，basePath端口是80的时候不显示；
- 2018年2月7日
- 主要更新
	由于linux下使用javaassist的反射方法获取方法的参数名时，获取的参数名与实际参数名不一致。
本次更新使用spring 方式替代了javaassist，感兴趣的小伙伴可以查阅源码修改的两处源码分别是：
QuartzJobClassSvc 106至142行
GetParamUtil 102至150行
- 次要更新
	1、修复未登录情况时，直接前往某个路由报错问题，UserInterceptor.java移动到系统基础部分；
	
![输入图片说明](https://gitee.com/uploads/images/2017/1215/094356_924f59cf_22738.png "1.png")
![输入图片说明](https://gitee.com/uploads/images/2017/1215/094408_27becaa2_22738.png "2.png")
![输入图片说明](https://gitee.com/uploads/images/2017/1215/094417_2dcf7299_22738.png "3.png")
![](https://git.oschina.net/uploads/images/2017/0516/223055_56ede065_22738.png "在这里输入图片标题")


### 其他
jfinal_cms深度精简，不再依赖jflyfox_base，jflyfox_jfinal。

### 代码质量分析
![输入图片说明](https://gitee.com/uploads/images/2017/1103/105801_c6f199f4_22738.png "fx3.png")

### 界面预览
![输入图片说明](https://gitee.com/uploads/images/2017/1103/110136_c846750a_22738.png "2017-11-03_110222.png")

### 配置说明
- 数据库连接配置 修改pom.xml
```
 

         

             develop 

             

                 true 

             

             

                 
                      

                 root 

                 123456 

             

         

     
```
- 登录系统账号 admin/123456
- spring使用
第一步 CONSTANTS.SPRING=false 开启
第二步 继承 BaseProjectController 调用 getClassBeanByName("classname") 即可获取spring管理的bean对象


### 鸣谢
- [JFinal](http://www.oschina.net/p/jfinal)

- [beetl](http://ibeetl.com/)

- [flyfox](http://git.oschina.net/flyfox)

### 关于作者
- IT小香猪(qq:454979901)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)