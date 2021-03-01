# ybg_auth 基于标准oauth2权限模型开发框架。

#### 项目介绍

基于开源的pig框架进行改造，使用springboot2+mybtis plus3 开发。入手难度：2年以上开发经验

| pig | ybg_auth| 
| --------- | ----- | 
| spring cloud1.X|  springboot2 | 
| 有mq消息|  无mq功能 |
| 整个项目运行项目内存较大(大于10G)|  内存开销很小 小于2G|
| mybtis plus 2|  mybtis plus 3 |
| 框架有负载均衡|  用nginx去控制 |
| 难度较大|  难度较小 |

#### 框架需求
一般来说传统的springmvc足以应付各种各样的小系统。随着公司发展,又会开发其他系统，然后吧部分权限的代码、拷过来用，加上自己的逻辑又是一个新系统。但是又出现了一个新的问题，那就是权限和业务耦合的太严谨了，无法拆分旧的权限系统，自己又没能力去搭建一个权限系统或者重复搭建一个权限系统是一个十分麻烦的事情，又要用以前的系统账号等复杂因素，本框架就由此产生。
采用标准oauth2开发。实现权限和业务相分离。一个点点配置 便可控制业务权限。





#### 软件架构

| 技术选型      | 版本 |  描述 |
| ---------   | ----- | ----- |
| springboot   |2.0.4  | |
| redis|  | |
| spring security oauth2|  | |
| mybatis plus| 3.0.6 | |
| kaptche|   | 验证码|
| maven      |  3.3.9 | |
| jdk       |  8 | |
| vue前端脚手架 |  2 | |
| swagger |  2 | 在线文档 |
| mysql|  5.7 |  |

#### 目录说明
ybg_auth 授权中心（授权服务器）

ybg_auth_admin 用户角色权限管理后端（相当于资源服务器）

ybg_auth_adminUI node.js项目搭建的用户角色权限管理前端，默认端口8000


架构设计图


![输入图片说明](https://images.gitee.com/uploads/images/2018/1006/212322_937ce663_880593.png "Untitled Diagram.png")

#### 开发环境
|开发环境|
|--------|
| eclipse 最近版|
| maven 3.3.9+|
| jdk8|
| redis 和redis客户端（RedisDesktopManager）|
| mysql5.7 以及navicat |
| tortoise svn|
| python|
| node.js|


#### 部署环境
|部署环境|
|--------|
|maven 3.3.9+|
| jdk8|
| redis |
|mysql5.7 |
| jenkins|
| nginx|






### 安装教程

1. 如何导入项目？参考 https://gitee.com/YYDeament/88ybg/wikis/Home
2. 安装环境 redis node.js maven 等环境？ 请百度
3. 启动顺序：ybg_auth ->  ybg_auth_admin  -> ybg_auth_adminUI 
4. 开发项目页面：http://localhost:8000 

### 部署教程
1. 暂不公布（收费）


#### 使用说明
1. 安装好开发环境必要环境，并且确保redis，mysql 能启动，如果是远程的redis和Mysql 请确保能远程访问的权限
2. 导入数据库文件，如果导不进 把字符varchar 的字节调小 导完后再改回来

先导入到数据库，库的名称叫uplus_auth 数据库编码是utf8mb4

![输入图片说明](https://images.gitee.com/uploads/images/2018/1007/091517_aec68b78_880593.png "屏幕截图.png")

3. 启动ybg_auth项目
    导入项目的方式参考 https://gitee.com/YYDeament/88ybg/wikis/Home
    修改ybg_auth项目中的application-dev.properties 文件 修改数据库配置和你的redis配置
    右键   /uplus-auth/src/main/java/com/uplus/AuthApplication.java    run as java application ,启动项目即可

4. 启动ybg_auth_admin项目
    导入项目的方式参考 https://gitee.com/YYDeament/88ybg/wikis/Home
    修改ybg_auth_admin项目中的application-dev.properties 文件 修改数据库配置和你的redis配置
    右键  /uplus-auth-admin/src/main/java/com/uplus/AuthAdminApplication.java    run as java application ,启动项目即可

5. 启动ybg_auth_adminUI 
    导入项目后，进入ybg_auth_adminUI 代码目录
    shift+右键 如图所示 
![输入图片说明](https://images.gitee.com/uploads/images/2018/1007/094404_4aceac98_880593.png "屏幕截图.png")
    先执行npm install命令
    执行完 再执行npm run dev 启动本地调试

#### 更多项目文档尽在wiki 或者 老项目中

https://gitee.com/SYDeament/ybg_auth/wikis/Home

https://gitee.com/YYDeament/88ybg/wikis/Home


#### QQ交流群：（女生，一个太阳以下拒绝加入）468054855



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)