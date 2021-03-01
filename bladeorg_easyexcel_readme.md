#easyExcel

## 关于

由于在项目中用了excel作报表导出，java操作excel基本上用的是poi,但是poi操作起来还是挺烦的，需要创建很多的row，cell以及样式，为了简便这种操作，便有了该项目，该项目实现了列表数据的导入，分页列表导出，支持自定义格式，支持模版以及模板和列表的混合导出。欢迎大家学习讨论，以提出你宝贵的建议和意见。


##版本号：0.1


##更新说明


注解类：

	Excel注解类，此注解类用于类上面，定义了读写excel所需要的属性，属性：
	
		beginRow：读写的开始行，不写默认第一行开始
		
		isNeedSequence：生成时是否生成序号列，默认生成
		
		dataHeader：生成时列头名称以及对就的列以及列的宽度，格式为:  字段名:哪一列:列宽,格式为,字段名:哪一列:列宽...
					可以写成：  字段名,字段名...或字段名:哪一列,格式为,字段名:哪一列...  注意省略值为默认
		
		outFilePath：生成路径
		
		inFilePath：读取路径
		
		autoHeight:是否自适应高度,默认不自适应
		
		createRowWay：创建行的方式，二个取值add,insert。add新增一行，insert插入一行，默认新增
	
	Sheet注解类，此类用于类上，定义相关sheet属性，属性：
	
		sheetName：生成时sheet的名称
		
		sheetNum：读写时确认哪一个sheet,默认第一个
		
		sheetSize：分面的数据量，在页多少条，默认不分页
		
	Cell注解类，此类用于字段上，确认字段和cell的匹配，属性：
	
		rowNum：哪一行
		
		columnNum：哪一列，支持大小写字母以及数字
		
		name:标签名称，当字段和标签名不一致时使用
		
	Ingore注解类，此类用于字段上，标识字段是否需要读写操作
	
功能以及用法：

	1.读取列表数据：
	
		例子请看代码测试，路径： EASYEXCEL\test\com\easyexcel\readlisttest，注意文件路径
		
			代码片段：
			类：
			@Excel(beginRow=2,inFilePath="d:\\students.xlsx")
			public class Students {
				@Cell(columnNum="2")
				private String name;
				@Cell(columnNum="c")//or@Cell(whichCell="C")
				private int age;
			}
			使用：
			ReadExcel  re = new ReadListExcel<>();
			Map  param = new HashMap ();
			List  list = re.read(param,Students.class);
			
	2.读取模版数据	
	
		a.用标签读取模版数据，例子请看代码测试，路径： EASYEXCEL\test\com\easyexcel\readmodeloflabletest，注意文件路径
		
			代码片段：
			类：
			public class Students {
				private String name;
				private int age;
			}
			使用：
			ReadExcel  re = new ReadModelExcel<>();
			Map  param = new HashMap ();
			param.put("inFilePath","d:\\studentsModel.xlsx");
			List  list = re.read(param,Students.class);
		
		b.用注解读取模版数据，例子请看代码测试，路径： EASYEXCEL\test\com\easyexcel\readmodelofannotationtest，注意文件路径
		
			代码片段：
			类：
			@Excel(inFilePath="d:\\studentsModelann.xlsx")
			public class Students {
				@Cell(rowNum = 5,columnNum="b")
				private String name;
				@Cell(rowNum = 2,columnNum="c")//or@Cell(columnNum="C")
				private int age;
			}
			使用：
			ReadExcel  re = new ReadModelExcel<>();
			List  list = re.read(null,Students.class);
			
		注意事项目：	
			读取excel传参说明：
				inFilePath：读取路径,可以用注解，如果传，则以传入为主
				beginRow：开始行，可以用注解，如果传，以传入为主
		
	3.写入列表数据：
		
		a.一个是通用的实现，例子请看代码测试，码路径：EASYEXCEL\test\com\easyexcel\writelistTest 方法为：testCommon
			
			代码片段：
			类：
			@Excel(beginRow=1,dataHeader="姓名:1,年龄:3,成绩:4",outFilePath="d:\\test.xls")
			@Sheet(/*sheetSize=2000,*/sheetName="测试")
			public class Students {
				@Cell(columnNum="1")
				private String name;
				@Cell(columnNum="c")
				private int age;
				@Cell(columnNum="4")
				private double grade;
			}
			使用：
			WriteExcel  we = new WriteListExcel ();
			Map  param = new HashMap ();
			List  list = new ArrayList ();
				for(int i=1;i  weh = new WriteListExcelHelp (cellStyle);
				Map  param = new HashMap ();
				List  list = new ArrayList ();
				for(int i=1;i  we = new WriteModelExcel<>();
			Map  param = new HashMap<>();
			param.put("inFilePath", "d:\\model.xlsx");//读取文件的目录必须有，可以传也可以用注解配,如果传以传为主
			param.put("outFilePath", "d:\\outmodel.xlsx");//生成路径必须有，可以传也可以用注解配,如果传以传为主
			List  list = new ArrayList ();
			list.add(new Students("张三",25));
			we.write(param, list);
		b.用注解来定位cell,即在类字段上用注解表时位置，如果有注解，以注解实现，例子请看代码测试，路径：EASYEXCEL\test\com\easyexcel\writemodelofannotationtest，注意文件路径
			
			代码片段：
			类：
			@Excel(inFilePath="d:\\modelann.xlsx",outFilePath="d:\\outmodelann.xlsx")
			@Sheet(sheetNum=1)
			public class Students {
				@Cell(rowNum=1,columnNum="b")
				private String name;
				@Cell(rowNum=3,columnNum="b")
				private int age;
				@Ingroe
				private double grade;
			}
			使用：
			WriteExcel  we = new WriteModelExcel<>();
			Map  param = new HashMap<>();
			List  list = new ArrayList ();
			list.add(new Students("张三",25));
			we.write(param, list);
			
	

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)