####WhereTa权限管理系统以SpringMvc+MyBatis+Shiro+MySQL+ActiveMQ+Redis+Easyui为架构，实现了用户-角色-权限三者结合的功能权限颗粒化控制：
    按钮根据权限限制
    菜单根据权限显示
    所有相关URL根据权限拦截
####数据权限暂时以用户为中心查询：
    查询部门只能查询本部门以及子级部门
    查询用户只能查询本级没有管理权限的用户以及所有子级用户
####会话管理使用Shiro的框架，结合Redis缓存，便于缓存控制以及实现分布式部署。如果想要实现自带的Map缓存或者使用Ehcache缓存都可以直接修改`shiro.xml`文件即可
####以下是程序屏幕截图：
#####登录页面
![登录页面](http://7u2jlp.com1.z0.glb.clouddn.com/whereurp抓图1.png)
#####权限页面
![权限页面](http://7u2jlp.com1.z0.glb.clouddn.com/whereurp抓图2.png)
#####角色页面
![角色页面](http://7u2jlp.com1.z0.glb.clouddn.com/whereurp抓图3.png)
#####菜单页面
![菜单页面](http://7u2jlp.com1.z0.glb.clouddn.com/whereurp抓图4.png)
#####部门页面
![部门页面](http://7u2jlp.com1.z0.glb.clouddn.com/whereurp抓图5.png)
#####用户页面
![用户页面](http://7u2jlp.com1.z0.glb.clouddn.com/whereurp抓图6.png)
####未完待续。。。

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)