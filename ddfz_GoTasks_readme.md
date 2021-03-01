#GoTasks

呃，不用说明了吧，直接go build就可以随意玩了。

已通过编译的版本包括：`go1.2.1 linux/amd64`、`go1.4.2 windows/amd64`。

目前我已经持续运行了超过12个小时，15个任务，其中有2个是秒发的任务，非常稳定没有中断过。

Http任务的执行是并发的，绝不延迟，同一个任务，下一次执行不会受到上一次任务的延迟而迟滞，所以请确定接收服务器能承受住压力才好使用。

日志库用了这个[https://github.com/donnie4w/go-logger](https://github.com/donnie4w/go-logger)，不过我修改了一些。

##如何获取代码

请使用go get指令获取代码：

```shell
go get git.oschina.net/janpoem/GoTasks
```

上述的指令，会将该项目所需的go-logger也下载到GOPATH的src目录中。

打开你的IDE，如IDEA或LiteIDE

创建如下的代码：

```go
package main

import "git.oschina.net/janpoem/GoTasks"

func main() {
    GoTasks.TaskServiceStart()
}
```

然后编译这个项目即刻。

##启动参数

```
./GoTasks --help
Usage of ./GoTasks:
  -cycle=43200: 重新加载任务的周期，单位秒
  -log-dir=".": 日志输出目录
  -log-level=1: 日志输出级别
  -show-complete=0: 显示请求完成的信息
  -tasks="": 任务列表
  -trace-cycle=600: 输出心跳信息的周期，单位秒
  -test=false: 是否测试命令的参数
  -console=true: 是否在命令行输出调试
  -pprof-port=0: pprof服务器端口号，为零不启用（默认为零）
```

执行命令

```
GoTasks -tasks="http://localhost/tasks.json" -cycle=43200
```

##tasks.json输出格式

给一个tasks.json的清单样例：

```json
{
	"Tasks":[
		{
			"Name":"kissOschina",
			"Url":"http://www.oschina.net/",
			"Cycle":1,
			"PostUrl":"",
			"Delay":10
		},
		{
			"Name":"kissBaidu",
			"Url":"http://www.baidu.com/",
			"Cycle":1,
			"PostUrl":"",
			"EventName":"baiduBack"
		}
	]
}
```

* Name 任务名称
* Url 要取得数据的Url
* Cycle 获取的周期，单位秒
* PostUrl 从Url取得的页面的内容，将他Post到另一个Url上
* Delay 延迟启动第一次的任务，单位秒，第二次恢复正常周期时间
* EventName 任务完成后触发的事件名称，EventName和Name只能两者取其一

##linux服务器发布

修改go_tasks.sh文件，修改13-35行部分的内容，主要填写：

* DAEMON GoTasks执行文件所在
* TASKS 任务URL

其它看需要修改。执行参数：

```bash
go_tasks.sh start    # 启动
go_tasks.sh stop     # 停止
go_tasks.sh restart  # 重启
go_tasks.sh status   # 查看状态
go_tasks.sh proc     # 查看具体的进程
```

目前限定单进程执行，如果要跑多个进程，最好将复制多一套执行文件和启动脚本，然后就可以多个进程了。

##新增事件接口

以上述的tasks.json为例，目前提供了两个事件的入口：

```go
package main

import (
	"git.oschina.net/janpoem/GoTasks"
	"git.oschina.net/janpoem/go-logger"
)

func main() {
    defer GoTasks.TaskServiceStart()
    // 针对Url请求的返回
    GoTasks.On("get:kissOschina", func(resp string) {
        fmt.Println(resp.Name) // 输出kissOschina
    })
    // 如果PostUrl不为空，则在完成PostUrl请求以后，会触发这个事件
    GoTasks.On("get:baiduBack", func(resp string) {
    
	})
}
```

##修改日志

**2015-05-04**

* 将Prepare函数改为可被外部调用的函数，并且限制Prepare只能被执行一次
* Task增加Delay，Delay用于延迟第一次执行任务的触发时间，用于降低全部任务启动第一次的并发压力，单位为秒，第二次执行任务就不会Delay了。
* Task增加EventName，用于定义任务完成时，触发执行的任务，EventName和Name只能选其一。
* TaskResult增加Name，用于获取当前执行的任务的名称。

**2015-03-26**

* 将logger的代码移出核心代码
* 调整一下代码的结构
* 增加pprof服务器，可以监控内存和goroutine的情况，监控的入口是：`http://localhost:端口号/debug/pprof/`
* 增加事件机制，主要针对每个任务完成时调用

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)