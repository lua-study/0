# Epoch

#### 社区支持

关键:截止到2019年6月份底，我本人都针对企业做免费的技术培训一次，远程或者西安直接现场培训。仅限周末空闲。

2018.12.11预告：基于epoch权限系统的，针对微信公众号和小程序的版本将于年底之前开源，敬请期待。

小程序跳转：地址待添加

公众号跳转：地址待添加

社区地址：[www.epoch.club](http://www.epoch.club)

项目预览地址：[跳转](http://www.epoch.club/epochOpen)(目前存在菜单被删除的情况，之后会禁止演示用户删除动作)
用户名：admin 密码123456

QQ交流群：607328652

文档地址：[http://epoch.mydoc.io/](http://epoch.mydoc.io/)  

关于文档密码请计算如下代码或者加QQ群免费获取：

```
int[] arr = new int[] {5,7,8,6};
int[] index = new int[] {0,3,1,1,2,2,2,1,1,3,1,2,1,3};
String tel = "";
for (int i : index) {
tel += arr;
}
```

#### 项目介绍

Epoch是基于Java语言，后端为jfinal,Beetl,Shiro,前端为bootstrap,bootstrap-table,jquery的后台权限管理系统。项目使用了Maven来进行管
理和基础构建。项目具有专业丰富的文档，以及提供的免费咨询的社区网站。[跳转社区](http://www.epoch.club)


Epoch系统管理分为以下功能，分别是用户管理，角色管理，部门管理，菜单管理，用户角色分配，角色菜单分配，数据字典，流水号规则，定时任务，
消息管理，系统监控，代码生成器功能模块。

核心功能模块

- 用户管理
- 角色管理
- 部门管理
- 菜单管理
- 用户角色分配
- 角色菜单分配
- 数据字典
- 流水号规则
- 定时任务
- 消息管理
- 系统监控
- 代码生成器
- 测试界面

Epoch适用于后台管理系统， 可以应用在任何J2EE项目的开发中，尤其适合企业信息管理系统（MIS）、内部办公系统（OA）、企业资源计划系统（ERP）、
客户关系管理系统（CRM）等。

 **前台UI封装后支持如下：(基本上都可以支持，包含了可以自己引入)** 

```
1. 表格快速开发，适用epoch:table标签进行快速开发，提供了一整套的表格编辑组件，以及实现类的相关功能。原理还是bootstrap-table。
   
2. 自适用结合数据字典的下拉框以及多选框，单选框radio。
    
3. 提供了组件普通弹窗winOpen，表格弹窗组件commonPopup，树形表格commonTreePopup等。
    
4. 提供了时间组件(基于laydate)封装，uploader上传，commonAttach上传，以及基于ajaxupload的云上传等功能。
    
5. 表格快速开发：提供了一整套的表格编辑组件，以及后台对应的实现类的相关功能。
```

#### 核心

```
1. 支持前台UI快速开发，具体看上面。
2. 支持代码生成器生成代码，免费试用，节省了开发效率70%。
3. 所有表格默认支持搜索功能开启，只需要简单的后台适配sql就行了，下拉框自动兼容到数据字典或者自己的数据，时间自动兼容date组件。
4. 所有表格可支持自动导出excel,CSV等文件，可按选中，全部，当前页三种方式。同时支持前后台转化，自动转化数据，自动可配置导出列。
5. 所有功能极速开发，例如保存，修改删除。项目是基于原生的jquery的。
6. 项目基于三套UI风格，可以互相切换，adminlte,ace以及H+风格。
```

#### 技术框架


```
- 核心框架: Jfinal
- 模板语言: Beetl
- 安全框架：Apache Shiro
- 缓存框架：Redis
- 文件导出：POI+流
- 前端：bootstrap,bootstrap-table,jquery,jquery-validate,Ztree

```

启动说明

```
* 项目依赖Redis服务。具体windows的redis安装方法，请参考跳转 epochblog.top中windows上安装redis服务
* 项目支持ajaxupload上传到oss，目前仅支持阿里云，具体配置在application下，请自行修改其中参数。配置后前台可使用ajaxupload上传。
* 请查看核心配置文件application，修改自己的参数如redis和数据库。使用Tomcat进行启动，正常启动即可访问项目。
```

商业版本

```
* 商业版本支持了工作流等，并且具有一套完整的工作流解决方案，具体请加群607328652联系群主，界面与当前界面保持一致。

```

预告

```
* 基于epoch的衍生的针对微信小程序和微信公众号的后台管理目标正在火热开发中，请敬请期待。
* 基于epoch的案例系统正在开发中，同时招募爱好epoch的人来协同开发，也将同步开源。
* 基于extjs6的epoch开源系统正在开发中。。。。。。
* 如果你针对epoch有好的发展和优化以及想衍生版本，请联系我。

```

部分预览图

![用户管理](https://images.gitee.com/uploads/images/2018/1130/201506_235b926f_626204.png "1.png")
![角色管理](https://images.gitee.com/uploads/images/2018/1130/201533_44135bef_626204.png "2.png")
![输入图片说明](https://images.gitee.com/uploads/images/2018/1130/201613_1446caae_626204.png "3.png")
![输入图片说明](https://images.gitee.com/uploads/images/2018/1130/201621_4f257787_626204.png "4.png")
![输入图片说明](https://images.gitee.com/uploads/images/2018/1130/201630_b75439a7_626204.png "5.png")
![输入图片说明](https://images.gitee.com/uploads/images/2018/1130/201638_1a6f32b6_626204.png "6.png")
![输入图片说明](https://images.gitee.com/uploads/images/2018/1201/153933_85100c41_626204.png "11.png")
![输入图片说明](https://images.gitee.com/uploads/images/2018/1201/154000_29fdd7ae_626204.png "22.png")

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)