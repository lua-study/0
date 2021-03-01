Spiderman - Java开源Web数据抽取工具
========================================
    Spiderman 是一个Java开源Web数据抽取工具。它能够收集指定的Web页面并从这些页面中提取有用的数据。
    Spiderman主要是运用了像XPath,正则表达式等这些技术来实数据抽取。
    
它包含了两部分（二者缺一不可）：
-----------------------------
	* spiderman-core 内核
	* spiderman-plugin 插件

主要特点
----------------------
    * 微内核+插件式架构、灵活、可扩展性强
    * 无需编写程序代码即可完成数据抽取
    * 多线程保证性能

怎么使用？
----------
* 首先，确定好你的目标网站以及目标网页（即某一类你想要获取数据的网页，例如网易新闻的新闻页面）
* 然后，打开目标页面，分析页面的HTML结构，得到你想要数据的XPath，具体XPath怎么获取请看下文。
* 最后，在一个xml配置文件里填写好参数，运行Spiderman吧！

XPath获取技巧？
--------------
* 首先，下载xpathonclick插件，[猛击这里](https://chrome.google.com/webstore/search/xpathonclick)
* 安装完毕之后，打开Chrome浏览器，可以看到右上角有个“X Path” 图标。
* 在浏览器打开你的目标网页，然后点击右上角的那个图片，然后点击网标上你想要获取XPath的地方，例如某个标题
* 这时候按住F12打开JS控制台，拖到底部，可以看到一串XPath内容
* 记住，这个内容不是绝对OK的，你可能还需要做些修改，因此，你最好还是去学习下XPath语法
* 学习XPath语法的地方：[猛击这里](http://www.w3school.com.cn/xpath/index.asp)

Spiderman Sample | 案例
=======================

* 首先保证你的机器至少可以运行Java程序、也可以执行Maven命令
* 案例程序[spiderman-sample] mvn test
* Spiderman程序将会运行N秒钟，然后到保存抓取数据的文件夹查看对应网站的数据
* 这里有篇文章介绍示例：[http://my.oschina.net/laiweiwei/blog/100866]

这是使用Spiderman的代码：
    
    public class TestSpider {
        
    	private final Object mutex = new Object();
    	
    	@Test
    	public void test() throws Exception {
    		String err = EWeb4JConfig.start();
			if (err != null)
				throw new Exception(err);
			
			SpiderListener listener = new SpiderListenerAdaptor(){
				public void afterScheduleCancel(){
					//调度结束回调
				}
				/**
				 * 每次调度执行前回调此方法
				 * @date 2013-4-1 下午03:33:11
				 * @param theLastTimeScheduledAt 上一次调度时间
				 */
				public void beforeEveryScheduleExecute(Date theLastTimeScheduledAt){
					System.err.print("[SPIDERMAN] "+CommonUtil.getNowTime("HH:mm:ss")+" [LAST_SCHEDULE_AT] ~ ");
					System.err.println("at -> " + CommonUtil.formatTime(theLastTimeScheduledAt));
				}
				public void onFetch(Thread thread, Task task, FetchResult result) {
					System.out.print("[SPIDERMAN] "+CommonUtil.getNowTime("HH:mm:ss")+" [FETCH] ~ ");
					System.out.println("fetch result ->" + result + " from -> " + task.sourceUrl);
				}
				public void onNewUrls(Thread thread, Task task, Collection  newUrls) {
					System.out.print("[SPIDERMAN] "+CommonUtil.getNowTime("HH:mm:ss")+" [DIG] ~ ");
					System.out.println(newUrls);
				}
				public void onDupRemoval(Thread currentThread, Task task, Collection  validTasks) {
	//				for (Task t : validTasks){
	//					System.out.print("[SPIDERMAN] "+CommonUtil.getNowTime("HH:mm:ss")+" [DUPREMOVE] ~ ");
	//					System.out.println(t.url+" from->"+t.sourceUrl);
	//				}
				}
				public void onTaskSort(Thread currentThread, Task task, Collection  afterSortTasks) {
	//				for (Task t : afterSortTasks){
	//					System.out.print("[SPIDERMAN] "+CommonUtil.getNowTime("HH:mm:ss")+" [SORT] ~ ");
	//					System.out.println(t.url+" from->"+t.sourceUrl);
	//				}
				}
				public void onNewTasks(Thread thread, Task task, Collection  newTasks) {
	//				for (Task t : newTasks){
	//					System.out.print("[SPIDERMAN] "+CommonUtil.getNowTime("HH:mm:ss")+" [NEWTASK] ~ ");
	//					System.out.println(t.sort + ",,,," + t.url+" from->"+t.sourceUrl);
	//				}
				}
				public void onTargetPage(Thread thread, Task task, Page page) {
	//				System.out.print("[SPIDERMAN] "+CommonUtil.getNowTime("HH:mm:ss")+" [TARGET] ~ ");
	//				System.out.println(page.getUrl());
				}
				public void onInfo(Thread thread, Task task, String info) {
					System.out.print("[SPIDERMAN] "+CommonUtil.getNowTime("HH:mm:ss")+" [INFO] ~ ");
					System.out.println(info);
				}
				
				public void onError(Thread thread, Task task, String err, Throwable e) {
					System.err.print("[SPIDERMAN] "+CommonUtil.getNowTime("HH:mm:ss")+" [ERROR] ~ ");
					e.printStackTrace();
				}
				
				public void onParse(Thread thread, Task task, List > models) {
					final String projectRoot = FileUtil.getTopClassPath(TestSpider.class);
					final File dir = new File(projectRoot+"/Data/"+task.site.getName()+"/"+task.target.getName());
					try {
						if (!dir.exists())
							dir.mkdirs();
						
						for (int i = 0; i   map = models.get(i);
							String fileName = dir + "/count_" + task.site.counter.getCount() + i;
							StringBuilder sb = new StringBuilder();
							for (Iterator > it = map.entrySet().iterator(); it.hasNext();){
								Entry  e = it.next();
								boolean isBlank = false;
								
								if (e.getValue() == null)
									isBlank = true;
								else if (e.getValue() instanceof String && ((String)e.getValue()).trim().length() == 0)
									isBlank = true;
								else if (e.getValue() instanceof List && ((ArrayList )e.getValue()).isEmpty())
									isBlank = true;
								else if (e.getValue() instanceof List && !((ArrayList )e.getValue()).isEmpty()) {
									if (((ArrayList )e.getValue()).size() == 1 && String.valueOf(((ArrayList )e.getValue()).get(0)).trim().length() == 0)
									isBlank = true;
								}
									
								if (isBlank){
									if (sb.length() > 0)
										sb.append("_");
									sb.append(e.getKey());
								}
							}
							String content = CommonUtil.toJson(map);
							if (sb.length() > 0)
								fileName = fileName + "_no_"+sb.toString()+"_";
							
							File file = new File(fileName+".json");
							FileUtil.writeFile(file, content);
							System.out.print("[SPIDERMAN] "+CommonUtil.getNowTime("HH:mm:ss")+" [INFO] ~ ");
							System.out.println(fileName + " create finished...");
						}
					} catch (Exception e) {
						e.printStackTrace();
					}
				}
			};
		
			//启动爬虫
			Spiderman.me()
				.init(listener)//初始化
				.startup()//启动
				.keepStrict("2h");//存活时间，过了存活时间后马上关闭
			
			//启动爬虫 + 调度定时重启
			//Spiderman.me()
				//.listen(listener)//设置监听器
				//.schedule("10s")//调度，爬虫运行10s
				//.delay("2s")//每隔 10 + 2 秒后重启爬虫
				//.times(3)//调度 3 次
				//.startup()//启动
				//.blocking();//阻塞直到所有调度完成
    	}
    }


下面详细看看这个sample的配置文件：

首先有一个初始化配置文件spiderman.properties，它就放在#{ClassPath}目录下
 
    #网站配置文件放置目录
    website.xml.folder=#{ClassPath}/WebSites
    #网站已访问url数据库存储目录
    website.visited.folder=#{ClassPath}/dbEnv
    #http抓取失败重试次数
    http.fetch.retry=3
    #http连接超时，支持单位 s秒 m分 h时 d天，不写单位则表示s秒
    http.fetch.timeout=5s

然后在#{ClassPath}/WebSites目录下有一份oschina.xml

     
	 
	 
		 
		 
			 
			 
				 
			 
			 
			 
				 
				 
			 
			 
				 
			 -->
			 
				 
			 -->
			 
			 
				 
				 
			 
			 
			 
				 
				 
					 
						  节点是一样的结构，只不过名称不叫model而是叫做digUrls而已
						-->
						 
							 
								 
									 
									 
								 
							 
							  
								 
									 
								 
							 
						 
					 
				 
				 
				 
					 
					 
						 
					 
					 
					 
						 
							 
						 
						-->
						 
						 
							 
								 
								  | regex:当使用XPath（包括attribute）规则获取到的文本内容不满足需求时，可以继续设置regex正则表达式进行解析
								  | exp:当使用XPath获取的文本(如果获取的不是文本则会先执行exp而不是regex否则先执行regex)不满足需求时，可以继续这是exp表达式进行解析
								  |     exp表达式有几个内置对象和方法:
								  |     $output(Node): 这个是内置的output函数，作用是输出某个XML节点的结构内容。参数是一个XML节点对象，可以通过XPath获得
								  |     $this: 当使用XPath获取到的是Node节点时，这个表示节点对象，否则表示Java的字符串对象,可以调用Java字符串API进行处理
								  |     $Tags: 这个是内置的用于过滤标签的工具类 
								  |            $Tags.xml($output($this)).rm('p').ok()
								  |            $Tags.xml($this).rm('p').empty().ok()
								  |     $Attrs: 这个是内置的用于过滤属性的工具类
								  |            $Attrs.xml($this).rm('style').ok()
								  |            $Attrs.xml($this).tag('img').rm('src').ok()
								  |     
								  |            $Tags和$Attrs可以一起使用: 
								  |            $Tags.xml($this).rm('p').Attrs().rm('style').ok()
								  |            $Attrs.xml($this).rm('style').Tags().rm('p').ok()
								  | skipErr:0|1 是否忽略错误消息
								  | skipRgxFail:0|1 是否忽略正则匹配失败，如果是，则会取失败前的值
								-->
								 
							 
						 
						 
							 
								 
								 
								 
								 
								 
								 
								 
								 
							 
						 
						 
							 
								 
							 
						 
						 
							 
								 
							 
						 
						 
							 
								 
							 
						 
					 
				 
			 
			 
			 
				 
				 
					 
					 
						 
						 
							 
							 
						 
						 
							 
						 
						 
							 
						 
						 
							 
						 
						 
							 
						 
						 
							 
						 
						 
							 
						 
						 
							 
						 
						 
							 
						 
						 
							 
						 
					 
					 
						 
							 
								 
							 
						 
					 
				 
			 
		 
	 
----

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)