JMDA开源项目源动力

  1. 在炎黄盈动工作6年，就职架构师一岗位，一直研究模型驱动开发平台和工作流引擎。
  2. 在离开炎黄之后，一直在做电商ERP业务，经过几次硬代码开发项目之后，历练出JMDA开发平台。
  3. JMDA只是个开源工具，用模型驱动的方式，解决项目开发过程中的难题，达到快速迭代，代码生成器等等。
  4. 后期还会结合当前ERP业务平台的模型推出一些列视频教程，与热爱开发平台与ERP软件的同学一起交流。

JMDA架构

![输入图片说明](http://git.oschina.net/uploads/images/2016/0617/155825_ba2bfd4d_453616.png "在这里输入图片标题")



项目截图

 列表建模工具

![列表建模工具](http://git.oschina.net/uploads/images/2016/0617/155332_c21a6904_453616.png "列表建模工具")
 表单建模工具

![表单建模工具](http://git.oschina.net/uploads/images/2016/0617/155347_fe6b474e_453616.png "表单建模工具")
表单建模工具

![表单建模工具](http://git.oschina.net/uploads/images/2016/0617/155357_f886febc_453616.png "表单建模工具")
列表模型运行

![列表模型运行](http://git.oschina.net/uploads/images/2016/0617/155406_86b155af_453616.png "列表模型运行")
表单模型运行

![表单模型运行](http://git.oschina.net/uploads/images/2016/0617/155415_bd7f7a5d_453616.png "表单模型运行")

登录 

URL地址: http://127.0.0.1:8081/jmda-web/console
注：此处应根据web工程名称访问
应用模型库
业务模型是指为达成对一个业务行为的描述和控制而抽象出的一组结构，这种具有语法、语义的结构既能够让 IT 和业务人员达成沟通，又能够让计算机去识别和执行。
新建模型分类
1.    点击工具条【新建】图标，选择【请输入模型分类名称】对话框
2.    输入一个新分类名，点击【确定】按钮，完成操作
 
 
列表模型

列表模型的目的是对流程和非流程数据管理应用提供全新的建模、执行引擎，满足客户对
数据管理的要求，包括：

1. 基本 CRUD 操作（Create、Read、Update、Delete）和按钮工具条
2. 简单实施即可满足典型主界面需求，可通过代码事件完成复杂个性需求
a) 提供简单模糊、条件组合查询器
b) 简单列表过滤、树形导航过滤
c) 总结三类典型的布局框架（传统、导航树）
d) 详细数据展示行为（内嵌下方、弹出层窗口、弹出新 Tab 页、弹出新窗体）
新建列表模型
1.    点击‘业务模型◢列表模型’
2.    点击工具条新建图标，选择【新建数据列表】 ，弹出【新建数据列表】对话
框
3.    输入【列表标题】 ，选择【表单名称】和【模型分类】 ，点击【确定】按钮，弹出数据列表
向导窗口
 
 
基本信息

在基本信息页填写，查询SQL，扩展的js或者css文件
 
属性项    说明
列表名称    进入该主模块给用户显示的标题，例如‘财务系统_经济分类’
模型分类    所有业务模型的通用属性，用于标识该模型属于哪类业务区域
唯一标识    系统自动生成的数据列表唯一标识号
查询SQL    列表显示的数据的查询SQL，其中???为系统标签，动态替换为查询条件
模版文件    系统默认的模版文件样式(支持树与列表同时存在模式配置)
扩展JavaScript/CSS    跟进业务自定义扩展的JavaScript/CSS文件内容，${basePath}标识为当前web工程路径
显示列
点击“添加”按钮，选择要显示的字段，点击右上方的“模拟运行”查看显示效
果
 
 
属性项    说明
字段    数据库字段名称
标题    列表显示标题
宽度    列表显示宽度
模糊查询    是否支持模糊查询（该功能暂时未实现）
是否排序    是否支持排序
对齐数据    数据显示时对齐方式
格式化函数    支持列的格式化js方法，可参考easyui  grid的格式化函数

工具条

  数据列表功能按钮区

 
点击添加系统默认添加，新建，修改，删除三个功能按钮
属性项    说明
名称    按钮名称
提示    悬浮按钮给予的提示信息（暂时没实现该功能）
图标    功能按钮icons
事件    当按钮点击被触发式响应的js函数事件
自定义UI    跟进业务可进行自定义的HTML查询显示，存在自定义UI则不执行（名称，提示，图标，事件）的配置信息
查询条件




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)