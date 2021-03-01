# CISE
# 基于内容的图片搜索引擎(Content-based Image Search Engine)


	本引擎旨在实现成一个图片搜索引擎控件，可供其他有需要的系统使用
	使用本引擎只需要少量的配置以及简单的启动代码，便能启动


## 所需配置
	

	* 项目根目录（由于考虑到使用本引擎的系统可能是普通的 Java 项目也有可能是 Web 项目，因此暂时没有去考虑如何区分获取项目根目录，暂用配置来解决问题）
	* 图片库目录
	* 每个搜索器返回的结果数目，默认为10
	* 线程池最大线程数，默认为50
	* 图片特征提取算法的配置，如果搜索图片时希望对某个特征进行搜索，则将对应的算法配置为 true ，否则为 false
	* 并行搜索器排序算法的配置，在排序算法中选择一种以供排序时使用，将选定的排序算法设置为 true


## 启动代码


### 启动索引


	  public class IndexerDemo {

	  	public static void main(String[] args) {
			/*
			 * 若要对现有的整个图片库进行索引，则在配置文件中配置图片库地址
			 * 然后直接调用 Indexer.start() 方法，进行索引
			 * */
			Indexer.start();
			/*
			 * 若图片库中的部分图片已生成索引了，现需对其他图片进行索引
			 * 则调用 Indexer.start(sufPath) 方法
			 * 参数为基于已配置的图片库地址的后缀地址
			 * 如要进行索引的目录为 C:\pictures\test ,配置的图片库地址为 C:\pictures\
			 * 则 sufPath = "test";
			 * 此方法是为了满足图片库逐日增加图片的需求
			 * 如项目的图片库是由爬虫所得，爬虫每日都进行爬取，则可将后缀地址设置为日期
			 * 如2015年7月16日爬取了部分图片，则需对 C:\pictures\20150716 目录下的图片进行索引
			 * 此时只需调用 Indexer.start("20150716");
			 * */
			// Indener.start("20150716");
	  	}

	  }

### 启动搜索


	  public class SearcherDemo {

	  	public static void main(String[] args) {
			// 输入文件，即要进行搜索的图片文件
			File file = new File("");
			SearchServiceImpl searchServiceImpl = new SearchServiceImpl(file);
			ArrayList  results = searchServiceImpl.search();
	  	}

	 }


## 引用 CISE


	要在自己的项目中引用 CISE ，只需将 required-jar 目录中的 jar 包加入项目的 build-path ，然后将 
	algorithmConfig.properties、baseConfig.properties、sortConfig.properties 三个配置文件放在 src 目录下即可
	三个配置文件的配置信息参照以上说明

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)