
===========================
HPT-Search 基于Lucene的轻量级分布式搜索引擎
===========================
---------------------------
功能
---------------------------
    整合好了lucene,分词器 不需要麻烦的配置,开箱即用

     1.提供面向对象的Lucene-API
        用注解定义实体（包括字段是否创建索引,字段的权值,是否用于检索,是否高亮 等）
        用hpt-search的服务接口操作实体,来实现索引的添加,修改,删除,检索

     2.支持高亮功能

     3.简化Lucene分页

     4.支持分组统计功能

     5.Lucene集群
        支持 1-master n-slave （一主多从） 结构同步索引
        集群节点状态管理界面

---------------------------
使用说明
---------------------------

```Java
-----------
引入包和配置文件
-----------
//Jar包:
//1.hpt-search.jar //release目录下找
//或者使用oschina的第三方maven库 参考http://maven.oschina.net/help.html

 
   com.hpt 
   search 
   1.0.1 
   pom 
 

//2.IKAnalyzer2012_hf.jar (libs目录下,IK分词)
//3.lucene4.3的Jar包 参考项目中pom.xml的引用

//配置文件:
search.properties

//lucene-local-impl: com.hpt.search.service.impl.LuceneSearchServiceImpl
//lucene-cluster-impl: com.hpt.search.service.impl.LuceneClusterServiceImpl
//选择使用单机/集群模式的搜索引擎类
searcher=com.hpt.search.service.impl.LuceneClusterServiceImpl
//是否打开高亮 on|off
highlight=on
highlight.pre= 
highlight.ext= 
//索引存放目录
lucene.indexDir=H:/tmp/search/test
```

