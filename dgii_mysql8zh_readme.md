# mysql8zh

#### 项目介绍
mysql8.0中文手册，方便学习查询，生成的手册请项目附件
 
MySQL 8参考手册
摘要
 
这是?MySQL参考手册。它的文件通过8.0.14 MySQL 8。它可以包括MySQL版本尚未发布功能的文档。关于哪个版本的信息已被释放，看到MySQL 8版本说明

MySQL集群是目前不在MySQL 8的支持。关于MySQL集群的信息，请参阅7.5、MySQL NDB Cluster NDB簇7.6

MySQL 8的特点。本手册介绍了不包含在MySQL 8的每一个版本的功能；这种功能可能不包含在MySQL 8版授权给你。如果你有任何问题的特征包含在你的MySQL 8版，指的是你的MySQL 8许可协议或与Oracle的销售代表。

笔记详细介绍每个版本的变化，看MySQL 8版本说明

合法的信息，包括许可证信息，看到前言和法律声明

利用MySQL的帮助，请访问或MySQL的论坛或MySQL邮件列表，在那里你可以讨论你的问题与其他MySQL用户。

文件：生在2018年08月02日（评：58345）


--------------------------------------------------------------------------------

目录

前言和法律声明
1一般资料
1.1关于本手册
1.2拼写和语法约定
1.3概述的MySQL数据库管理系统
1.3.1什么是MySQL？
1.3.2 MySQL的主要特点
1.3.3历史MySQL
1.4什么是新的MySQL 8
1.5服务器和状态变量和选择的，过时的，或在MySQL 8中删除
1.6 MySQL的信息来源
1.6.1 MySQL网站
1.6.2 MySQL邮件列表
在MySQL论坛1.6.3 MySQL社区的支持
在互联网中继聊天（IRC）1.6.4 MySQL社区的支持
1.6.5 MySQL企业
1.7如何报告错误或问题
1.8 MySQL标准
1.8.1 MySQL扩展标准的SQL
1.8.2 MySQL区别于标准的SQL
1.8.3 MySQL如何处理约束
1.9学分
1.9.1贡献的MySQL
documenters 1.9.2 and；
1.9.3包支持MySQL
1.9.4工具被用来创建MySQL
1.8.5支持MySQL
MySQL的安装和升级2
2.1一般安装指导
2.1.1 MySQL版本和配电安装
2.1.2如何让MySQL
2.1.3验证包装完整性使用MD5校验或GnuPG
2.1.4安装布局
2.1.5编译器特定的生成特性
2.2安装在Unix / Linux使用通用二进制代码MySQL
在微软Windows 2.3安装MySQL
2.3.1 MySQL的安装布局在微软Windows
2.3.2选择安装包
2.3.3 MySQL的Windows安装程序
2.3.4 MySQL的通知
2.3.5安装在微软Windows使用MySQLnoinstallzip档案
2.3.6排除微软Windows MySQL服务器安装
2.3.7 Windows安装后的程序
2.3.8升级MySQL在Windows
2.4安装MySQL在MacOS
2.4.1一般笔记安装MySQL在MacOS
2.4.2安装使用本地包MacOS MySQL
2.4.3安装和使用MySQL启动守护程序
2.4.4安装和使用MySQL偏好窗格
2.5 installing是Linux下MySQL
2.5.1安装MySQL使用yum库Linux MySQL
2.5.2安装MySQL使用MySQL的容易存放Linux
2.5.3安装MySQL使用MySQL版本库的Linux
2.5.4安装MySQL使用Oracle Linux RPM包
2.5.5安装MySQL使用Debian Linux的Oracle
2.5.6部署MySQL在Linux和Docker
2.5.7安装MySQL在Linux从本地软件库
2.5.8安装MySQL在Linux和Juju
2.5.9管理MySQL服务器系统
2.6安装MySQL使用牢不可破的Linux网络（ULN）
2.7安装MySQL在FreeBSD
2.8安装MySQL从源
2.8.1 MySQL源安装布局
2.8.2安装MySQL使用标准源分布
2.8.3安装MySQL使用开发源码树
2.8.4 . MYSQL源-配置选项
2.8.5问题处理编译MySQL
2.8.6 MySQL的配置和三方工具
2.8.7生成MySQL doxygen文档内容
2.9安装后的设置和测试
2.9.1初始化数据目录
2.9.2启动服务器
2.9.3测试服务器
2.9.4保证初始MySQL账户
自动启动和停止MySQL 2.9.5
2.10升级MySQL或downgrading
2.10.1升级MySQL
参赛人员downgrading MySQL
2.10.3重建或修复表或索引
2.10.4复制MySQL数据库到另一台机器
2.11 Perl安装说明
2.11.1安装Perl在UNIX
2.11.2 ActiveState Perl安装Windows
2.11.3问题使用Perl / DBD接口
教程3
3.1连接到服务器和从服务器断开
3.2进入查询
3.3创建和使用数据库
3.3.1创建和选择数据库
3.3.2创建表
3.3.3数据加载到表
3.3.4检索信息从表
3.4是对数据库和表的信息
3.5使用mysql的批处理模式
常见疑问3.6例
3.6.1最大值为列
3.6.2行持某一列的最大
3.6.3最大柱每组
3.6.4持有某列的分组最大的行
3.6.5使用用户定义的变量
3.6.6使用外键
3.6.7搜索两键
3.6.8计算每天的访问量
使用auto_increment 3.6.9
3.7使用MySQL和Apache
4 MySQL程序
4.1概述MySQL程序
4.2使用MySQL的程序
4.2.1调用mysql程序
4.2.2连接MySQL服务器
4.2.3指定程序选项
4.2.4使用命令行选项
4.2.5程序选项修饰符
4.2.6使用选项文件
4.2.7命令行选项选择文件处理的影响
4.2.8使用选项设置程序变量
4.2.9 Option Defaults, Options Expecting Values, and the = Sign
4.2.10设置环境变量
4.3 MySQL服务器，服务器启动程序
4.3.1mysqld- MySQL服务器
4.3.2_ mysqld safeMySQL服务器启动脚本
4.3.3mysql.serverMySQL服务器启动脚本
4.3.4mysqld _多管理多个MySQL服务器
4.4 MySQL安装相关程序
4.4.1公司_错误编译MySQL错误信息文件
4.4.2MySQL安装的安全_ _提高MySQL安装的安全性
4.4.3mysql_ssl_rsa_setup创建SSL / RSA文件
4.4.4MySQL _ tzinfo _到_ SQL-加载时区表
4.4.5mysql_upgrade检查升级MySQL表
4.5 MySQL客户端程序
4.5.1MySQL- MySQL命令行工具
4.5.2mysqladmin-管理MySQL服务器客户端
4.5.3mysqlcheck一个表的维护程序
4.5.4mysqldump一个数据库备份方案
4.5.5mysqlimport-数据导入程序
4.5.6mysqlpump一个数据库备份方案
4.5.7MySQLShow显示数据库、表和列的信息，
4.5.8mysqlslap负载仿真客户端
4.6 MySQL管理实用程序
4.6.1ibd2sdiInnoDB表空间- SDI提取工具
4.6.2innochecksum离线InnoDB文件校验工具
4.6.3myisam_ftdump显示全文索引信息
4.6.4myisamchkMyISAM表-维修工具
4.6.5myisamlog日志文件内容显示MyISAM
4.6.6MyISAMPack-生成压缩，read - only Myisam Table
4.6.7_ _ MySQL配置编辑器MySQL的配置实用程序
4.6.8mysqlbinlog用于处理二进制日志文件的效用
4.6.9mysqldumpslow总结慢查询日志文件
4.7 MySQL程序开发工具
4.7.1_配置MySQL-编译客户端显示选项
4.7.2my_print_defaults从选项文件显示选项
4.7.3resolve_stack_dump解决数字堆栈转储符号
4.8杂项程序
4.8.1lz4_decompress-解压缩mysqlpump lz4压缩输出
4.8.2perror解释错误代码
4.8.3resolveip-解析主机名到IP地址或反之亦然
4.8.4zlib_decompress-解压缩mysqlpump zlib压缩输出
4.9 MySQL程序的环境变量
5 MySQL服务器管理
5.1 MySQL服务器
5.1.1配置服务器
5.1.2服务器配置的默认值
5.1.3服务器选项，系统变量和状态变量的引用
5.1.4服务器系统变量引用
5.1.5服务器状态变量引用
5.1.6.伺服command options
5.1.7服务器系统变量
5.1.8使用系统变量
5.1.9服务器状态变量
5.1.10服务器SQL模式
5.1.11 IPv6支持
5.1.12 MySQL服务器的时区支持
5.1.13服务器端的帮助
5.1.14服务器响应信号
5.1.15服务器关机过程
5.2 MySQL数据目录
5.3 MySQL数据库系统
5.4 MySQL服务器的日志
5.4.1选择通用查询和慢查询日志输出目的地
5.4.2 the error log
5.4.3通用查询日志
5.4.4二进制日志
5.4.5慢查询日志
5.4.6 DDL日志
5.4.7服务器日志维护
5.5 MySQL服务器组件
5.5.1错误日志组件
5.6 MySQL服务器插件
5.6.1安装和卸载插件
5.6.2获取服务器插件信息
5.6.3 MySQL企业线程池
5.6.4的重写查询重写插件
5.6.5版标记
5.7运行多个MySQL实例在一台机器上
5.7.1设置多个数据目录
5.7.2在Windows上运行多个MySQL实例
5.7.3运行在UNIX多个MySQL实例
5.7.4使用客户端程序在多服务器环境
6安全
一般的安全问题
6.1.1安全指南
6.1.2保证密码安全
6.1.3使MySQL安全免受攻击
6.1.4安全相关的mysqld选项和变量
6.1.5如何运行MySQL作为一个正常的用户
6.1.6安全问题和负荷数据的地方
6.1.7客户端编程的安全指南
6.2 MySQL的权限系统
6.2.1提供MySQL权限模式
6.2.2静态与动态权限
6.2.3授权表
6.2.4指定帐户名称
6.2.5指定角色的名字
6.2.6访问控制，阶段1：连接验证
6.2.7访问控制，阶段2：请求验证
6.2.8当特权更改生效
6.2.9连接到MySQL问题的故障排除
6.3 MySQL用户账户管理
6.3.1用户名称和密码
6.3.2添加用户帐户
6.3.3删除用户帐户
6.3.4使用角色
6.3.5保留用户帐户
6.3.6设置帐户的资源限制
6.3.7分配帐户密码
6.3.8密码管理
6.3.9服务器过期密码处理
6.3.10认证
6.3.11 .激光器代理
6.3.12用户帐户锁定
6.3.13基于SQL MySQL帐户活动的审计
6.4使用加密连接
6.4.1配置MySQL使用加密连接
6.4.2命令选项加密连接
6.4.3创建SSL和RSA证书和密钥
6.2.4 Opsssl versus Wolfsl
6.4.5建筑MySQL加密连接支持
6.4.6加密连接协议和密码
6.4.7连接到MySQL从Windows SSH远程
6.5安全组件和插件
6.5.1认证插件
6.5.2连接控制插件
6.5.3密码验证组件
6.5.4 MySQL的钥匙圈
6.5.5 MySQL企业审计
6.5.6 MySQL企业防火墙
6.6 fips支持
7备份和恢复
7.1备份和恢复类型
7.2数据库备份方法
7.3实例的备份和恢复策略
7.3.1建立备份策略
7.3.2使用备份恢复
7.3.3备份策略总结
7.4使用mysqldump备份
7.4.1数据转储与mysqldump SQL格式
7.4.2重装SQL格式备份
7.4.3倾销数据分隔符的文本格式，mysqldump
7.4.4重装分隔符的文本格式备份
7.4.5 mysqldump贴士
在时间7点（增量）使用二进制日志恢复
在使用事件的时间点恢复7.5.1
在使用事件位置的时间点恢复7.5.2
7.6 MyISAM表的维护和故障恢复
7.6.1用于崩溃恢复myisamchk
7.6.2如何检查MyISAM表错误
7.6.3如何修复MyISAM表
美国MyISAM表优化
7.6.5建立MyISAM表的维护计划
8优化
8.1优化概述
8.2优化SQL语句
8.2.1优化SELECT语句
8.2.2优化子查询、导出表、视图的引用，和公用表表达式
8.2.3 information_schema查询优化
8.2.4优化性能模式查询
8.2.5优化数据变化报表
8.2.6优化数据库的权限
8.2.7其他优化技巧
8.3优化指标
8.3.1 MySQL如何使用索引
8.3.2主关键字优化
8.3.3空间索引优化
8.3.4外键优化
8.3.5列索引
8.3.6多列索引
8.3.7验证指标的使用
8.3.8 InnoDB和MyISAM索引的统计信息收集
8.3.9比较B树和哈希索引
使用索引扩展第
8.3.11优化器使用生成的列的索引
8.3.12隐形反射
8.3.13降序索引
8.4优化数据库结构
8.4.1优化数据大小
8.4.2优化MySQL数据类型
8.4.3优化多表
在MySQL中使用8.4.4内部临时表
8.5优化InnoDB表
8.5.1优化InnoDB表的存储布局
8.5.2优化InnoDB事务管理
8.5.3优化InnoDB只读事务
8.5.4优化InnoDB重做日志
8.5.5 InnoDB表加载大量数据
8.5.6 InnoDB查询优化
8.5.7 InnoDB DDL操作优化
8.5.8 InnoDB磁盘I/O优化
8.5.9优化InnoDB配置变量
8.5.10优化InnoDB有很多表系统
8.6优化MyISAM表
8.6.1 MyISAM查询优化
8.6.2数据批量加载对MyISAM表
8.6.3优化检修表报表
8.7优化内存表
8.8了解查询执行计划
8.8.1优化查询详细解释
8.8.2解释输出格式
8.8.3扩展解释输出格式
8.8.4获取执行计划信息为命名的连接
8.8.5估计查询性能
8.9控制查询优化器
8.9.1控制查询计划的评价
8.9.2优化器提示
3切换优化
8.9.4指标提示的
8.9.5优化器成本模型
8.9.6优化器统计
8.10缓冲和缓存
8.10.1 InnoDB缓冲池的优化
8.10.2的myisam Key Cache
8.10.3缓存的准备好的语句和存储的程序
对于优化锁定操作
8.11.1内部锁定的方法
8.11.2表锁定问题
8.11.3并发插入
8.11.4元数据锁定
8.11.5外锁闭
8.12优化MySQL服务器
4优化磁盘I/O
8.12.2使用符号链接
8.12.3优化内存使用
8.12.4优化网络使用
8.12.5资源组
8.13性能测试（基准）
8.13.1企业测量表达式和函数的速度
8.13.2使用您自己的基准
8.13.3测量性能与performance_schema
8.14检查线程信息
8.14.1公司螺纹指令值
8.14.2通用线程状态
8.14.3复制主线程状态
8.14.4复制从I/O线程状态
8.14.5 SLAVE端状态
8.14.6复制从连接线程状态
8.14.7事件调度线程的状态
9语言结构
9.1文字值
9.1.1 literals字符串
9.1.2数字字面值
9.1.3日期和Time Literals
9.1.4 Hexadecimal Literals
9.1.5位值的文字
literals 9.1.6布尔
9.1.7空值
9.2架构对象名称
9.2.1标识符限定符
9.2.2标识符大小写敏感
9.2.3映射标识符文件名
9.2.4函数名称解析和分辨率
关键词9.3和保留字
9.4用户定义的变量
9.5表达式的语法
9.6如何语法
10字符集Unicode排序规则，
一般在10.1字符集和整理
在MySQL 10.2字符集和整理
10.2.1字符集的剧目
10.2.2 gb3212 for元数据
10.3指定字符集和整理
10.3.1整理命名约定
10.3.2服务器字符集和整理
10.3.3数据库字符集和整理
10.3.4表字符集和整理
10.3.5列的字符集和字符
10.3.6字符串的字符集和整理
10.3.7国家字符集
10.3.8字符集介绍
10.3.9实例字符集和整理作业
10.3.10兼容性与其他数据库管理系统
10.4连接字符集和排序规则
10.5配置应用程序的字符集和整理
10.6错误消息的字符集
10.7列的字符集转换
10.8 collation问题
10.8.1使用SQL语句整理
10.8.2 COLLATE子句优先级
10.8.3字符集和整理的兼容性
10.8.4整理可压缩性表达
10.8.5的二进制排序规则相比，_bin排序规则
10.8.6运动学效应（collation of the
10.8.7使用information_schema搜索排序
10.9 Unicode支持
10.9.1的utf8mb4（4字节gb3212字符集Unicode编码）
10.9.2的utf8mb3（3字节gb3212字符集Unicode编码）
10.9.3 UTF8字符集（Alias utf8mb3）
10.9.4 UCS2字符集（UCS-2编码）
10.9.5的UTF16字符集（UTF-16 Unicode编码）
10.9.6 the utf16le（UTF - 16le Unicode字符集编码）
10.9.7 utf32（UTF-32字符集的Unicode编码）
10.9.8转换Unicode字符集之间的3字节和4字节
10.10支持的字符集和整理
10.10.1 Unicode字符集
10.10.2西欧字符集
10.10.3中欧字符集
10.10.4欧洲南部和中东的字符集
10.10.5波罗的字符集
10.10.6西里尔字符集
10.10.7亚洲字符集
10.10.8二进制字符集
10.11设置错误消息的语言
10.12添加字符集
10.12.1字符定义数组
10.12.2字符串排序复杂字符集支持
10.12.3多字节字符支持复杂的字符集
10.13添加整理到一个字符集
10.13.1 collation执行类型
10.13.2选择整理ID
10.13.3添加一个简单的整理到一个8位字符集
10.13.4加入UCA整理到一个Unicode字符集
10.14字符集配置
10.15本地MySQL服务器支持
11数据类型
11.1数据类型概述
11.1.1数字类型概述
11.1.2日期和时间类型概述
11.1.3字符串类型概述
11.2
11.2.1整数类型（精确值）整数int、smallint、TINYINT、MEDIUMINT，bigint
11.2.2固定点的类型（精确值）-十进制数字
11.2.3浮点类型（近似值）浮球式、双
11.2.4型位位值
11.2.5数值型属性
11.2.6超出范围和溢出处理
11.3日期和时间类型
11.3.1日期，日期，和时间戳类型
11.3.2时间类型
11.3.3年型
11.3.4迁移年（二）列年（四）
11.3.5自动初始化和更新时间和日期
11.3.6分数秒的时间值
11.3.7之间的转换日期和时间类型
在日期11.3.8两位数的年
11.4字符串类型
11.4.1的char和varchar类型
11.4.2的binary和varbinary类型
11.4.3 BLOB和文本类型
11.4.1 . Enum类型
11.4.5集合类型
11.5空间数据类型
11.5.1空间数据类型
11.5.2 OpenGIS的几何模型
11.5.3支持空间数据格式
11.5.4几何的合法性和有效性
11.5.5空间参考系统的支持
11.5.6创造空间列
11.5.7填充空间列
11.5.8获取空间数据
11.5.9优化空间分析
11.5.10创建空间索引
11.5.11使用空间索引
11.6 JSON数据类型
11.7数据类型的默认值
11.8数据类型的存储要求
11.9为一列选择正确的类型
11.10使用其他数据库引擎的数据类型
12函数和操作符
12.1功能及操作参考
12.2类型转换表达式求值
（3）运营商
12.3.1运算符的优先级
12.3.2比较函数和操作符
12.3.3逻辑运算符
12.3.4赋值运算符
12.4流程控制函数
12.5字符串函数
12.5.1字符串比较函数
12.5.2正则表达式
12.5.3字符集和功能结果的整理
12.6数值函数和操作符
12.6.1算术运算符
可以声明为任意类型的数学函数
12.7日期和时间函数
12.8什么是历用MySQL？
12.9全文搜索功能
12.9.1自然语言全文检索
12.9.2布尔全文搜索
12.9.3全文检索查询扩展
12.9.4全文构建
12.9.5全文限制
12.9.6微调MySQL全文搜索
12.9.7添加一个全文索引排序
12.9.8 Ngram全文解析
12.9.9 mecab全文解析插件
12.10铸造的函数和操作符
12.11 XML功能
12.12位函数和操作符
12.13加密和压缩功能
12.14信息功能
12.15空间分析功能
12.15.1空间函数参考
12.15.2参数空间功能处理
12.15.3函数创建几何值WKT值
12.15.4函数创建几何值从WKB近似值
12.15.5 MySQL特定的功能，创建几何值
12.15.6几何格式转换功能
12.15.7几何属性函数
12.15.8空间算子函数
12.15.9功能测试之间的几何对象的空间关系
12.15.10 Geohash函数空间
12.15.11 GeoJSON函数空间
12.15.12空间便利功能
12.16 JSON功能
12.16.1 JSON函数参考
12.16.2函数创建JSON值
12.16.3功能搜索JSON值
12.16.4函数修改JSON值
12.16.5函数返回JSON值属性
12.16.6 JSON表功能
12.16.7 JSON的实用功能
JSON的语法12.16.8路径
12.17函数使用全局事务ID。
12.18 MySQL企业加密功能
12.18.1企业加密装置
12.18.2企业加密使用的例子
12.18.3企业加密函数参考
12.18.4 Enterprise enCRIMENT Function Desence
12.19集（组）功能
12.19.1骨料（组）功能描述
12.19.2集团的编辑修改器
12.19.3 MySQL处理组
12.19.4检测功能的依赖
12.20窗函数
12.20.1窗口功能说明
12.20.2窗函数的概念和语法
12.20.3窗函数框架规范
12.20.4命名为Windows
12.20.5窗函数的限制
12.21内部函数
12.22多功能
12.23珍贵数学
12.23.1类型的数值
12.23.2小数数据类型特征
12.23.3表达处理
12.23.4舍入行为
12.23.5精密的数学例子
13 SQL语句语法
13.1数据定义语句
13.1.1原子数据定义语句的支持
13.1.2数据库语句的句法
13.1.3改变事件语法
13.1.4改变函数的语法
13.1.5改变实例的语法
13.1.6改变程序的语法
改变服务器13.1.7 syntax
13.1.8修改表的语法
阿尔斯特片合成器
13.1.10改变视图的语法
13.1.11创建数据库的语法
13.1.12创建事件语法
13.1.13创建函数的语法
13.1.14创建索引的语法
13.1.15创建过程和创建函数的语法
13.1.16创建服务器的语法
13.1.17创造空间参考系统的语法
13.1.18创建表的语法
肌酸片合成器
13.1.20创建触发器的语法
13.1.21创建视图的语法
13.1.22删除数据库的语法
排气合成器
13.1.24降功能语法
13.1.25删除索引的语法
13.1.26下降过程和降功能语法
13.1.27滴Server语法
13.1.28下降空间参考系统的语法
13.1.29下拉表的语法
13.1.30删除表空间语法
13.1.31删除触发器语法
13.1.32删除视图的语法
13.1.33重命名表语法
13.1.34截断表语法
13.2 . Data Managing statements
13.2.1调用语法
13.2.2删除语法
13.2.3的语法
13.2.4样本处理表
13.2.5进口表的语法
13.2.6插入语法
13.2.7 LOAD DATA INFILE语法
13.2.8加载XML语法
13.2.9替换语法
13.2.10 SELECT语法
13.2.11查询语法
13.2.12更新语法
13.2.13语法（公用表表达式）
13.3事务和锁的陈述
13.3.1启动事务，提交和回滚语法
13.3.2语句不能回滚
13.3.3陈述引起隐式提交
13.3.4保存点回滚保存点和两个保存点语法，释
13.3.5备份锁和解锁实例语法实例
13.3.6表加锁和解锁表语法
13.3.7事务语法
13.3.8 XA事务
13.4 .折叠定制
13.4.1控制主服务器的SQL语句
13.4.2控制从服务器的SQL语句
控制组的复制13.4.3 SQL语句
13.5编写的SQL语句的语法
13.5.1准备表
13.5.2执行语法
13.5.3释放准备表
13.6复合语句语法
13.6.1开始…端复合语句语法
13.6.2 syntax语言标签
13.6.3声明的语法
13.6.4变量中存储的程序
13.6.5流控制语句
13.6.6 cursors
13.6.7条件处理
13.7数据库管理报表
13.7.1账户管理报表
13.7.2资源集团管理报表
13.7.3表维护报表
13.7.4组件，插件，和用户定义的函数语句
13.7.5集语法
13.7.6显示语法
13.7.7其他管理报表
13.8实用语句
138.SYNTAX描述
13.8.2解释语法
13.8.3语法帮助
13.8.4使用语法
MySQL数据字典14
14.1数据字典模式
14.2去除基于文件的元数据存储
14.3事务性存储数据字典
14.4词典对象缓存
14.5 information_schema和数据字典的整合
14.6系列词典信息（SDI）
14.7数据字典的用法差异
14.8日词典的局限性
15 InnoDB存储引擎
15.1引言InnoDB
15.1.1使用InnoDB表的好处
15.1.2 InnoDB表的最佳实践
15.1.3验证InnoDB是默认的存储引擎
15.1.4测试和基准测试与InnoDB
15.2 InnoDB和酸模式
15.3 InnoDB的多版本
15.4 InnoDB建筑
15.4.1 Buffer Pool
15.4.2改变缓冲
15.4.3自适应哈希索引
15.4.4重做日志缓冲区
15.4.5球系统表空间
15.4.6 Doublewrite Buffer
15.4.7 UNDO日志
15.4.8文件每个表的表空间
一般15.4.9表空间
15.4.10 undo表空间
15.4.11临时表空间
15.4.12重做日志
15.5 InnoDB锁和事务模型
15.5.1 InnoDB锁定
15.5.2 InnoDB事务模型
15.5.3锁的不同设置SQL语句在InnoDB
15.5.4幻像行
15.5.5死锁在InnoDB
15.6 InnoDB配置
15.6.1 InnoDB启动配置
15.6.2配置InnoDB只读操作
15.6.3 InnoDB缓冲池的配置
15.6.4 InnoDB缓冲配置变化
15.6.5配置InnoDB线程并发
15.6.6配置背景InnoDB I/O线程数
15.6.7使用异步I/O的Linux
15.6.8配置InnoDB主线程I/O速率
15.6.9自旋锁轮询配置
15.6.10配置InnoDB净化调度
15.6.11配置优化器统计InnoDB
15.6.12配置合并阈值的索引页
15.6.13启用自动配置一个专用的MySQL服务器
15.7 InnoDB表空间
15.7.1 InnoDB SYSTEM表空间大小
15.7.2变化的数量或大小的InnoDB重做日志文件
15.7.3使用原始磁盘分区系统表空间
15.7.4 InnoDB表的表空间文件
15.7.5每表表空间创建外部数据文件的目录
15.7.6复制文件到另一个实例的每个表的表空间
15.7.7移动表空间文件，而服务器离线
15.7.8 undo表空间配置
15.7.9截断撤销表空间
一般15.7.10 innodb tablespace）
15.7.11 InnoDB表空间加密
15.8 InnoDB表和索引
15.8.1 InnoDB表
15.8.2 InnoDB索引
15.9 InnoDB表和网页压缩
15.9.1 InnoDB表压缩
15.9.2 InnoDB页面压缩
15.10 InnoDB行存储和列格式
15.10.1概述InnoDB的行存储
15.10.2指定行的格式表
15.10.3动态压缩行格式
15.10.4紧凑和多余的行格式
15.11 InnoDB的磁盘I/O和文件空间管理
15.11.1 InnoDB的磁盘I / O
15.11.2文件空间管理
15.11.3 InnoDB检查站
15.11.4整理表
15.11.5回收磁盘空间表
比InnoDB和在线DDL
15.12.1 DDL操作在线
15.12.2在线DDL性能和并发性
15.12.3在线DDL的空间要求
15.12.4简化在线DDL DDL语句
在线15.12.5 DDL失效条件
15.12.6在线DDL的局限性
15.13 InnoDB启动选项和系统变量
15.14 information_schema InnoDB表
15.14.1 InnoDB information_schema表压缩
15.14.2 InnoDB information_schema事务和锁定信息
15.14.3 InnoDB information_schema架构对象表
15.14.4 Innodb Information Control Information FullText Index Table
15.14.5 InnoDB缓冲池表information_schema
15.14.6 InnoDB information_schema度量表
15.14.7 InnoDB information_schema临时表信息表
15.14.8 InnoDB表空间元数据检索information_schema.files
15.15 InnoDB集成MySQL性能模式
15.15.1监测改变InnoDB表的使用性能模式表的进展
15.15.2监测InnoDB互斥等使用性能模式
15.16 InnoDB监视器
15.16.1 InnoDB监视器类型
15.16.2使InnoDB监视器
15.16.3 InnoDB标准监控锁监视器输出
15.17 InnoDB备份和恢复
15.17.1 InnoDB备份
15.17.2 InnoDB恢复
15.18 InnoDB和MySQL复制
15 InnoDB Memcached插件
在InnoDB Memcached插件15.19.1效益
15.19.2 Innodb Memcached架构
15.19.3设置innodb memcached插件
15.19.4 InnoDB Memcached多得到和范围查询支持
对于InnoDB Memcached插件15.19.5安全注意事项
15.19.6写InnoDB Memcached插件的应用
15.19.7 InnoDB Memcached插件和复制
15.19.8 InnoDB Memcached插件内部
15.19.9排除InnoDB Memcached插件
15.20 InnoDB故障排除
15.20.1 InnoDB I/O问题的故障排除
15.20.2迫使InnoDB恢复
15.20.3 InnoDB数据字典操作故障
15.20.4 InnoDB错误处理
16选择存储引擎
16.1设置的存储引擎
16.2 MyISAM存储引擎
16.2.1 MyISAM启动选项
16.2.2空间所需要的钥匙
16.2.3 Myisam table storagen格式
16.2.4 MyISAM表的问题
16.3内存存储引擎
16.4 CSV存储引擎
16.4.1检修CSV表
16.4.2 CSV局限性
16.5 ARCHIVE存储引擎
16.6黑洞的存储引擎
16.7合并存储引擎
16.7.1合并表的优点和缺点
16.7.2合并表格的问题
16.8联邦存储引擎
16.8.1联邦存储引擎概述
16.8.2如何创建联合表
16.8.3联邦存储引擎的笔记与心得
16.8.4联邦存储引擎资源
16.9例存储引擎
16.10其他存储引擎
16.11概述MySQL存储引擎体系结构
16.11.1式存储引擎架构
16.11.2通用数据库服务器层
17复制
17.1复制配置
17.1.1二进制日志文件的位置为基础的复制配置概述
17.1.2设置二进制日志文件的位置为基础的复制
下面的复制与全球事务标识符
17.1.4 MySQL多源复制
17.1.5改变复制模式的在线服务器
17.1.6复制和二进制日志记录选项和变量
17.1.7常见复制管理任务
17.2 .复制执行
17.2.1复制格式
17.2.2 .复制执行细节
17.2.3复制通道
17.2.4复制继电器状态日志
17.2.5服务器如何评价复制过滤规则
17.3复制解决办法
17.3.1使用复制备份
17.3.2处理复制奴隶意外停止
17.3.3监控基于行的复制
本使用不同的主从复制存储引擎
17.3.5使用规模复制
17.3.6复制不同的数据库，不同的奴隶
17.3.7提高复制性能
17.3.8大师在故障转移切换
17.3.9设置复制使用加密连接
17.3.10半同步复制
17.3.11延迟复制
17.4复制笔记与心得
17.4.1复制的特点和问题
17.4.2复制MySQL版本之间的兼容性
17.4.3升级复制设置
17.4.4排除复制
17.4.5如何报告复制错误或问题
18组复制
18.1组复制背景
18.1.1复制技术
情势和组复制使用案例
18.1.3组复制的细节
18.2入门
18.2.1部署在单个主模式组复制
18.3监测组复制
18.3.1 replication_group_member_stats
18.3.2 replication_group_members
18.3.3复制_连接_ status
18.3.4 replication_applier_status
18.3.5组复制服务器状态
18.4组的复制操作
18.4.1部署在多发或单个主模式
18.4.2调整恢复
18.4.3网络划分
18.4.4使用MySQL企业备份与复制组
18.5组复制安全
18.5.1 IP地址白名单
18.5.2安全套接字层（SSL）的支持
18.5.3虚拟专用网络（VPN）
18.6组复制系统变量
18.7要求和限制
18.7.1组复制的要求
18.7.Group Reliver阳离子限制
18.8交叉询问问题
18.9组复制的技术细节
18.9.1组复制插件体系结构
18.9.2组
18.9.3数据处理定制
18.9.4数据定义语句
为18.95分布式恢复
18.9.6可观测性
18.9.7组复制性能
19 MySQL的内核
20使用MySQL作为文件存储
20.1关键概念
20.2设置MySQL作为文件存储
20.2.1安装mysql
20.2.2启动mysql
20.3快速入门指南：JavaScript mysql
203.1 .导言
20.3.2导入数据库样本
20.3.3 MySQL的内核
20.3.4文件和收藏
20.3.5关系表
在Tables 20.3.6文件
20.4快速入门指南：python mysql
204.1 .导言
20.4.2导入数据库样本
20.4.3 MySQL的内核
20.4.4文件和收藏
20.4.5关系表
在Tables 20.4.6文件
20.5快速入门指南：Visual Studio的MySQL
20.6 X插件
20.6.1检查X插件安装
20.6.2禁用X插件
20.6.3使用安全X插件连接
20.6.4 X插件和缓存SHA-2认证插件
20.6.5 X插件选项和变量
20.6.6监测X插件
21 InnoDB集群
21.1介绍InnoDB集群
21.2创建一个InnoDB集群
21.2.1部署方案
21.2.2 InnoDB集群的要求
21.2.3安装方法
21.2.4 InnoDB集群生产部署
21.2.5沙箱InnoDB集群部署
21.2.6采用一组复制的部署
21.3使用MySQL InnoDB集群路由器
21.4 InnoDB集群的工作
21.5 known limitations
22分解
22.1分区概述MySQL
22.2分区类型
22.2.1范围划分
22.2.2列表分区
22.2.3栏目划分
22.2.4 hash分解
22.2.5密钥分配
22.2.6分区
22.2.7 MySQL如何分割处理空
22.3分区管理
22.3.1管理范围和列表分区
22.3.2哈希分区管理和重点
22.3.3交换分区和子分区表
22.3.4维护分区
22.3.5获得信息的分区
22.4分区修剪
2.2.5分区选择
在分区22.6限制
原发性22.6.1分解钥匙和钥匙，钥匙，特制
22.6.2划分的局限性与存储引擎
22.6.3划分的局限性与功能
23存储程序和视图
2定义存储的程序
23.2使用存储子程序（过程和函数）
23.2.1存储程序的语法
23.2.2存储程序和MySQL的特权
23.2.3存储程序的元数据
23.2.4存储过程，函数，触发器，和last_insert_id()
23.3使用触发器
23.3.1 Trigger Syntax和例子
23.3.2触发元数据
23.4使用事件调度器
23.4.1事件调度程序概述
23.4.2事件调度器配置
Event Sootax
23.4.4事件元数据
23.4.5状态事件调度器
23.4.6事件调度器和MySQL的特权
23.5使用视图
23.5.1景语法
23.5.2视图处理算法
23.5.3更新和插入的观点
23.5.4观检查选项条款
23.5.5查看元数据
23.6访问控制用于存储程序和视图
23.7二进制日志存储程序
24 information_schema表
24.1 information_schema character_sets表
24.2 information_schema排序表
24.3 information_schema collation_character_set_applicability表
24.4 information_schema列表
24.5 information_schema column_privileges表
以上的information_schema column_statistics表
24.7 information_schema引擎表
24.8 information_schema事件表
24.9%的information_schema文件表
24.10 information_schema key_column_usage表
24.11 information_schema关键词表
24.12 information_schema optimizer_trace表
24.13的information_schema参数表
24.14 information_schema分区表
为的information_schema插件表
24.16 information_schema列表表
24.17 information_schema分析表
24.18 information_schema referential_constraints表
24.19 information_schema resource_groups表
24.20 information_schema程序表
24.21 information_schema图式表
24.22 information_schema schema_privileges表
幅员的information_schema统计表
24.24 information_schema st_geometry_columns表
24.25 information_schema st_spatial_reference_systems表
24.26 information_schema表表
占的information_schema表空间表
24.28 information_schema table_constraints表
24.29 information_schema table_privileges表
24.30 information_schema触发器表
24.31 information_schema user_privileges表
24.32 information_schema意见表
24.33的information_schema view_routine_usage表
24.34 information_schema view_table_usage表
24.35 information_schema InnoDB表
24.35.1的information_schema innodb_buffer_page表
24.35.2的information_schema innodb_buffer_page_lru表
24.35.3的information_schema innodb_buffer_pool_stats表
24.35.4的information_schema innodb_cached_indexes表
24.35.5的information_schema innodb_cmp和innodb_cmp_reset表
24.35.6的information_schema innodb_cmpmem和innodb_cmpmem_reset表
24.35.7的information_schema innodb_cmp_per_index和innodb_cmp_per_index_reset表
24.35.8的information_schema innodb_ft_being_deleted表
24.35.9的information_schema innodb_ft_config表
24.35.10的information_schema innodb_ft_default_stopword表
24.35.11的information_schema innodb_ft_deleted表
24.35.12的information_schema innodb_ft_index_cache表
24.35.13的information_schema innodb_ft_index_table表
24.35.14的information_schema innodb_locks表
24.35.15的information_schema innodb_lock_waits表
24.35.16的information_schema innodb_metrics表
24.35.17的information_schema innodb_columns表
24.35.18的information_schema innodb_datafiles表
24.35.19的information_schema innodb_fields表
24.35.20的information_schema innodb_foreign表
24.35.21的information_schema innodb_foreign_cols表
24.35.22的information_schema innodb_indexes表
24.35.23的information_schema innodb_session_temp_tablespaces表
24.35.24的information_schema innodb_tables表
24.35.25的information_schema innodb_tablespaces表
24.35.26的information_schema innodb_tablespaces_brief表
24.35.27的information_schema innodb_tablestats观
24.35.28的information_schema innodb_virtual表
24.35.29的information_schema innodb_temp_table_info表
24.35.30的information_schema innodb_trx表
24.36 information_schema线程池表
24.36.1的information_schema tp_thread_group_state表
24.36.2的information_schema tp_thread_group_stats表
24.36.3的information_schema tp_thread_state表
24.37 information_schema连接控制表
24.37.1的information_schema connection_control_failed_login_attempts表
24.38扩展显示报表
25 MySQL性能模式
25.1绩效模式快速启动
25.2绩效模式生成配置
25.3绩效模式启动配置
25.4性能模式运行时配置
25.4.1性能架构事件时序
25.4.2性能架构事件过滤
25.4.3事件预滤波
25.4.4预滤波的仪器
25.4.5预过滤的对象
25.4.6预滤波的线程
25.4.7预滤波的消费者
254.8例证
25.4.9命名工具或消费者对过滤操作
25.4.10确定什么是仪表
25.5绩效模式查询
最大性能模式仪器的命名约定
25.7性能模式状态监测
25.8绩效模式的原子和分子事件
25.9绩效模式语句消化和采样
25.10绩效模式一般特征表
25.11绩效模式表描述
25.11.1性能架构表索引
25.11.2性能模式设置表
25.11.3绩效模式实例表
25.11.4性能模式等事件表
25.11.5表现图式阶段事件表
25.11.6性能架构声明事件表
25.11.7性能模式交易表
25.11.8性能模式连接表
25.11.9性能模式连接属性表
25.11.10性能模式用户变量表
25.11.11性能架构复制表
25.11.12性能模式锁定表
25.11.13性能架构系统变量表
25.11.14性能模式状态变量表
25.11.15性能模式汇总表
25.11.16性能模式杂表
25.12性能模式选项和变量引用
25.13性能模式命令选项
25.14绩效模式的系统变量
25.15性能模式状态变量
25.16性能架构的内存分配模型
25.17性能模式和插件
25.18使用性能模式来诊断问题
25.18.1查询使用性能模式分析
26 MySQL系统架构
26.1先决条件使用SYS模式
26.2使用SYS模式
26.3系统架构的进展报告
26.4系统架构对象参考
26.4.1系统架构对象索引
26.4.2 sys模式表和触发器
26.4.3系统架构视图
26.4.4系统架构的存储过程
26.4.5 sys模式存储功能
27连接器和API
27.1 MySQL连接器/ C
27.2 MySQL连接器/ C
27.3 MySQL连接器/ J
27.4 MySQL连接器/网
27.5 MySQL连接器/ ODBC
27.6 MySQL连接器/ Python
27.7 MySQL C API
27.7.1 MySQL C API的实现
27.7.2同时MySQL服务器和连接器/ C装置
27.7.3示例C API的客户端程序
27.7.4构建和运行的C API的客户端程序
27.7.5 C API的数据结构
27.7.6 C API函数概述
12.7 c c API function defunction
27.7.8 C API的准备好的语句
27.7.9 C API编写报表的数据结构
27.7.10 C API编写的语句功能概述
27.7.11 C API编写的语句功能说明
27.7.12 C API螺纹功能描述
27.7.13 C API函数的客户端插件
27.7.14 C API接口的二进制日志
27.7.15 C API的二进制日志中的数据结构
27.7.16 C API的二进制日志功能概述
27.7.17 C API的二进制日志功能描述
27.7.18 C API加密连接支持
27.7.19 C API多语句执行支持
27.7.20 C API编写的语句处理日期和时间值
27.7.21 C API编写的调用语句支持
27.7.22 C API编写的语句的问题
27.7.23 C API的可选的结果集元数据
27.7.24 C API自动重联控制
27.7.25 C API的常见问题
27.8 MySQL，PHP的API
27.9 MySQL Perl API
MySQL的Python API的范围
27.11 MySQL Ruby API
27.11.1 MySQL / Ruby API
27.11.2红宝石/ MySQL的API
27.12 MySQL TCL API
MySQL的包装小于艾菲尔
28扩展MySQL
28.1 MySQL内部
28.1.1 MySQL线程
28.1.2 MySQL测试套件
28.2 mysql插件API
28.2.1类型的插件
28.2.2插件API特性
28.2.3零件插件API
28.2.4编写插件
28.3 MySQL服务插件
28.3.1锁定服务
28.3.2到此服务
28.4添加新的功能到MySQL
的用户定义的函数接口28.4.1特征
28.4.2添加一个新的用户定义的函数
28.4.3添加一个新的原生功能
调试和移植MySQL 28.5
28.5.1调试一个MySQL服务器
28.5.2调试MySQL客户端
28.5.3该包的
MySQL企业版29
MySQL企业监控器概述29.1
29.2 MySQL企业备份概述
29.3 MySQL企业安全概述
2 MySQL企业加密概述
29.5 MySQL企业审计概述
29.6 MySQL企业防火墙概述
29.7企业概述MySQL线程池
30 MySQL Workbench
MySQL 8的常见问题
A.1一般为MySQL的常见问题：
A.2 MySQL存储引擎时常见问题：
A.3 MySQL服务器的SQL模式8常见问题：
A.4 MySQL 8常见问题：存储过程和函数
A.5 MySQL 8常见问题：触发
结合MySQL 8常见问题：观点
A.7 MySQL 8常见问题：information_schema
8 MySQL 8常见问题：迁移
MySQL安全8.0出来的常见问题：
A.10 MySQL 8常见问题：MySQL集群
A.11 MySQL 8常见问题：MySQL的中国，日本，和koreancharacter集
a.12 MySQL 8常见问题：连接器和API
a.13 MySQL 8常见问题：复制
a.14 MySQL 5.0 FAQ：MySQL企业线程池
A.15 MySQL 8常见问题：InnoDB Change Buffer
8常见问题：“16 MySQL InnoDB表空间加密
A.17 MySQL 8常见问题：虚拟化支持
B错误，错误代码，及常见问题
B.1错误信息来源
B类错误值
3服务器错误代码和消息
B客户端错误代码和消息
B问题和常见错误
b.5.1如何确定是什么原因造成的问题
b.5.2常见错误使用MySQL的程序
b.5.3管理相关问题
b.5.4查询相关问题
b.5.5优化器的相关问题
b.5.6表定义的相关问题
b.5.7已知问题在MySQL
C限制和限制
C.1限制存储的程序
C限制条件的处理
C限制服务器端游标
在子查询支付限制
食用限制的观点
C.6限制我们XA事务
有权限制的字符集
在性能模式c的限制
C限制认证
C限制MySQL
c.10.1限制加入
c.10.2限制对数据库和表的数量
c.10.3限制表的大小
c.10.4限制表的列数和行的大小
c.10.5 Windows平台的局限性
D指标
总指数
C功能指数
命令索引
功能指数
information_schema指数
连接类型指标
算子的指标
选择指数
特权指数
SQL模式指标
声明/语法指标
状态变量指标
系统变量指标
事务隔离级别指数
MySQL的词汇

```
这里输入代码
```
 


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)