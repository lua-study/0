# wxcms
wxmcs是本着快速开发，易于扩展的理念，基于jfinal+shiro+layui+freemarker+ueditor+mysql等框架和技术结合maven多模块方式构建开发的一款通用内容发布系统。

#### 参与贡献

 **1. 欢迎Fork 本项目** 

 **2. 完成的还不太完善，欢迎大家一起交流探讨** 

 **3. 交流qq群：766508380** 

#### 运行效果图
后端内容发布系统效果图
![输入图片说明](https://images.gitee.com/uploads/images/2018/0922/095424_c8f7377b_131664.png "TIM截图20180922095354.png")
![输入图片说明](https://images.gitee.com/uploads/images/2018/0922/095446_a12f3720_131664.png "TIM截图20180922095222.png")
![输入图片说明](https://images.gitee.com/uploads/images/2018/0922/095521_b62a25a0_131664.png "TIM截图20180922095159.png")
![输入图片说明](https://images.gitee.com/uploads/images/2018/0922/095533_195b6f3c_131664.png "TIM截图20180922095124.png")
![输入图片说明](https://images.gitee.com/uploads/images/2018/0922/095820_b10daf8f_131664.png "TIM截图20180922095728.png")
![输入图片说明](https://images.gitee.com/uploads/images/2018/0922/095832_859cee94_131664.png "TIM截图20180922095702.png")

生成的前端页面效果图
![输入图片说明](https://images.gitee.com/uploads/images/2018/0906/112332_f43823de_131664.png "屏幕截图.png")

#### 项目介绍
一，使用的相关技术

（1）jfinal作为核心框架，感谢波总开源如此好用的框架

（2）使用shiro作权限控制

（3）整合了百度编辑器ueditor

（4）使用mysql数据库存储数据

（5）采用layui作为UI框架

（6）使用freemarker作为模板，生成前端静态页

（7）采用maven多模块方式构建项目，可以快速扩充而不影响其他模块

二，功能方面

目前只是实现了基础的一些功能

（1）权限管理

（2）文章发布

（3）栏目管理

（4）整合微信公众号开发的小部分内容

断断续续的开发了一个月的时间，只实现了一些简单的功能，欢迎大家多多交流。

#### 软件架构
wx-admin  后端管理模块包含系统用户管理、权限管理、栏目管理等功能

wx-cms    内容发布相关的模块

wx-comm   公共类以及工具类

wx-core   shiro基于jfinal的扩展类，和jfinal配置类

wx-model  使用jfinal自动生成的项目相关的model

wx-web    项目前端页面，相关的静态资源，生成静态网站所需的模板，系统配置文件

wx-weixin 微信公众号相关的内容

#### 安装使用

1.将位于wx-web/src/main/webapp/document/wxcms.sql文件导入mysql数据库

2.将项目导入开发工具，使用maven 编译并运行

3.登录用户：admin 登录密码：admin

4.前端页面需要在nginx下打开ssi on;才能正确显示

5.前端静态页下载地址：[前端项目地址](https://gitee.com/live.cn/qkj)
#### 扩展说明
如需新增模块只需要三步即可完成，就算不熟悉本项目，只需会用jfinal和maven即可

1.新增maven子模块

2.在新增模块下增加该模块的路由列表

  以wx-admin 为例

  public class AdminRoutes extends Routes {

    public void config()
    {
        add("/", MainController.class);

        add("/user", UserController.class);

        add("/staff",StaffController.class);

        add("/menu",MenuController.class);

        add("/log",LogController.class);

        add("/role",RoleController.class);
    }

}

3.将新增模块的路由列表加入到项目总的配置类中

  在wx-core模块下的AppConfig配置类中增加新增模块的路由列表

  public void configRoute(Routes me) {

        //加入路由list使shiro生效
        routeList.add(new AdminRoutes());

        //加入路由list使shiro生效
        routeList.add(new CmsRoutes());

        //加入admin模块的路由
        me.add(new AdminRoutes());

        //加入cms模块的路由
        me.add(new CmsRoutes());

        //加入weixin（微信）模块的路由
        me.add(new WeixinRoutes());
    }
完成以上三步即可将新的扩展内容增加进去，无需修改其他代码

说明：微信部分正在开发中，只是实现了获取用户信息和简单的信息回复。



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)