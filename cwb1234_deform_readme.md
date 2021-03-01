# 基于雷劈网的表单设计器扩展，java实现后台解析（插件内容和字段和原版有一定改变）。致敬雷劈网. [http://formdesign.leipi.org/](http://formdesign.leipi.org/)


解析全部由java处理，时间紧迫，代码实现上不考虑太多的效率问题。原有控件部分已经屏蔽，如果大家感兴趣可以联系我一起加进来，另外如果控件有需要新增也可以联系本人(jjxliu306@163.com)。

 **演示地址：** [http://211.159.185.23:9999/form/index](http://211.159.185.23:9999/form/index)
 

 **最新修改：** 
    目前 radio，select，checkbox均支持ajax从后台获取数据进行列表组合。


 **数据表两个：** 


drop table if exists form; 
-- 自定义的工单 
create table form( 
	form_id	int auto_increment primary key , 
	form_name varchar(255), 
  	template text, -- 页面编辑好的原始html 
  	html text   , -- 反解析出来的页面html代码(设计到定义的select lictrl等控件要解析出展示代码) 
  	data text, -- 自定义的各个控件字段的jsonarray格式存储 
  	parse text , 
  	fields integer,  
	crtime timestamp, 
	modify_time timestamp 
);
 
 
drop table if exists entry; 
-- 保存各个工单填写的记录 
create table  entry( 
	id	int auto_increment primary key   , 
	form_id	int ,  -- 填写的动态工单ID 
	value	text,   -- 实际为json格式，存储此次填写的动态表单数据 
	crtime timestamp , 
	modify_time	timestamp  
	); 
	 
	 

动态表单绘制完毕后由后台解析并存储到数据库，后续每次发起的工单通过form中的html在页面进行绘制。工单填写完毕通过页面将form表单内容jsonobject之后交由后台验证并保存。 


### 以下是目前此项目的一些截图。



 **1、动态表单新增** 

![输入图片说明](https://gitee.com/uploads/images/2018/0126/140058_5ee2d045_146738.jpeg "1516945803(1).jpg")

 **2、动态表单预浏览** 

![输入图片说明](https://gitee.com/uploads/images/2018/0126/140149_0990d096_146738.jpeg "preview.jpg")

 **3、填写已设置动态表单的工单** 

![输入图片说明](https://gitee.com/uploads/images/2018/0126/140237_a410d034_146738.jpeg "edit.jpg")

 **4、工单浏览查看（readonly）** 

![输入图片说明](https://gitee.com/uploads/images/2018/0126/140310_b9ae03d2_146738.jpeg "view.jpg")


###  **功能实现:** 

雷劈网动态表单中原有的字段大部分均添加了一些修改，譬如非空（notnull），将name和title区分开，增加select，radios，checkbox选项的数据从填写的url中通过ajax获取等。详细如下：

 **1、** 针对text，textarea，select，checkboxs，listctrl，datepicker（自增控件）添加notnull非空选项，勾选此选项后，后续数据输入均会在后端进行非空验证（针对text中int，email等类型也会进行格式验证）.

 **2、** listctrl屏蔽单位、合计、默认值，但增加每个列字段的非空验证选项（针对字段的int类型也会验证）。

 **3、** 对所有控件中name和title区分出来，其中name主要用来后续表单存储结果中作为key，title用来后续表单验证中进行提示使用。

 **4、** select,radios,checkbox控件中选项数据均通过配置url从后台获取数据显示。


### 各个控件编辑图如下：


 **text：** 

![输入图片说明](https://gitee.com/uploads/images/2018/0126/141009_14f35c3a_146738.jpeg "text.jpg")

 **textarea:** 

![输入图片说明](https://gitee.com/uploads/images/2018/0126/141023_f160e981_146738.jpeg "textarea.jpg")

 **radio:** 

 ![输入图片说明](https://gitee.com/uploads/images/2018/0201/173108_e845352a_146738.png "radios.png")

 **checkboxs:** 

 ![输入图片说明](https://gitee.com/uploads/images/2018/0201/173122_6089c0d9_146738.jpeg "checkboxs.jpg")

 **select:** 

![输入图片说明](https://gitee.com/uploads/images/2018/0126/141115_340a917d_146738.jpeg "select.jpg")

 **datepicker:** 

![输入图片说明](https://gitee.com/uploads/images/2018/0126/141140_813d8f66_146738.jpeg "datepicker.jpg")

 **listctrl** 

![输入图片说明](https://gitee.com/uploads/images/2018/0126/141157_61581f58_146738.jpeg "listctrl.jpg")



 **最后来几张示例项目的全图：** 

![输入图片说明](https://gitee.com/uploads/images/2018/0126/141234_6cee8ff6_146738.jpeg "form_list.jpg")

![输入图片说明](https://gitee.com/uploads/images/2018/0126/141254_7615b250_146738.jpeg "entry_list.jpg")



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)