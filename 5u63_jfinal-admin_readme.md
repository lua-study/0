### jfinal-admin 后台框架 
jfinal-admin 是基于JFinal的后台管理系统，采用了简洁强大的JFinal作为web框架，模板引擎用的是beetl，数据库用mysql，前端bootstrap框架。

- 测试地址 http://yxyun.win/jadmin
- admin
- 123456
- 不要删除内置数据

### 部署重要说明
需要jdk7及以上环境支撑，需要maven最好用idea部署


### 最新更新
- 1.菜单栏xss漏洞修复
- 2.废弃dubbo注解的方式集成spring，提供spring集成开关配置默认关闭
- 3.角色授权bug修复


### 更新日志 如图
![](https://git.oschina.net/uploads/images/2017/0516/223055_56ede065_22738.png "在这里输入图片标题")


### 特性
1. 内置用户和权限系统
2. mysql、oracle等多数据库支持
3. 支持引入第三方前端库
4. 基于jfinal_cms深度精简
5. 集成spring(可选)

### 其他
jfinal_cms深度精简，不再依赖jflyfox_base，jflyfox_jfinal。

### 效果截图
![输入图片说明](http://static.oschina.net/uploads/img/201601/28091447_rQtD.gif "在这里输入图片标题")
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