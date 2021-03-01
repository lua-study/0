# octopus
# 基于Pyspark，通过SQL简化数据处理与加工，同时保证了Python的灵活性，提供了更高扩展性，使各组件通过Django连接，减轻使用组件障碍。使数据抽取、加工、多维预生成Cube、下推数据、SQL查询、存储过程等功能平台化。
# 主要组件
Django + Spark + hive + hdfs + parquet + ES
# 主要功能
1、抽取不同数据库的数据，装入hive中，以parquet做为hive的文件存储格式。
2、根据维度属性预生成多维多层级汇总CUBE，可选择将数据导入Elastic Search中。
3、提供了SQL查询页面、提供了Python命令页面。
4、提供了数据抽取的配置页面，支持Oracle、Teradata等数据库抽取配置。
# 主要思路
通过Django维持了同一个SparkSession，避免了数据交换，Python命令页面与SQL页面基于同一个SparkSession，DataFrame可以直接互用。
避免了Python处理数据的复杂性，数据准备可通过SQL完成，处理循环、判断逻辑可以通过Python完成；同时保证Python的灵活性，可以调用Pandas、Scipy等数据分析常用包。

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)