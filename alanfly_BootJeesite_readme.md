# BootJeesite
jeesite的springboot版本 同时加入一些其他优秀插件

项目页面为jsp模式

项目默认使用h2内存数据库自动插入数据（代码生成模块除外）只需maven包下载完成以后运行即可，项目会随时更新

项目博客：http://blog.sina.com.cn/timoer

项目演示：http://bootjh.butterfly.mopaasapp.com/test 

如发现无法登陆一直卡错误界面http://bootjh.butterfly.mopaasapp.com/test/a/logout

账户：admin 密码:admin 

QQ群：414089039 

项目默认访问路径localhost:8080/test

数据库访问路径 http://127.0.0.1:8082/login.do?jsessionid=05482a112348ec5e7759612370ef1428

数据库url地址  jdbc:h2:file:~/h2/testdb 

账户：admin 密码：admin

H—UI页面
![输入图片说明](https://gitee.com/uploads/images/2018/0109/145310_42719dcd_731572.png "14AF9C44-1432-4D76-B51F-9697E2C3895B.png")
hui版本 从附件和发行版本中下载

当前版本为layui基础版本 

![输入图片说明](https://gitee.com/uploads/images/2018/0112/181221_6e5ade6d_731572.png "v.png")

2018年01月12日18:10:15 更新加入用户layui实例页面（功能已实现） 效果图

![输入图片说明](https://gitee.com/uploads/images/2018/0112/181041_c19a2ad7_731572.png "a.png")

2018年4月20日16:03:24

菜单管理和权限管理已添加-并修复权限不正确的问题--注意查看博客自行修改资源访问路径
问题描述：http://blog.sina.com.cn/s/blog_d06cca100102xqwi.html
![输入图片说明](https://gitee.com/uploads/images/2018/0420/160644_1ca2f381_731572.png "]MJJYD4F@I0(L8W19A)`H52.png")

2018年4月26日12:01:24

代码生成模块新增

关于代码生成模块--在使用代码生成模块时请先运行sql文件创建表---在使用框架数据表生成文件时-请修改创建类名

已修改为mysql数据库的朋友可以吧数据库删掉重新生成表

修改h2数据库为mysql的方法-->application.properties-->对应注释有mysql数据库的注释取消掉 并注释h2的配置文件

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)