# MD2File

## MD2File可以干嘛？

能将markdown语法的文档内容，导出为word，pdf，HTML等的文件。

之所以使用markdown，是因为markdown比较好解析，而且md文本的内容会比较规范。另外，html转md也是比较好处理的。

目前MD2File支持大部分markdown的基本语法（**支持表格语法**）。无序列表和有序列表暂时还不支持多级列表。

导出的word文档，在微软的office word中格式是最好的，毕竟poi开发的时候，也是以支持ms word为主。在wps中也还不错。在pages中内容排版基本正常，部分样式不支持。导出的pdf文档，相对于word文档，会美观很多。

## 顺便开发的功能：支持markdown转HTML文本

既然MD2File都能支持导出HTML文件了，支持markdown转HTML文本也就是几秒钟的事。

新增了MDUtil类，就是支持此功能的。现在java方面支持markdown转html还没有个比较好的jar，或多或少都有缺陷。当然目前MD2File也有，但会慢慢完善的，这也是作者的承诺。

##简单例子
	@Test
	public void test(){
		try {
			// 导出文本
			FileFactory.produce(new File("test_file/md_for_test.md"), "test_file/test.docx");
			FileFactory.produce(new File("test_file/md_for_test.md"), "test_file/test.pdf");
			FileFactory.produce(new File("test_file/md_for_test.md"), "test_file/test.html");
		} catch (FileNotFoundException e) {
			e.printStackTrace();
		}
		//markdown转html
		System.out.println(MDUtil.markdown2Html("[**开源中国**](http://www.oschina.net)社区，是一个很不错的网站。欢迎上去查找开源软件，吐吐槽！"));
	}

## 怎么获取MD2File这个开源工具？

代码已经放到：[https://git.oschina.net/cevin15/MD2File](https://git.oschina.net/cevin15/MD2File)

有兴趣的可以star一下，想使用的可以fork一下。

## 关于MD2File的一点说明

使用很简单，用`FileFactory`提供的方法即可。导出word依赖于poi，pdf依赖于itext，html无其他依赖，通过pom.xml文件可以清楚看到。

如果觉得默认的样式不符合自己的要求，可以fork项目之后，通过修改`*Decorator`这个类来实现。

为方便大家下载直接使用，在lib中上传了MD2File的jar包，以及依赖包。

PS.如果你只是需要markdown转HTML的功能，可以看[这里](https://github.com/cevin15/MDTool)。

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)