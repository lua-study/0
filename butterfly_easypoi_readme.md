===========================
EasyPoi Excel和 Word简易工具类
===========================
 easypoi功能如同名字easy,主打的功能就是容易,让一个没见接触过poi的人员
就可以方便的写出Excel导出,Excel模板导出,Excel导入,Word模板导出,通过简单的注解和模板
语言(熟悉的表达式语法),完成以前复杂的写法

	作者博客：http://blog.afterturn.cn/
	作者邮箱： qrb.jueyue@gmail.com
	QQ群:  364192721
	
	开发者:魔幻之翼 xf.key@163.com

**开发指南**

**[http://easypoi.mydoc.io](http://easypoi.mydoc.io)**

[开发文档请查看DOC下面的EasyPoi教程](http://git.oschina.net/jueyue/easypoi/blob/master/doc/EasyPoi%E6%95%99%E7%A8%8B.docx?dir=0&filepath=doc%2FEasyPoi%E6%95%99%E7%A8%8B.docx&oid=133ebde5641f128420023dbdc2533ab4b53c7792&sha=4c8d94c80544811e2e358518bad6c689a63c13e9)
!!!2.1.6 版本开始和之前的版本校验不兼用,使用JSR303的校验,删除了之前的注解,请注意
!!! 2.3.0 模板导出有问题,请使用2.3.0.1修复版本


版本介绍
history.md

基础示例
basedemo.md

[测试项目](http://git.oschina.net/jueyue/easypoi-test): http://git.oschina.net/jueyue/easypoi-test

**!!! 3.0.1 版本开始全新包名和GROUPID cn.afterturn**

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
SNAPSHOT 版本
https://oss.sonatype.org/content/groups/public/
```xml
		  
			 cn.afterturn 
			 easypoi-base 
			 3.0.1-SNAPSHOT 
		 
		 
			 cn.afterturn 
			 easypoi-web 
			 3.0.1-SNAPSHOT 
		 
		 
			 cn.afterturn 
			 easypoi-annotation 
			 3.0.1-SNAPSHOT 
		 
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