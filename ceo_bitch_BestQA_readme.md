####系统工程简介：
- 本系统基于Equeue消息框架

####系统工程结构：

1. BestQA.Commands ：即为CQRS框架中的Command
2. BestQA.CommandSubscribe： 为系统命令的订阅处理程序
3. BestQA.Domain: 核心领域层
4. BestQA.EventSubscribe: 为领域事件订阅处理程序
5. BestQA.MessageQueue: 系统消息队列程序
6. BestQA.MockRepository:系统数据存储处理，采用EF方式
7. BestQA.QueryInterface:系统查询接口，即CQRS中的Query
8. BestQA.Web：基于MVC的用户操作界面，前端采用angularjs
9. Lee.Infrastructure：公共类库，与平台无关

####启动顺序：

- 创建数据库：BestQA，并使用InitTables.sql进行初始化；
- 依次运行：
1. BestQA.MessageQueue.exe
2. BestQA.CommandSubscribe.exe
3. BestQA.EventSubscribe.exe
4. BestQA.Web(注意修改连接字符串)

####典型的业务处理流程：

发布一个新问题：
- 用户通过WEB发送CreateNewQuestionCmd
- BestQA.MessageQueue收到命令
- BestQA.CommandSubscribe收到通知并处理，然后发送QuestionCreatedEvent
- BestQA.MessageQueue收到领域事件
- BestQA.EventSubscribe处理领域事件，把结果写入数据库


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)