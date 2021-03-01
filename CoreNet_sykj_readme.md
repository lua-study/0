# sykj

#### 介绍
自微软的.net core 发布以后，一直想做一套基于.NET平台通用用户权限后台管理系统，能跨平台部署linux，于是并有了该系统的诞生，该项目采用经典DDD架构思想进行开发，简洁而不简单，实用至上，所写每一行代码都经过深思熟虑，内置了很多常用组件并且通过Linux系统线上应用的实测，ORM使用微软官方EF支持MySQL、SqlServer、PostgreSQL；后期我们将会不断更新，慢慢接入支付宝，微信支付，标准电商系统等模块。

#### 内置功能

1、CMS模块；
文章栏目管理、文章内容管理；
2、会员管理；
用户管理、积分明细管理、系统消息管理；
3、网站管理；
网站留言管理，网站基本参数配置、微信小程序，开发平台接入参数配置；
4、系统设置；
角色授权、账号管理、角色管理、权限管理、缩略图设置、日志管理、系统参数设置；

#### 技术栈

.net core 2.1 + EF core + layui + ztree + swagger + json.net + Quartz + JWT

#### 特点

1、架构：项目采用经典DDD架构思想进行开发，DDD（Domain Driven Design，领域驱动设计）作为一种软件开发方法，它可以帮助我们设计高质量的软件模型。在正确实现的情况下，我们通过DDD完成的设计恰恰就是软件的工作方式。
2、项目简介：
Sykj.CodeGenerator：代码生成工具(源码)，自动化构建项目，方便快捷，解放双手；
Sykj.Components：业务公共组件(如：异常处理，依赖注入，JWT，认证与权限，推送服务接入，短信服务接入，百度编辑器源码整合，微信服务号，小程序SDK接入等)；
Sykj.Entity：EF实体；
Sykj.Infrastructure：基础设施(如：基于Aspose组件，实现excel导入，导出，word导出；字节转换类；配置文件管理类；文件操作类；HTTP发送请求类；图片压缩裁剪帮助类；二维码生成类；html处理，随机数，时间戳等帮助类；缓存实现，RedisCache、MemoryCache；加密算法整理（AES，DES、RSA）哈希算法整理（MD5,SHA1,SHA256）
Sykj.IServices：服务接口；
Sykj.Repository：仓储，支持原生SQL查询，返回DataTable与强类型集合；
Sykj.Services：服务层；
Sykj.Test：单元测试；
Sykj.Timer：任务管理，根据设定规则定时执行，Quartz实现；
Sykj.ViewModel：DTO，数据传输对象；
Sykj.Web：web项目，后台，webapi；

#### 开发者信息

开发者：云南尚雅科技文化有限公司；
公司官网：http://www.sykjwh.cn/

#### 更新信息

2019-06-04 更新unipush 推送服务；
2019-06-01 更新微信小程序，服务号接入；

#### 在线体验

地址：http://open.sykjwh.cn/manager/
用户名：admin
密码：111111

#### 项目截图预览

![输入图片说明](https://images.gitee.com/uploads/images/2019/0605/135243_3dde6685_4771167.png "1.png")
![输入图片说明](https://images.gitee.com/uploads/images/2019/0605/135301_0dd4ab8f_4771167.png "2.png")
![输入图片说明](https://images.gitee.com/uploads/images/2019/0605/135313_0486687f_4771167.png "3.png")
![输入图片说明](https://images.gitee.com/uploads/images/2019/0605/135327_02096ad1_4771167.png "4.png")
![输入图片说明](https://images.gitee.com/uploads/images/2019/0605/135338_7e644639_4771167.png "5.png")
![输入图片说明](https://images.gitee.com/uploads/images/2019/0605/135349_945518f7_4771167.png "6.png")
![输入图片说明](https://images.gitee.com/uploads/images/2019/0605/135402_5f29a928_4771167.png "7.png")
![输入图片说明](https://images.gitee.com/uploads/images/2019/0605/135414_f5504027_4771167.png "8.png")

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)