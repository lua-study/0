# yiban_leave

#### 介绍
基于springboot和易班开放平台的学生请假系统， 完成学生请假审批的基本功能

#### 使用技术
##### 后端
1. 持久层框架-mybatis
2. 数据库连接池-druid
3. json处理 fastjson
4. 二级缓存 ehcache
5. 日志 logback
6. 模板引擎 thymeleaf
7. 工作流 activiti 6.0
8. 代码生成器 mybatis-plus

##### 前端(前端框架都是以webjar形式引入)
1. jquery
2. bootstrap
3. 弹出层 layer

#### 基本功能
##### 1.0.0
1. 学生个人中心：学生可修改本人的基本信息（事实上只能修改宿舍号，其他的信息如学号，姓名等等都是从易班获取..滑稽:)）
2. 请假：学生可填写请假信息（请假类型，请假原因，开始时间，结束时间）向审批人提交请假请求等待审核人审批，具体审核的流程由请假时间决定，请假信息提交后，系统会向审核人发送信息进行提醒
3. 审核：学生提交的请假信息会被展示到审核人页面，审核人通过查看请假信息的详情决定是否同意请假，审核完成后，会向学生发送提示信息
4. 销假：学生的请假被通过后，必须完成销假操作，否则无法再次请假
5. 分页功能：请假信息会以列表的形式呈现给用户，并提供了基本分页功能（首页，尾页，上一页，下一页）
##### 1.0.1
1. 修复请假详细信息 学生学号和班级名位置颠倒问题
2. 修复学生个人中心宿舍号中包含0的提升宿舍号格式错误问题
3. 添加班主任待销假列表个数徽章



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)