
EasyPoi Excel和 Word简易工具类
===========================

 easypoi功能如同名字easy,主打的功能就是容易,让一个没见接触过poi的人员
就可以方便的写出Excel导出,Excel模板导出,Excel导入,Word模板导出,通过简单的注解和模板
语言(熟悉的表达式语法),完成以前复杂的写法

	官网： http://www.afterturn.cn/
	邮箱： qrb.jueyue@foxmail.com
	QQ群:  1群 364192721(满) 2 群116844390
	
	开发者:魔幻之翼 xf.key@163.com
Spring Boot 支持    https://gitee.com/lemur/easypoi-spring-boot-starter

[官网](http://www.afterturn.cn/)

[VIP技术服务](https://lemur.taobao.com)

    提供一年的技术支持服务
    提供10次内的1V1服务,限1小时
    提供升级指导
    针对lemur提供的所有开源项目提供支持服务

**开发指南**

**[http://www.afterturn.cn/doc/easypoi.html](http://www.afterturn.cn/doc/easypoi.html)**



[用户征集](https://gitee.com/lemur/easypoi/issues/IFDX7)

版本介绍

[history.md](https://gitee.com/lemur/easypoi/blob/master/history.md)

基础示例

[basedemo.md](https://gitee.com/lemur/easypoi/blob/master/basedemo.md)

[测试项目](http://git.oschina.net/lemur/easypoi-test): http://git.oschina.net/lemur/easypoi-test

**!!! 3.0 版本开始全新包名和GROUPID cn.afterturn**

---------------------------
EasyPoi的主要特点
--------------------------
	1.设计精巧,使用简单
	2.接口丰富,扩展简单
	3.默认值多,write less do more
	4.AbstractView 支持,web导出可以简单明了

---------------------------
EasyPoi的几个入口工具类
---------------------------

	1.ExcelExportUtil Excel导出(
	普通导出,模板导出)
	2.ExcelImportUtil Excel导入
	3.WordExportUtil Word导出(只支持docx ,doc版本poi存在图片的bug,暂不支持)
	
---------------------------
关于Excel导出XLS和XLSX区别
---------------------------

	1.导出时间XLS比XLSX快2-3倍
	2.导出大小XLS是XLSX的2-3倍或者更多
	3.导出需要综合网速和本地速度做考虑^~^
	
---------------------------
几个工程的说明
---------------------------
	1.easypoi 父包--作用大家都懂得
	2.easypoi-annotation 基础注解包,作用与实体对象上,拆分后方便maven多工程的依赖管理
	3.easypoi-base 导入导出的工具包,可以完成Excel导出,导入,Word的导出,Excel的导出功能
	4.easypoi-web  耦合了spring-mvc 基于AbstractView,极大的简化spring-mvc下的导出功能
	5.sax 导入使用xercesImpl这个包(这个包可能造成奇怪的问题哈),word导出使用poi-scratchpad,都作为可选包了
--------------------------
maven 
--------------------------
maven库应该都可以了
SNAPSHOT 版本-很少发布
https://oss.sonatype.org/content/groups/public/
```xml
		  
			 cn.afterturn 
			 easypoi-base 
			 3.1.0 
		 
		 
			 cn.afterturn 
			 easypoi-web 
			 3.1.0 
		 
		 
			 cn.afterturn 
			 easypoi-annotation 
			 3.1.0 
		 
```
	

--------------------------
pom说明
--------------------------
word和sax读取的时候才使用,就不是必须的了,请手动引用,JSR303的校验也是可选的,PDF的jar也是可选的
```xml
			 
			 
				 xerces 
				 xercesImpl 
				 ${xerces.version} 
				 true 
			 
			 
				 org.apache.poi 
				 poi-scratchpad 
				 ${poi.version} 
				 true 
			 
			
			 
             
                 org.apache.poi 
                 ooxml-schemas 
                 1.3 
                 true 
             
			
			 
			 
				 org.hibernate 
				 hibernate-validator 
				 5.1.3.Final 
				 true 
			 
			
			 
				 org.apache.bval 
				 org.apache.bval.bundle 
				 1.1.0 
			 
			
			 
			 
				 com.itextpdf 
				 itextpdf 
				 5.5.6 
				 true 
			 

			 
				 com.itextpdf 
				 itext-asian 
				 5.2.0 
				 true 
			 
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)