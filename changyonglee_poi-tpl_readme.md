# poi-tpl

## 介绍
在做数据类或办公类系统时，往往需要将数据导出为excel文档，excel格式要求各种各样，如果为每个excel样式都定制开发，工作量会非常大并且日后若做调整又得重新开发，很是不方便。本项目基于POI实现了基于excel定制模板，然后填充数据，完成excel导出，若要调整excel结构，只需要重新定义excel模板，无需更改代码。

## 软件架构
软件架构说明


## 安装教程

1. 下载代码
2. 使用mvn package 或mvn install 打包成jar加入到工程中
3. 准备数据（参见“准备数据“章节）
4. 定义模板（参见“定义模板”章节）
5. 调用接口生成文件

## 名词解释
1. 上下文: excel数据模型,为JSONObject对象;
2. 变量: 变量一般为n个数字字母下划线组成,对应上下文中的key, 实际值即为上下文中对应的value.
3. 直接量: 相对"变量"而言, 直接量不会经上下文转换,也就是说传入的值即实际的值.

## 准备数据

1. 项目采用fastjson作为基本数据模型, 因此,我们可以将需要在excel中展示的数据集中成一个JSONObject对象, 成为"上下文";
2. xxxx
3. xxxx

## 定义模板

excel模板目前支持xls格式, excel中需要填充数据的单元格使用函数,其他固定部分则按照普通excel设计方式设计.
excel函数采用${}包裹, 函数形式为XXX（aaa,bbb,...）形式, 期中XXX为函数名称, () 为函数参数列表, 期中函数参数列表中的参数为直接量或函数.

模板中支持的excel函数:

1. V 变量函数.接受一个参数, 参数对应上下文中的key, 也可以简单标识为${aaa}, aaa即一个变量, 常量也可标识为${'aaa'}, 即传入一个aaa字符串, 注意:函数列表中的参数均为直接量,如果需要传变量则需要用V函数.
2. SUM 求和函数
3. GRID 表格函数
4. GMERGE 表格内勤函数, 合并单元格
5. CONCAT 字符串拼接函数

## 参与贡献

1. Fork 本仓库
2. 新建 Feat_xxx 分支
3. 提交代码
4. 新建 Pull Request


## 码云特技

1. 使用 Readme\_XXX.md 来支持不同的语言，例如 Readme\_en.md, Readme\_zh.md
2. 码云官方博客 [blog.gitee.com](https://blog.gitee.com)
3. 你可以 [https://gitee.com/explore](https://gitee.com/explore) 这个地址来了解码云上的优秀开源项目
4. [GVP](https://gitee.com/gvp) 全称是码云最有价值开源项目，是码云综合评定出的优秀开源项目
5. 码云官方提供的使用手册 [https://gitee.com/help](https://gitee.com/help)
6. 码云封面人物是一档用来展示码云会员风采的栏目 [https://gitee.com/gitee-stars/](https://gitee.com/gitee-stars/)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)