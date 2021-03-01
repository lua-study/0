# CMS 完整能运行的后台管理系统，后台数据工程基于SpringMVC实现，前台界面工程基于Node.js+Vue.js+iView的架构实现。
## 工程结构介绍
```
 cms/
    * cms_data/ ---------- 后台数据工程
    * cms_web/  ---------- 前台界面工程
    * tb_menu_one.sql ---- 数据库初始化sql
 ```
 ## 关键技术功能介绍
 ### 一. 登录账号密码采用RSA非对称加密方式
  由后端工程下发公钥，前端工程使用公钥对账号密码进行加密再进行login操作，有效避免账号密码暴露。
  如下图所示：
![输入图片说明](https://images.gitee.com/uploads/images/2019/0509/210747_76b7b5c7_1133403.png "7.png")
  
 ### 二. 左侧菜单栏动态下发
  左侧菜单栏的显示根据不同用户分配的权限下发不同的菜单，采用二级菜单的结构，如图所示：
![输入图片说明](https://images.gitee.com/uploads/images/2019/0509/210807_cce7df9a_1133403.png "1.png")

 ### 三. JWT做权限加密和超时管理
![输入图片说明](https://images.gitee.com/uploads/images/2019/0509/210821_1dbf48f4_1133403.png "8.png")
![输入图片说明](https://images.gitee.com/uploads/images/2019/0509/210839_612e9915_1133403.png "9.png")
 
 ### 四. 菜单栏路径配置
![输入图片说明](https://images.gitee.com/uploads/images/2019/0509/210859_c8b6bd07_1133403.png "2.png")
![输入图片说明](https://images.gitee.com/uploads/images/2019/0509/210915_087c2909_1133403.png "3.png")
 
 ### 五. 角色管理
  可以创建不同角色，对角色分配菜单栏的界面权限
![输入图片说明](https://images.gitee.com/uploads/images/2019/0509/210933_4c00d182_1133403.png "5.png")
 
 ### 六. 用户管理
  对用户进行编辑，冻结等操作，同时可以对不同用户分配角色，每个用户只能有一个角色。
![输入图片说明](https://images.gitee.com/uploads/images/2019/0509/210951_4b6f4334_1133403.png "6.png")


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)