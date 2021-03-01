# kunter-constant

[Git@OSC](https://git.oschina.net/nature/kunter-constant.git)
[GitHub](https://github.com/angelsinklowcn/kunter-constant.git)
[Bitbucket](https://bitbucket.org/angelsinklow/kunter-constant.git)
[Coding](https://git.coding.net/kunter/kunter-constant.git)



## 更新日志



## 基础数据生成

生成文件列表：
- 数据模板
- SQL（基础数据插入脚本）
- Java（系统常量类）

配置说明：
####1. 配置文件目录：/src/main/resources
> 1.1 jdbc.properties
>>  [a] SourceType：数据源类型，可选择（DB、EXCEL）

>>  [b] path.dictionary：数据字典目录，设置数据源类型为EXCEL时必须设值，支持中文目录 ** 注意路径，必须为双斜杠或者反斜杠 **

>>  [c] DB：数据库类型，必须设值，可选择（ORACLE、MYSQL、POSTGRESQL）

>>  [d] DB.xx：数据库连接属性，数据库类型相关连接属性，设置DB类型必须设值

> 1.2 config.properties
>>  [b] package：包名，例：cn.kunter.constant.common.constant

>>  [c] table：表名称，支持通配符 ** 数据源类型为EXCEL，则参数无效 建议使用EXCEL的时候分模块保存设计文档 **

>>  [d] target：输出目录，可以为绝对目录或者相对目录，例：target/ 当前kunter-constant下的target/

### Main
> cn/kunter/common/constant/make/MakeConstant.java 常量类生成

> cn/kunter/common/constant/make/MakeExcel.java 数据模板生成

> cn/kunter/common/constant/make/MakeSQL.java SQL脚本生成

# 技术交流
* 邮箱：nature@kunter.cn‍
* QQ讨论群：[325980480](http://jq.qq.com/?_wv=1027&k=TrLNcX)

# 开源赞助

![Git@OSC](http://git.oschina.net/uploads/images/2015/0608/230108_2f43d66e_6133.png "开源赞助我(支付宝)")

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)