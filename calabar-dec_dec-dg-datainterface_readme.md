# dec-dg-datainterface
    东锅写入查询数据接口服务

## 部署节点
    实时处理节点：dataquery004
    项目存放位置：calabar 用户目录下的 dfdq，例如：/home/calabar/dfdq/

### 启动
    PROJECT_HOME/bin/start.sh

### 停止
    PROJECT_HOME/bin/stop.sh
    
### conf.properties 中主要需要修改的内容
    #server 服务
	server.port=19999

	#mysql    mysql的配置
	spring.datasource.driver-class-name=com.mysql.jdbc.Driver  
	spring.datasource.url=jdbc:mysql://10.3.101.128:3306/dfdq
	spring.datasource.username=root
	spring.datasource.password=123456

	#kks table name kks表配置
	query.mysql.kks-table-name=d_kks_info  mysql中kks信息表表名
	#field name of substd_code 子系统编码配置
	query.mysql.substdcode-name=substd_code   mysql中子系统编码字段名

	#opentsdb opentsdb的配置
	opentsdb.url.query=http://10.3.101.115:9998/api/query/    opentsdb普通查询端点
	opentsdb.url.query-last=http://10.3.101.115:9998/api/query/last opentsdb最后一条查询端点
	opentsdb.url.put=http://10.3.101.115:9998/api/put	opentsdb写入端点




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)