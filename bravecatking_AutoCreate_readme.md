AutoCreate —— 基于 Jfinal 和 beetl 实现的自动代码生成
===============

AutoCreate 是 数据库链接采用Jfinal ActiveRecordPlugin，模板配置采用beetl，实现根据模板自动生成项目代码。

*  默认模板目录：/autopath/template/project/
*  自带三套模板beetl（生成beetl文件）、jsp（生成jsp文件）、jflyfox（生成本人jflyfox个人博客项目文件）
*  默认自动生成输出目录：/autopath/output/ 
*  启动文件：com.jflyfox.client.AutoCreateClient
* 生成表需要有表注释和字段注释。（写注释也是个好习惯哦）

## 配置说明

* src/main/java/conf/db.properties 配置链接的数据库信息
* src/main/java/conf/template.properties 配置使用模板，生成路径和生成那些表
* template.selected参数 制定下面已经存在的模板key
* template.tables参数 设定生成那些表；不填和all会生成数据库所有表；多个表明用逗号分隔
* src/main/java/conf/config.properties 配置beetl模板参数

## 参数说明

主要通过CRUD和ModelAttr进行模板展示

***CRUD***
```
	private Table table;
	/**
	 * 主键
	 */
	private String primaryKey;
	/**
	 * url key 关键字
	 */
	private String urlKey;
	/**
	 * 名称
	 */
	private String name;

	private final Map  map = new LinkedHashMap ();
	private final Map  searchMap = new LinkedHashMap ();
	private final Map  listMap = new LinkedHashMap ();
	private final Map  addMap = new LinkedHashMap ();
	private final Map  editMap = new LinkedHashMap ();
	private final Map  viewMap = new LinkedHashMap ();
```

***ModelAttr***
```
        /**
	 * 字段key
	 */
	private String key;
	/**
	 * 字段名称
	 */
	private String name;
	/**
	 * 编辑类型
	 */
	private FormType formType = FormType.INPUT;
	/**
	 * Input类型
	 */
	private InputType inputType = InputType.TEXT;
	/**
	 * 编辑数据
	 */
	private String formTypeData = "";
	/**
	 * 验证方式
	 */
	private String formTypeValid = "";
	/**
	 * 是否可以为空
	 */
	private boolean isNull;
	/**
	 * 是否是数字
	 */
	private boolean isNumber;

	/**
	 * 数据展示
	 * 
	 * @see 学以致用，不嫌麻烦~！~
	 * 
	 * @see 8位，前四位保留;后三位，
	 * @see 查询,展示列表，添加列表，编辑列表，查看列表
	 * @see 1表示展示，0表示隐藏
	 */
	private byte operate;
```

## 运行方法

***Main函数运行***

> com.jflyfox.client.AutoCreateClient

***bat执行***

> start.bat

# 鸣谢
 1. [JFinal](http://www.oschina.net/p/jfinal)
 2. [beetl](http://ibeetl.com/community/)
 3. [oschina](http://www.oschina.net/)

# 开源赞助
![OSC@GIT](http://static.oschina.net/uploads/space/2015/0213/104940_ZKNb_166354.png "开源赞助我(支付宝)")


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)