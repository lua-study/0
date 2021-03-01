# 和平之翼代码生成器SMEU版

## 本代码生成器全面支持前后端分离界面了(Excel,SGS)

欢迎大家使用由无垠式，和平之翼和光三代动词算子式代码生成器组成的动词算子式代码生成器阵列，在我的码云站点
[https://gitee.com/jerryshensjf/](https://gitee.com/jerryshensjf/)
大家可以找到这些代码生成器。把他们统统部署在Tomcat中，您可以获得超过600N的代码变形能力。


### 最近进展

已释出和平之翼代码生成器SMEU 4.1.0 Beta3版。可去本站附件下载二进制war包发行版：[https://gitee.com/jerryshensjf/PeaceWingSMEU/attach_files](https://gitee.com/jerryshensjf/PeaceWingSMEU/attach_files)，推荐使用Tomcat 8.5 作为应用容器。

和平之翼代码生成器SMEU 4.1.0 Beta3版全面支持同时生成Vue+ElementUI的前后端分离的前端项目(Excel,SGS)和原有的SMEU的后端项目。非常简易和强大，您值得一试。

前端项目截图：
登录：
![登录](https://images.gitee.com/uploads/images/2019/0415/214758_8c47b686_1203742.png "vue_login.png")

Grid:
![Grid](https://images.gitee.com/uploads/images/2019/0415/214815_c2dfdd1e_1203742.png "vue_bonuses.png")

多对多：
![多对多](https://images.gitee.com/uploads/images/2019/0415/220549_b19d2ca4_1203742.png "Vue_mtm.png")

编辑，下拉列表：
![输入图片说明](https://images.gitee.com/uploads/images/2019/0416/085420_45584d04_1203742.png "vue_update_dropdown.png")

#### 前端项目运行使用方法。
此前端界面例程的使用，下载和平之翼代码生成器SMEU版4.0.0 RC版，运行此代码生成器，同时生成相应的前端和后端项目。运行此后端项目。

将前端界面项目解压。如果没有安装Nodejs，请先安装。在解压的前端界面文件夹内运行 npm install命令。运行好后运行npm run dev

一切就绪后访问 http://localhost:8000/ 即可使用此前端项目。

### 最新研发动态

和平之翼代码生成器SMEU 4.1.0 Beta3宝船(Treasure Ship)已公布，欢迎在本站附件处下载正式版二进制war包。

最新的正式版为和平之翼代码生成器SMEU 4.0.0 宝船。本版主要改进了多重多对多关系及其初始化数据功能。从Beta 4开始，支持Excel数据导出。对Oracle数据库的支持进行了全面测试。并排除了相关错误。

最近，完成了对EasyUI的升级，并完成了POI Excel导出功能。完成了自动textarea功能，凡字段名中含有content,description和comment字串的字段，会被自动设置为textarea。这些特性会包含在和平之翼4.0.0 Beta4和以后的版本中。

正式版有如下优点：

1. 支持Excel格式数据导出
1. 支持两个域对象间多重多对多关系
1. 支持多重多对多和多对多关系的初始化数据
1. 支持两个域对象间多重一对多关系
1. 默认生成界面为Excel模板生成界面
1. 新增在线问答文档
1. 在线文档更新，配图
1. 默认生成界面改为Excel模板代码生成


截图为多重多对多和初始数据的效果：

![输入图片说明](https://images.gitee.com/uploads/images/2019/0218/161033_774e9447_1203742.png "TS_mmtm.png")

截图为Excel数据导出结果的效果：
![输入图片说明](https://images.gitee.com/uploads/images/2019/0224/204505_7c136333_1203742.png "TS_Excel_out.png")

### 交流QQ群
无垠式代码生成器群  277689737

### 现有主要功能清单

1. 十余种单表操作
1. 一对多关系
1. 多对多关系，采用4种双表操作实现
1. 多重多对多关系，采用多对多别名实现
1. 多重一对多关系，采用一对多别名实现
1. 标准生成器脚本（SGS）支持
1. Excel代码生成支持
1. 初始数据导入
1. 缺省Excel数据导出
1. id和DomainId两种格式主键支持
1. delete和deleted删除标志自动反义功能
1. MySQL/MariaDB支持
1. Oracle支持
1. 详细的编译警告和编译错提示
1. 编译警告支持
1. Eclipse JEE版兼容的代码生成物
1. 整站代码生成
1. 源文件或源代码自动保存
1. 数据库脚本自动生成
1. 详细的在线理论文档
1. 详细的用户手册和安装说明
1. 丰富的代码示例
1. EasyUI界面支持
1. 已支持跨域以支持前后端分离，未来将直接生成前端项目
1. 新增在线问答文档
1. 前后端分离界面例程已包含，例程使用的技术是Vue和ElementUI


### 近期研发计划

4.0.0宝船完成后，将开始4.1.0宝船的研发。4.1版将进行重大的引擎升级，大大增加代码生成器的实用性，增加对更多数据类型的支持。4.2版拥有默认的登录模块，可能还有字典模块。这些模块演示了名词，名词性动词的概念，具备强大的变形能力，所以被称为弹性模块。

在差不多同时，弹性模块也会在无垠式代码生成器JEEEU版Elsa冰雪女王上实现。

还有第三代动词算子式代码生成器光的第一个版本Enlightment启蒙将开始研发。光对技术进行了简化和重构，不再支持SGS标准生成器脚本，统一使用Excel模板进行代码生成。并且，光的Oracle支持将重新实现，采用一套基础代码同时支持Mysql，MariaDB和Oracle。欢迎大家围观。

### 质量提高计划

为了提高本生成器的效能和用户体验，计划对代码本代码生成器的编译错和编译警告子系统进行彻底的增强。如果你在使用的时候您的SGS源码或者Excel模板在生成时出错或者给出的提示叫您不知如何处理，请把这些原始文件Email我：jerry_shen_sjf@qq.com

如果您的源文件有帮助，这些文件将作为标准测试集的一部分，而您，也将出现在贡献者名单里。期望得到大家的帮助。

### 4.0.0 新特性清单

现在宝船已支持： 

1. 高低两种分辨率的UI
1. 个性化题头，副题头和页脚
1. 支持跨域
1. 支持两个对象间的多重多对多关系：比如一个论坛中的主题和用户之间存在多重多对多关系：点赞和收藏
1. 升级至Spring框架至4.2版。
1. 宝船的Excel模板代码生成支持三种Office:MS Office, WPS Office和Libreffice,模板需保存成xls格式
1. 宝船增加了激活和批激活两个动词
1. 需要注意，宝船代码生成器的编译兼容性为JDK 8，生成物仍然兼容JDK 7
1. SGS脚本中支持双引号括起来的字符串
1. EasyUI版本升级至1.7.2
1. 新增POI Excel格式数据导出功能
1. 已支持跨域以支持前后端分离，未来将直接生成前端项目
1. 新增在线问答文档
1. 前后端分离界面例程已包含，例程使用的技术是Vue和ElementUI


### 本代码生成器特色

本代码生成器是超级语言（SGS 标准生成器脚本）驱动的先进编译系统。旨在演示数据驱动的代码生成器固有的生产率上的优势和与标准编译器（Java语言）的良好协作关系。在未来，更先进的代码生成器和编译器的组合会显现出巨大的生产力优势，让我们一起促成这一天所需要的技术的进化循环。

### 用户注意

注意，本作品为火鸟（Rocketship 沈戟峰）个人作品，为开源的代码生成器，并不收取费用，也未曾委托其他的公司，如果有公司声称是它的作品，并进行网络推广活动和收取费用，皆不属实，希望所有用户注意。

### 项目代号宝船的图片

![输入图片说明](https://images.gitee.com/uploads/images/2018/0708/224107_74d3ac15_1203742.jpeg "TreasureShip.jpg")

![输入图片说明](https://images.gitee.com/uploads/images/2019/0304/142601_28769983_1203742.jpeg "ts.jpg")


### 动词算子的力量

向Lisp和Lambda算子致敬

愿动词算子的力量与你同在

![输入图片说明](https://images.gitee.com/uploads/images/2019/0109/211947_432567db_1203742.png "magic_v.png")

### 项目截图

Excel生成界面：
![输入图片说明](https://images.gitee.com/uploads/images/2019/0604/220503_7a80a6e0_1203742.png "new_ts_excel.png")

传统的SGS（标准生成器脚本）生成界面，支持SGS语法加亮：
![输入图片说明](https://images.gitee.com/uploads/images/2019/0604/215435_d4e41b80_1203742.png "ts_sgs.png")

Excel模板：

![输入图片说明](https://images.gitee.com/uploads/images/2019/0604/215508_e8a63584_1203742.png "excel_project.png")

![输入图片说明](https://images.gitee.com/uploads/images/2019/0604/215531_09ddde85_1203742.png "excel_domain.png")

![输入图片说明](https://images.gitee.com/uploads/images/2019/0604/215543_46fa9cfa_1203742.png "excel_multi.png")

在线文档：

![输入图片说明](https://images.gitee.com/uploads/images/2018/1226/224238_9c8cce80_1203742.png "lt_index.png")

![输入图片说明](https://images.gitee.com/uploads/images/2019/0619/214129_b6be6ce7_1203742.png "ts_lt8.png")

![输入图片说明](https://images.gitee.com/uploads/images/2019/0619/214148_09866b7c_1203742.png "ts_lt12.png")

![输入图片说明](https://images.gitee.com/uploads/images/2019/0619/214257_cd1df03c_1203742.png "ts_lt14.png")

在线问答文档：

![输入图片说明](https://images.gitee.com/uploads/images/2019/0619/214327_8f72b68e_1203742.png "ts_qa.png")

代码生成物截图
![输入图片说明](https://images.gitee.com/uploads/images/2019/0604/215707_80e97d7e_1203742.png "ts_result_grid.png")

代码生成物多对多界面截图
![输入图片说明](https://images.gitee.com/uploads/images/2019/0604/215738_061349b1_1203742.png "ts_result_mtm.png")

代码生成物下拉列表截图
![输入图片说明](https://images.gitee.com/uploads/images/2019/0604/215811_8ed1a55e_1203742.png "ts_grid_dropdown.png")

![输入图片说明](https://images.gitee.com/uploads/images/2019/0604/215831_891cc31f_1203742.png "ts_update_dropdown.png")


代码生成物更新界面截图：
![输入图片说明](https://images.gitee.com/uploads/images/2019/0604/220447_fe48684f_1203742.png "ts_result_update.png")


和平之翼代码生成器SMEU版，一键支持下拉列表和多对多，已支持Oracle数据库。

SMEU技术栈支持JQuery Easy UI,Spring MVC4,spring4, MyBatis 3。

本版支持下拉列表，使用者只需要在域对象相应的外键字段设定dropdown:DomainName fieldName;
即下拉列表：外键域名 字段名，即可一键支持下拉列表（外键）。

本版支持多对多关系，只要在多对多关系的主域对象中定义了
manytomanyslave:slaveDomainName即可在生成的功能和数据库定义中支持了两者的多对多
关系。

和平之翼代码生成器是动词算子式Java通用代码生成器，是无垠式代码生成器的第二代。
支持Oracle数据库，您只需要定义dbtype:oracle即可支持Oracle数据库，详细情况请看相关示例。

### 翅膀
和平之翼代码生成器图标，翅膀：

![输入图片说明](https://images.gitee.com/uploads/images/2018/1105/161512_b814baaa_1203742.jpeg "peacewing.jpg")

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)