springboot+mybatis+beetl开发的一款CMS，支持自定义内容模型、模板标签、全站静态化等功能（功能不断完善中.....）
QQ交流群:1482196
# Quick Start
##### 1、将sql目录下db.sql导入本地数据库，修改resources目录下的plication.properties配置文件。
![](https://raw.githubusercontent.com/westboy/CicadasCms/master/CicadasCms/doc/s1.png)
![](https://raw.githubusercontent.com/westboy/CicadasCms/master/CicadasCms/doc/s2.png)
##### 2、 运行CmsApplication类下main方法启动项目（超级管理员：admin，密码：123456）

![后台首页](https://raw.githubusercontent.com/westboy/CicadasCms/master/CicadasCms/doc/index.png "后台首页")
![内容管理](https://static.oschina.net/uploads/space/2017/0818/172741_OaDV_1409333.png "内容管理")
![内容管理](https://static.oschina.net/uploads/space/2017/0818/172843_eANP_1409333.png "内容管理")
![站点管理](https://static.oschina.net/uploads/space/2017/0818/172606_58lG_1409333.png "站点管理")
![定时任务](https://static.oschina.net/uploads/space/2017/0818/172806_vCHS_1409333.png "定时任务")
![模板管理](https://static.oschina.net/uploads/space/2017/0818/172932_JFLd_1409333.png "模板管理")
##### 3、 演示地址[使用博客模版做的博客网站]（账号：testdemo1，密码：testdemo1）
###### 前台：http://demo.westboy.net
###### 后台：http://demo.westboy.net/admin/login
# Other
##### 1、相关技术
> springboot
、mybatis
、[beetl](http://www.ibeetl.com "beetl")
、shiro
、[mybatis通用mapper](http://git.oschina.net/free/Mapper "通用mapper")（整合maven方式代码生成）
、[七牛云存储](https://portal.qiniu.com/signup?code=3lb7ah8vdj0ia "七牛云存储")
、[B-JUI v1.2](http://www.b-jui.com/download/ "B-JUI v1.2")
##### 2、栏目列表标签
```html
   
                @if(isNotEmpty(category)&&category.categoryId==bean.categoryId){
                 ${bean.categoryName!} 
                @}else{
                 ${bean.categoryName!} 
                @}
 
```
##### 3、栏目标签
```html
   
         分类：【 ${bean.categoryName!} 】 
  
```
##### 4、内容列表标签
```html
     
             
                  ${content.title!}  
                @if(isEmpty(content.thumb)){
                   
                @}else{
                   
                @}
                 
                     ${content.description!} 
                     阅读全文&gt;&gt; 
                 
                  作者：${content.author!} 

                     
                     分类：【 ${bean.categoryName!} 】 
                     

                     浏览（ ${content.viewNum!} ） 
                 
                 ${content.inputdate!,dateFormat="yyyy-MM-dd"} 
             
  
```
##### 5、内容分页标签（这个标签只能用在list页面）
```html
  
             
                 
                      ${content.title!}  
                     
                         作者：${content.author!} 
                     
                     分类：[ ${bean.categoryName!} ] 
                     
                         浏览（ ${content.viewNum!} ） 
                     
                     ${content.description!} 
                 
                @if(isEmpty(content.thumb)){
                   
                @}else{
                   
                @}
                 ${content.inputdate!,dateFormat="yyyy-MM-dd"} 
             
             
```
##### 6、分页标签
```html
  
                @//上一页
                @${page.last}
                @for( change in page.changePage){
                @if(!change.isLink){
                 ${change.value!} 
                @}else{
                ${change.url!}
                @}
                @}
                @//下一页
                @${page.next}
 
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)