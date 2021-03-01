# demoncat-db-sync

数据库同步工具

# 功能

1、将A数据的数据同步到B

2、下载项目，进行二次开发：编写同步的表，以及同步操作的JUNIT

3、支持Oracle和Mysql数据库

# 使用

1、配置run.Config ，指定源数据库、目标数据库、同步前需要清空的目标数据库表(需要同步的表除外)

2、在syncs包下创建同步类(参考syncs.DemoSync)：继承 util.BaseSync，实现 init()和parse()

3、编写run.Run，调用同步类的方法，通过Junit执行同步


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)