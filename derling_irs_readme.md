适合新手练手的项目，基于eclipse+ssm+shiro+layui的后台权限管理系统

maven版请异步： https://gitee.com/ssuperdu/irs-maven 

QQ交流群： **473676340**  需要的加一下共同学习！
   

# irs V1.2

默认账号：admin 密码：123456

数据库文件在doc目录下

添加用户需要邮件激活：邮件设置在global.properties配置文件中，支持QQ邮箱，自行修改邮箱密钥

## 介绍
irs致力于做更简洁的后台管理系统,完美整合springmvc + spring + shiro + mybatis注释丰富,上手容易

页面使用了layui

## 管理系统功能
1.角色管理 2.管理员管理 3.菜单管理 4.用户管理 5.业务日志 6.SQL、URL和Spring监控 7.集成MyBatis逆向工程

## 项目特点
1. 基于ssm+shiro
2. 后台脚手架，马上上手
3. 完善的日志记录体系，可记录登录日志，业务操作日志(可记录操作前和操作后的数据)，异常日志到数据库
4. 日志删除修改为定时任务(每日21点删除30天以前的日志，配置在global.properties)
5. 新增菜单管理、SQL、URL和Spring监控
6. 逆向工程：根据数据库生成pojo和dao（新增），请自行修改配置generatorConfig.xml，配置完运行：com.irs.generator.GeneratorSqlmap.main方法即可。

## 项目截图
![输入图片说明](https://gitee.com/uploads/images/2018/0325/145022_599a5d05_1045447.png "1.PNG")
![输入图片说明](https://gitee.com/uploads/images/2018/0519/223825_8fe428e9_1045447.png "QQ截1111.png")
![输入图片说明](https://images.gitee.com/uploads/images/2018/0729/145423_ff526c7d_1045447.png "1.png")
![输入图片说明](https://gitee.com/uploads/images/2018/0325/145056_977828e7_1045447.png "3.PNG")
![输入图片说明](https://gitee.com/uploads/images/2018/0325/145107_ad9fcd59_1045447.png "4.png")
![输入图片说明](https://gitee.com/uploads/images/2018/0325/145119_4a25eaf9_1045447.png "5.png")
![输入图片说明](https://gitee.com/uploads/images/2018/0325/145128_3c771dac_1045447.png "6.PNG")
![输入图片说明](https://gitee.com/uploads/images/2018/0325/145138_ba5accbc_1045447.png "7.png")
![输入图片说明](https://gitee.com/uploads/images/2018/0507/114145_ea68ad83_1045447.png "ttt.png")

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)