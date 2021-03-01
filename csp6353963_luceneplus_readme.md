                            

### LucenePlus  让搜索开发更简单，更快捷，更容易维护   


### 简介
    lucenePlus 是基于 lucene 6.x 实现的，具有 易学易用、极其稳定、内置功能丰富 的全文搜索框架、lucene 6.x 要求jdk 版本 1.8 以上  请注意

### 特点
    。多表分库设计
    。自定义非法过滤
    。动态查询索引支持
    。自定义索引条件
    。自定义排序条件
    。自定义高亮显示
    。一键增删改查
    。内置中文检索 IK

### 应用场景
    论坛、商城、音乐、电影、小说 等。。。。 各个领域
	
### 安装说明：
	把resources 文件下的 luceneHome.zip  解压到 d盘 根目录（可以是别的目录）运行：TestLucenePlus 测试类 里面的方法

### 文档：
	。Config 配置类  只要配置 Lucene_path  和 Illegal_filtering 
	。Lucene_path 是luceneHome.zip 解压后的根目录
	。Illegal_filtering是非法字符过滤,以逗号分割 如：xxx,xxx,xxx
		      
	。LucenePlugin  必须传的2个参数是  Config配置类 和 luceneHome/core  下的 一个表 
        。本测试用例是 test所以传入 test 即可(参考solr)，可选参数是分词器默认是 ik，传参方式 AnalyzerType.IKAnalyzer
        。每个表里都有一个配置文件 如   ..../luceneHome/core/conf/config.xml  文件
	。里面的 field 是用来 定义字段	
        。每个 field 有type,name,isQuery,isSort 4个属性
        。type = int类型 或 string  字母为小写
        。name = 字段名称
        。isQuery = 该字段是否参与查询  y 是  n 不
        。isSort = 改字段 是否 参与排序  y  是 n  不  ,升降排序  例： y-y /  y-n
        。boost  = 权重  选填


### 更新
        。2017-4-11 ： 增加权重、优化代码

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)