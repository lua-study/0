# job-timer

定时任务管理工具，目前可管理三类任务：spark job、datax 数据导入/导出任务、shell脚本。

一个任务包含的属性有：标题、说明、类型（spark|datax|shell）、运行参数、开始时间、运行周期

定时任务以组的方式进行管理，进行一次数据分析通常需要多个任务协同工作，比如需要先导出数据到hdfs，然后用spark分析导出的数据，在导出数据时可能还需要做一些文件转移、重命名等操作。

这些任务有严格的执行顺序，这样的一系列任务放做为一个任务组运行。当分析任务比较简单时，也可以一个组中只包含一个任务。

# 功能模块

* 任务组的增、删、改、查操作
* 集成了livy控制台
* 文件上传，可将文件直接上传到 hdfs
* 状态监控
× 定时器模块

# 环境

基于 node.js v8.9 开发，由于使用了 async/await 关键字，所以运行环境至少 node.js v8.1 以上。

UI页面基于 vue + elementUI，需chrome 45 版本以上。

项目已在公司的linux服务器上线运行，操作系统理论上可支持 windows与mac，但未经过测试。

* spark环境：与 spark 集群的通讯依赖 livy 实现，但是任务运行日志是使用 yarn 命令收集，所以 spark on yarn 模式可使用项目的完整功能，其它的 spark 集群模式只能发布任务，不能收集到任务日志（livy日志依然可以收集）。
* datax环境：阿里的开源项目，依赖python2.7，需在path环境变量中配置python。
* shell环境：脚本运行的根目录是项目所在目录，如果脚本对路径有要求，最好在脚本开头使用 cd 命令切换目录，windows环境下有可能会出现中文字符集问题（node.js默认UTF-8格式，windows bat 文件为操作系统默认）。
* hadoop环境：文件上传功能使用的是 hadoop fs 命令，可直接把文件上传到hdfs，如果没有 hadoop 环境，不影响任务发布，只影响文件上传功能。

# 依赖

* node.js v8.1 以上
* mongodb 3.4 以上
* apache livy 0.5
* datax 3.0
* chome浏览器 45
* linux 操作系统
* spark 2.0x
* hadoop 2.7.x
* 其它依赖见 package.json 与 admin/package.json

# 任务说明

## spark job

基于 apache livy 工具二次开发，通过 livy 向 yarn 提交 jar，需注意 spark 运行的 jar 包要放置在 hdfs 中。

可参考 livy rest api 文档： https://livy.incubator.apache.org/docs/latest/rest-api.html

搭建过程：http://note.youdao.com/noteshare?id=ca7126842d0abc74c52998fab8e27306&sub=D7CED5916C2748A7BBAA6072297F5174

## datax job

阿里开源的数据导入、导出工具，可以支持大部分存储介质之间相互提取导入，通常用于把 oracle 中的数据导入到 hive。

依赖　python 2.7

可参考文档：https://github.com/alibaba/DataX

## shell job

基于 node.js child_process 模块的 execFile 函数开发，系统会将 shell 脚本保存成 sh 文件，然后调用 execFile 函数执行，需注意脚本输出不能大于200k。

参考文档：http://nodejs.cn/api/child_process.html#child_process_child_process_execfile_file_args_options_callback

默认的超时时间为 10分钟，暂不支持 args 参数列表，options可以使用。

## spark streaming job

由于 streaming 任务常驻 livy session，所以在一个任务组中只能包含一个 streaming 任务，而且必须为最后一个。

系统会每隔一段时间检查一次所有 streaming 任务的运行状态，对于异常退出的任务会尝试自动恢复。检查间隔可在 config.js 中配置，创建 streaming 任务时可选择是否自动恢复。

项目不会对 streaming 任务提取运行日志。

由于 streaming 是运行在 livy session 中，所以重启 job-timer 项目不会干扰到 streaming 任务的运行。

# 配置

## 前台ui配置

UI界面目录是 /admin 基于VUE开发，是一个 使用 vue-cli 工具创建的项目，如果需要二次开发，参考 vue webpack 模板项目。

在UI界面中，以 iframe 方式加入了 livy 的控制台页面，所以需要配置 livy 的 url 地址，配置项为 LIVY_HOST，开发环境与生产环境分别对应以下两个文件：

* /admin/config/dev.env.js  开发环境
* /admin/config/prod.env.js 生产环境

## 后台配置

后台所有配置都在 /config.js 文件中，系统判断环境变量 RUN_MODULE = proc 为生产环境，其它值或未配置为开发环境，见 config.js 代码。

配置文件中同时保存了开发环境与生产环境的配置，修改配置时需要注意对应环境。所有配置项都是用``` ? : ``` 三元运行符配置的，如果没有表示开发环境与生产环境配置相同。

通常初次配置需要修改的配置项包括：

* upload：文件上传临时目录
* livy： apache livy api host
* mongo：mongodb相关配置，如果需要安全验证，参考 [mongodb模块](http://mongodb.github.io/node-mongodb-native/3.0/api/MongoClient.html) 配置
* datax：datax3.0 home 目录
* log4js：日志输出
* listenPort：占用端口，如果修改此项，会影响开发环境下的vue，还需修改 /admin/config/index.js 文件中的端口配置

# 运行

web ui 使用 vue + elementUi 开发，使用以下命令

```shell
# 生产环境

# 启动 livy、mongodb，配置 python、hadoop 环境变量

cd admin

npm install		#安装web ui相关包

npm run build  #ui系统打包

./publish.sh   #部署到 public 目录

cd ..

npm install   #安装后台相关包

npm start   #运行，或 pm2 start bin/www

# 开发模式

cd admin

npm install		#安装web ui相关包

npm run dev  #运行 vue 项目，默认占用8080端口，如果8080被占用，会自动调整端口，详细见命令输出

#另开启一个终端运行后台

npm install

npm start

```

# 表结构

数据库使用的是 mongodb .

## jobs

任务组

```
{
	_id: '', //mongodb 自动生成
	title: '',
	description: '',
	beginTime: new Date(''),	//开始运行的时间
	cycle: 10000,		//运行周期，单位 ms
	status: '1',		//状态：0-不可用，1-可用
	lastRunTime: Date,
	lastLog: '_id of logs',
	group: [{			//任务组，顺序执行组中的任务
		id: 0,		//组中的id，在同一组中不可重复
		title: '',
		description: '',
		type: 'spark | datax | shell',		//任务类型，对应不同的执行插件
		args: {},		//任务参数
		lastRunTime: Date
	}, ...]
}
```

## logs

日志

```
{
	_id: '', //mongodb 自动生成
	jobId: '_id of jobs',
	title: '',
	group: [{
		id: 0,
		title: '',
		type: 'spark | datax | shell',
		args: {},
		log: 'text | file',
		begin_time: Date,
		end_time: Date
	}],
	beginTime: Date,
	endTime: Date
}
```

# 界面

## 任务列表

![任务列表](docs/images/jobs.png)

## 日志列表

![日志列表](docs/images/logs.png)

## 日志详细

![日志详细](docs/images/log.png)

## 文件上传

![文件上传](docs/images/upload.png)

## 新建任务组

![新建任务组](docs/images/add-group.png)

## 新建子任务

![新建子任务](docs/images/add-job.png)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)