### CloudLimiter是什么？
CloudLimiter是成都基础平台架构开发的用于TPS、及流量控制和统计的基础组件，适用于java的maven项目：

* 支持TPS控制
* 支持流量控制
* 流量统计及TPs统计

当前最新版本功能支持：
* 1、支持TPS控制
* 2、支持流量控制
* 3、流量统计及TPs统计

----------

### 如何开始？`必读`
* [下载最新版安装包]()
* [`CloudLimiter使用指南`]已经归档到当前项目docs/目录下


----------

### 开源协议
[Apache License, Version 2.0](http://www.apache.org/licenses/LICENSE-2.0.html) Copyright (C) 2016-2020 CloudLimiter Group Holding Limited

----------

### 开发规范
* 代码使用Eclipse代码样式格式化，提交代码前须格式化[cloudmq.java.code.style.xml](http://git.oschina.net/gomecode/cloudmq/tree/dev/docs/cloudmq.java.code.style.xml)
* 必须设置 Java源文件使用Unix换行、UTF-8文件编码（idea设置：File->Settings->Editor->Code Style line separator 设置为Unix and OS）
* 请在git clone命令之前执行`git config --global core.autocrlf false`，确保本地代码使用Unix换行格式
* 请在非主干分支上开发，禁止提交本地未测试运行通过代码到线上
* 每次提交及之前(正常来说需要先pull,解决冲突)，对代码进行修改必须有相对应的解释说明
* 为了避免对原生代码的侵入、对于修改原生Rocketmq代码的，需要知会组内所有开发人员，经过审核后方可提交（且需要有统一格式注释，参照注释类型3）



### 注释规范
* 对于注释，请遵照以下规范：
* 注释类型1（适用于类或者包或者方法注释）、

```
/**
 * 顺序消息的生产者（顺序消息的消费者与普通消费者一致）
 *
 * @Author xxx
 * @Since 2016/6/27 or v1.0.0
 */
```

* 注释类型2（适用于结构体或者包名注释）、

```
// 由于是顺序消息，因此只能选择一个queue生产和消费消息
```

* 注释类型3（适用于结构体或者包名注释）、

```
// xxx  Modify: xxx,   Since: 2017/3/20 or v1.0.0
// xxx  Add: xxx,   Since: 2017/03/20 or v1.0.0
```


* 关于TODO、FIXME、XXX注释规范、

```
// TODO: + 说明：xxx Author: xxx,    Since: 2017/3/20 or v1.0.0
```
如果代码中有TODO该标识，说明在标识处有功能代码待编写，待实现的功能在说明中会简略说明。

```
// FIXME: + 说明：xxx Author: xxx,    Since: 2017/3/20 or v1.0.0
```
如果代码中有FIXME该标识，说明标识处代码需要修正，甚至代码是错误的，不能工作，需要修复，如何修正会在说明中简略说明。

```
// XXX: + 说明：xxx Author: xxx,    Since: 2017/3/20 or v1.0.0
```
如果代码中有XXX该标识，说明标识处代码虽然实现了功能，但是实现的方法有待商榷，希望将来能改进，要改进的地方会在说明中简略说明。


### 开发IDE
* 开发工具不做统一规定（Idea、Eclipse都可以），建议使用Idea
* 建议使用最新版格式Idea，附下载地址：http://pan.baidu.com/s/1slMkXY1
* 附Idea属性格式注释文件下载地址：http://pan.baidu.com/s/1hrU3IgW

----------

### 联系我们
 :fa-comments-o: 
----------


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)