```Java
-----------
实体定义
-----------
@SearchEntity(searchFields={"author","content","type"},idFiled="name")
public class SearchTestEntity {

	@SearchColum(name="author", index = true, store = true)
	private String author;

	@SearchColum(index =true, store = true,highLight = true)
	private String content;

	@SearchColum(index =true,name="name", store = true)
	private String name;

    @SearchColum(index =true,name="type", store = true)
    private String type;
-----------
单元测试
-----------
public class SearchTest {
    //初始化搜索引擎
	private SearchService service = HptSearcher.getService();

	/**
	 * 创建索引 配置文件：resources/search.properties -indexDir:索引文件存放磁盘路径
     * 其中 name 字段作为索引的 逻辑唯一表示位（主键）
	 */
	@Test
	public void create() {
        List  books = new ArrayList (10);
        SearchTestEntity s1 = new SearchTestEntity("小说","罗贯中","本书是中国古典四大名著之一，全名为《三国志通俗演义》。作者是元末明初小说家罗贯中，是中国第一部长篇章回体历史演义小说。描写了从东汉末年到西晋初年之间近105年的历史风云。全书反映了三国时代的政治军事斗争，反映了三国时代各类社会矛盾的转化，并概括了这一时代的历史巨变，塑造了一批叱咤风云的三国英雄人物。\n" +
                "自《三国演义》问世以来，各式各样的版样层出不穷，明代刻本有20多种，清代刻本也有70多种，在中国民间流传甚广。康熙二十八年，日僧湖南文山编译出版日文本《通俗三国志》之后，朝鲜、日本、印度尼西亚、越南、泰国、英国、法国、俄国等许多国家都对《三国演义》有本国文字的译本，并发表了不少研究论文和专著，对这部小说作出了极高的评价。","三国演义");
        SearchTestEntity s2 = new SearchTestEntity("哲学","王阳明","本书是哲学著作，作者是中国明代哲学家、宋明道学中心学一派的代表人物王守仁（字伯安），世称阳明先生。此书记载了他的语录和论学书信。传习一辞源出自《论语》中的传不习乎一语。","传习录");
        SearchTestEntity s3 = new SearchTestEntity("小说","石悦","明朝那些事儿，本书是网络连载的历史小说，作者是当年明月，本名石悦，广东顺德海关公务员。[2] 2006年3月在天涯社区首次发表，2009年3月21日连载完毕，边写作边集结成书出版发行，一共7本[3] 。","明朝那些事儿");
        SearchTestEntity s4 = new SearchTestEntity("传记","陈梧桐","本书是一部人物传记，运用了丰富扎实的史料，生动流畅的文笔，全面记述了中国历史上的杰出政治家和军事家明太祖朱元璋从贫苦出身的小行童到元末农民起义领袖，再到明朝开国皇帝的传奇经历和主要活动，是一部具有重要学术价值和较强可读性的历史著作。","洪武大帝朱元璋传");
        SearchTestEntity s5 = new SearchTestEntity("未知","佚名","本书是一部","不知道");
        books.add(s1);
        books.add(s2);
        books.add(s3);
        books.add(s4);
        books.add(s5);
        try {
            service.createOrUpdateIndexBatch(books);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }

	/**
	 * 关键字搜索-无分页 关键字搜索支持lucene语法
	 */
	@Test
	public void search() {
		try {
			SearchResult  r = service.findSearchResult(
					com.hpt.junit.SearchTestEntity.class, "明朝");
			System.out.println(r.getSize());
			for(SearchTestEntity t:r.getResult()){
				System.out.println(t);
			}
		} catch (CorruptIndexException e) {
			e.printStackTrace();
		} catch (IOException e) {
			e.printStackTrace();
		} catch (ParseException e) {
			e.printStackTrace();
		} catch (Exception e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
	}

	/**
	 * 关键字搜索-分页 关键字搜索支持lucene语法
	 */
	@Test
	public void searchPage() {
		try {
			SearchResult  r = service.findSearchResult(
					com.hpt.junit.SearchTestEntity.class, "明朝", 1, 1);
			System.out.println(r.getSize());
			for(SearchTestEntity t:r.getResult()){
				System.out.println(t);
			}
		} catch (CorruptIndexException e) {
			e.printStackTrace();
		} catch (IOException e) {
			e.printStackTrace();
		} catch (ParseException e) {
			e.printStackTrace();
		} catch (Exception e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
	}

    /**
     * 分组统计
     * 按照书的类型 统计数量和书名
     */
    @Test
    public void group(){
        try {
           GroupResult groupResult = service.group(SearchTestEntity.class, "本书", "type", "name", 10000);
           System.out.println( groupResult.getCountMap());
           //输出结果：{传记=1, 哲学=1, 小说=2, 未知=1}
        } catch (Exception e) {
            e.printStackTrace();
        }
    }

	/**
	 * 索引更新
	 */
	@Test
	public void update() {
        SearchTestEntity s5 = new SearchTestEntity("小说","佚名","本书是一部小说","围城");
		try {
			service.createOrUpdateIndex(s5);
		} catch (Exception e) {
			e.printStackTrace();
		}
		search();
	}

	/**
	 * 索引删除
	 */
	@Test
	public void del() {
        SearchTestEntity s5 = new SearchTestEntity();
        s5.setName("围城");
		try {
			service.deleteIndex(s5);
		} catch (Exception e) {
			e.printStackTrace();
		}
		search();
	}

}
```

---------------------------
集群模式配置-索引复制
---------------------------

web.xml 增加集群Servlet配置
```Xml

     
		 hptSearch 
		 com.hpt.search.cluster.ClusterServlet 
		 1 
	 
	 
		 hptSearch 
		 /manager 
	 
```

修改配置文件 search.properties
```Java

//修改实现类为集群模式
searcher=com.hpt.search.service.impl.LuceneClusterServiceImpl

//集群配置
//主节点master,从节点slave
lucene.cluster.mode=master

//集群模式下的同步日志路径
lucene.cluster.logbase=H:/tmp/search/node1/log

//本机IP+端口(将以此端口作为节点间通讯端口)
lucene.cluster.me=127.0.0.1:9990
//节点配置(多个节点用逗号分隔,从节点留空即可)
lucene.cluster.group=127.0.0.1:9991
//日志发布的时间间隔 (毫秒)
lucene.cluster.period.pub=60000
//日志重做的时间间隔 (毫秒)
lucene.cluster.period.redo=60000
//心跳检测的时间间隔 (毫秒)
lucene.cluster.period.heartbeat=60000
//错误重试的时间间隔 (毫秒)
lucene.cluster.period.pubFromError=60000
```

在master部署后可查看集群节点的状态 http://localhost:8080/hpt-search/manager?page=index \ 
![](http://chuantu.biz/t2/9/1432365041x-1376440086.jpg)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)