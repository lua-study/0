# flyray-android-demo



#### 软件架构
软件架构说明
Module采用MVP模式，将业务逻辑都抽取到Presenter层，避免Activity层显示和逻辑臃肿混乱，让Activity专注于按照生命周期显示控件。同时，将逻辑抽取到Presenter层，可以单独对Presenter层进行测试，也可以随时更换掉业务逻辑


整个项目是由多个Module共同组装完成。Module类型分为基础组件Module，业务模块Module。
每一个业务模块Module都引用基础组件Module，这样可以针对于每一个业务模块进行单独测试，甚至可以对此业务模块进行单独打包、单独发布。如果需要集成到总的平台，只需依赖此业务Module即可。

##app  平台module，总的应用入口

##route 路由module，多个module之间启动Activity、Service使用，可以进行修改从而控制各个页面的跳转。

##base 基础组件module，里面包含了联网框架、orm框架等基础组件供各个module使用

##hospital 医疗组件 所有的医疗业务的实现，可以单独打包，也可以集成到app组件中

##bus 公交组件 所有的公交业务实现，可以单独打包，也可以集成到app组件中 


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)