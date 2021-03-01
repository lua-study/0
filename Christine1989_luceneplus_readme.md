# lucenex
基于JDK 1.8 & lucene 7.x 的搜索框架、在不影响原本性能的同时、提升80%的开发效率、降低70%的开发难度！！！
# 文档
### javadoc：https://apidoc.gitee.com/Myzhang/luceneplus
### 轻松入门：https://gitee.com/Myzhang/luceneplus/blob/master/README.md
### 入门实例：https://gitee.com/Myzhang/luceneplus/tree/master/src/test/java/com/ld/lucenex/demo
# 更新日志
### v1.3
* 增加单个对象添加索引 
* 同步实时索引 
### v1.2
* 增加jfinal、springboot、servlet等集成插件 
* 精简代码 
* 增加两个实用方法 
* 删除2个依赖 
* 适配 javabean and map and fastjson 直接添加 
* 自动提交&关闭数据、避免丢失数据或手动提交 
### v1.1
* 补充大量文档注释 
* 精简&优化代码 
* 修复一个错误的Demo 
### v1.0
* 去除第三方分词依赖&无用的Jar 
* 使用cglib 动态代理创建 Service 
* 新增拦截器 
* 添加更新 默认异步

# 亮点
* 轻 ~ 不足千行
* 简 ~ 零配置项
* 全 ~ 内置丰富
* 易 ~ 入门简单
* 快 ~ 接近原生
* 稳 ~ 坚如磐石
* 展 ~ 插件扩展

# 特点
* 原声Lucene 用法
* 注解式声明字段
* 多库自动切换
* 自动管理资源创建于释放
* 自动高性能近实时索引
* 可持续扩展的Service 接口设计
* 内置常用的 增删改查
* 可直接添加Java对象与Map集合 无需手动创建 Document
* 支持操作回退
* 可自定义分词器
* 默认异步提交和更新
# 社区
* QQ群号:475349334
# 安装
### maven
```
 
   com.github.zhangxianweihebei 
   lucenex 
   1.1 
 
```
# 用法
### 1、继承 LuceneXConfig
```
public class DemoConfig extends LuceneXConfig{
	@Override
	public void configConstant(Constants me) {
	}
	@Override
	public void configLuceneX(BaseConfig me) {
		// 存储目录 、名称、高亮、分词器、存储类
		me.add("d:/", "test",  false, new PerFieldAnalyzerWrapper(new StandardAnalyzer()), Empty.class);
	}
}
```
### 2、获取Service
```
//默认使用第一个存储库（如果您只有一个库或使用第一个库的话）
BasisService basisService = LdService.newInstance(BasisService.class);
//自定义使用库
BasisService basisService = LdService.newInstance(BasisService.class,"test");
```
### 3、内置基础方法 满足一般业务
```
public List  TermQuery(String field,String value,int num)
public long IntDelete(String field,int value)
public void addIndex(List  list)
public List  searchList(Query query, int n)
public   Page  searchList(Query query,Page  page)
public List  searchTotal()
public long addDocuments(Iterable > docs)
public long addDocument(Iterable  doc)
public int count(Query query)
public TopDocs search(Query query, int n)
public TopFieldDocs search(Query query, int n, Sort sort)
public long deleteAll()
public long deleteDocuments
public long deleteDocuments(Term... terms)
public void deleteUnusedFiles()
public long updateIndex(List  list,Term term)
public List  toDocument(List  list)
public void goBack()
```
### 4、如何测试
```
//手动启动
LuceneX.start(DemoConfig.class);
```
### 5、如何实现自己的Service
#### 5.1、继承BasisService
#### 5.2、可以使用父类已有的基础方法也可以使用 SourceConfig config 变量获取以下字段
```
private String indexPath;//存储地址
private boolean highlight;//是否高亮
private IndexWriter writer;//写入对象
private IndexSearcher searcher;//查询对象
private PerFieldAnalyzerWrapper analyzer;//分词器
private Class  defaultClass;//存储对象Class
private Highlighter highlighter;//高亮标签
```
#### 5.3、使用实例Demo
```
default public int count(Query query) throws IOException {
	return config.getSearcher().count(query);
}
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)