# godeim

#### 项目介绍
尝试使用golang实现一个消息通信系统

#### 软件架构
 ##### RootSerMux.go 
 实现黑白名单过滤的一个简单的Server
 
 ```go
 //创建一个server
serMux := server.NewServeMux()
// 注册一个路由
serMux.HandleFunc("/a", a)

//创建一个过滤器
sf := server.NewServerFilter("自定义id")
// 匹配过滤规则，当fb返回true的时候，到此截断，返回false，表示处理流程继续
sf.FilterFunc("/a", filter)
//server添加一个过滤器
serMux.AddFilter(sf.GetId(), sf)

//正常路由
func a(w http.ResponseWriter, r *http.Request) {	
	w.Write([]byte("aaaaa"))
}

//过滤函数写法
func filter(w http.ResponseWriter, r *http.Request) server.FILTER_RESULT {
	w.Write([]byte("done fc\n"))
	return server.FLYUP
}
```
过滤器
 - 过滤规则由 路由和过滤函数 组成
 - 一个过滤器可以添加多个过滤规则
 - 有多个过滤器的时候，按照`server.AddFilter()`的顺序依次执行
 - 同一个过滤器，若存在一个路由地址对应多个过滤函数，则实际执行的是最后一个添加的过滤函数
 

过滤函数的返回值：
 - `FLYUP` 跳过后续所有的过滤器，直接进入正常路由
 - `BREAK` 流程到此截断，后续的过滤器和正常路由都不执行
 - `CONTINUE` 本过滤规则通过，继续下一个过滤规则

#### 安装教程

1. xxxx
2. xxxx
3. xxxx

#### 使用说明

1. xxxx
2. xxxx
3. xxxx

#### 参与贡献

1. Fork 本项目
2. 新建 Feat_xxx 分支
3. 提交代码
4. 新建 Pull Request


#### 码云特技

1. 使用 Readme\_XXX.md 来支持不同的语言，例如 Readme\_en.md, Readme\_zh.md
2. 码云官方博客 [blog.gitee.com](https://blog.gitee.com)
3. 你可以 [https://gitee.com/explore](https://gitee.com/explore) 这个地址来了解码云上的优秀开源项目
4. [GVP](https://gitee.com/gvp) 全称是码云最有价值开源项目，是码云综合评定出的优秀开源项目
5. 码云官方提供的使用手册 [https://gitee.com/help](https://gitee.com/help)
6. 码云封面人物是一档用来展示码云会员风采的栏目 [https://gitee.com/gitee-stars/](https://gitee.com/gitee-stars/)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)