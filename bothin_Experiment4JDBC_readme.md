## 实验四实验报告
    院（系）名称：网络空间安全学院
    专业班级： 17软卓1班
    学号： 201741404110
    姓名： 李剑波
    实验题目： 实验4 J编程DBC
    实验日期：2019.05.15
    实验（上机）学时： 2
    成绩：
### 实验内容、要求
*改写用户注册/登录模块，使用JDBC或JPA技术实现用户数据的持久化，大致功能如下： 
1、	设计用户实体Entity与莞工登录用户Entity，并设置关联。 
2、	Entity需要校验用户数据的合法性。 
3、	用户照片保存在数据库中；前端显示用户照片时，改为读取数据库。 
4、	任何数据库操作发生错误时，请导向error.jsp，并回滚数据库事务。 
5、	增加绑定莞工中央认证账号的功能。本地账号登录的用户，可以在用户中心绑定莞工认证账号。绑定后，本地账号与莞工中央认证账号关联（一对一），并且使用莞工中央认证登录等价于本地账号登录。

### 采用的Java EE技术规范
* JDBC的基础语法
* JPA的基础语法
* Ajax 异步检测表单数据
* jQuery基本用法

### 运行该项目的流程
* http://localhost:8080/index.jsp
![adsf](img/index.png)
* 点击注册
![adsf](img/register.png)
![adsf](img/registered.png)
* 注册成功的页面
![adsf](img/info.png)
* 点击头像进行上传头像
![adsf](img/uploadImg.png)
* 点击修改信息按钮
![adsf](img/change.png)
* 点击绑定信息按钮
![adsf](img/bind.png)
![adsf](img/changed.png)


### 文件介绍
* index.jsp (首页)
利用session负责界面的登陆以及登出，若已登录，则显示登出按钮，以及登陆的用户信息，反之则相反



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)