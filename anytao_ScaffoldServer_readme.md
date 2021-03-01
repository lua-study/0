# ScaffoldServer
> 基于.netcore2.0

前端项目地址(基于react) => https://gitee.com/teambp/ScaffoldClient

项目相关文章：[点击这里](http://www.cnblogs.com/Ambre/p/7825527.html)

项目演示地址：[点击这里](http://test.hourxu.com)



仅开放了少数几个菜单的查看和新增权限。
因为做了处理，所以，账号只能一个人登录，前面登录的人会被挤下来，所以多提供几个账号
jw1 ,tw1,gw1这3个账号。密码和账号一样

# 注意****，很重要！

![输入图片说明](https://gitee.com/uploads/images/2018/0426/091535_9983967a_332899.png "屏幕截图.png")

在生成表之前，先注释这句话，然后配置好T4的2个config文件，T4生成成功后，取消注释这句话，再启动项目即可！

如果T4一直无法执行成功，非常抱歉。暂时还没找到原因。一般来说，只要config配置的是对的，T4就能生成成功。

生成顺序：

0.配置API层的链接字符串，配置Application层的config.ttinclude,配置Boostrap层的config.ttinclude

1.注释上图的那句话

2.选中API层，生成表（看下面的readme）

3.保存BaseService.tt文件,IBaseService.tt文件，保存Startup.tt文件

4.取消注释

# 2018/01/19更新

加入T4模板，生成IOC注入类和服务类，项目需要服务类改成部分类，这样就可以直接扩写。

加入T4的好处是：有些类是不需要扩写复杂操作的，只用基类里的简单操作

详细教程：[http://www.cnblogs.com/Ambre/category/1113820.html](http://www.cnblogs.com/Ambre/category/1113820.html)

简易教程：

![T4位置](https://gitee.com/uploads/images/2018/0119/093201_701c1338_332899.png "屏幕截图.png")

![config](https://gitee.com/uploads/images/2018/0119/093243_15989c77_332899.png "屏幕截图.png")

![输入图片说明](https://gitee.com/uploads/images/2018/0119/093307_adf87662_332899.png "屏幕截图.png")

输入你的数据库地址

注意，2处都要写。写完后，去保存一下你的T4模板就行了，它会自动生成。vS2017有BUG，生成->转化所有T4模板这个按钮没作用了。大家可以去下一个AutoT4的VS2017插件，生成的时候，帮你生成所有T4模板




# 项目介绍

QQ群 点击加入 [17078075](https://jq.qq.com/?_wv=1027&k=58kloo3)

项目架构简洁，适合中小型团队使用，适合快速开发。

未加入T4模板生成代码！

架构是实际项目慢慢简化而来的。

# 项目实现了什么
1. API层请求验证
2. API文档的自动生成（swagger）
3. DI容器
4. 日志数据库
5. CodeFirst

......具体还是看代码吧

# 项目结构

业务项目文件夹：

C-Scaffold

Scaffold.API API服务层

Scaffold.AppService 应用服务层

Scaffold.AppService.Model ViewModel层，请求类

Scaffold.Domain  数据模型层

Scaffold.BootStrapper  启动层

通用代码层：

EStart.DataBase.EF 针对EF的封装，包含服务的基类ServiceCore，和工作单元UnitOfWork

EStart.DataBase.Event.Domian  日志数据库

EStart.Infrastructure  基础帮助类所在层

EStart.Interface  接口层

EStart.ServiceAgent  其他第三方服务层 ，如发短信的服务，发邮件的服务

# 项目初始化

VS 2017打开


配置数据库链接字符串

Scaffold.API->appsettings.json


在Scaffold.API文件夹启动CMD

```
dotnet build
```
或者ALT+B+B


打开程序包管理控制台

![输入图片说明](https://gitee.com/uploads/images/2017/1111/115022_dab3d66a_332899.jpeg "TIM截图20171111115041.jpg")

选中项目 ->EStart.DataBase.Event.Domian 初始化日志数据库

```
update-database -context EventDbContext
```

选中项目 ->Scaffold.Domain 初始化业务数据库

```
update-database -context ScaffoldDbContext
```

CMD中输入
```
dotnet run
```
启动项目

![输入图片说明](https://gitee.com/uploads/images/2017/1111/115407_98d2039a_332899.jpeg "TIM截图20171111115503.jpg")

这样就启动成功了

输入地址：http://localhost:59049/swagger/

![输入图片说明](https://gitee.com/uploads/images/2017/1111/115639_7aac3d34_332899.jpeg "TIM截图20171111115720.jpg")

出现上面的图片，就是启动成功了！

前端使用admin,admin即可登陆。初始数据已经加入进去

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)