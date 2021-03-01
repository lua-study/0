# 消息服务平台
消息服务平台，给其他系统提供统一的消息接入，可以处理未读、已读、消息列表等，消息支持发送邮件【支持附件发送，附件必须为互联网可以访问的地址】或短信。
具体改造可以见SendEmailTask.java和SendSmsTask.java文件
消息服务平台还支持设置个人对分组消息的接收开关等规则，可以设置单个用户分组下的接收短信手机号和接收邮箱信息

message-server：下载源码后，启动message-server的服务，启动服务前，需要先创建好数据库(message)，然后执行sql脚本(message.sql、init.sql)文件。

html版本的API：message-server\src\main\webapp\api下的index.html入口页面，提供了html调度接口

# 系统、用户
### 1. 需要先创建系统的信息
```
调用接口：/sysInfo/saveOrUpdate
参数：
    sysNo：系统编码
    name：系统名称
参考测试类：AccessUserTest.java
```

### 2. 导入系统用户信息
```
调用接口：/userInfo/saveOrUpdate
参数：
	sysNo：系统编码
    userId：用户编号
参考测试类：AccessUserTest.java
```

# 消息分组
### 1. 新增修改消息分组
```
调用接口：/msgGroup/saveOrUpdate
参数：
    id：分组编码
    sysNo：系统编码
    name：分组名称
    type：类型[10系统、20个人、30其它]
	pid：父分组编码
参考测试类：MsgGroupTest.java
```

### 2. 分页获取消息分组列表
```
调用接口：/msgGroup/pageQuery
参数：
    page：页码
    size：每页大小
    sysNo：系统编码
	pid：父分组编码
参考测试类：MsgGroupTest.java
```

# 用户分组规则
### 1. 新增或修改用户分组规则
```
调用接口：/userGroupRule/saveOrUpdate
参数：
    sysNo：系统编码
    groupId：分组编号
    userId：用户编号
    status：状态[10打开、20关闭]
    emailStatus：发邮件[10打开、20关闭]
    smsStatus：发短信[10打开、20关闭]
	recePhone：接收手机[多个;分隔]
	receEmail：接收邮箱[多个;分隔]
参考测试类：UserGroupRuleTest.java
```

### 2. 获取用户分组规则的集合
```
调用接口：/userGroupRule/find
参数：
    sysNo：系统编码
    userId：用户编号
参考测试类：UserGroupRuleTest.java
```


# 消息 - 操作
### 1. 发送消息 (支持群发多人)
```
调用接口：/msgInfo/save
参数：
    sysNo：系统编码
    groupId：消息分组编号[可以传入sys代表系统的消息分组]
	type：类型[10阅读、20待办]
    title：标题
    content：内容
    sendUserId：发送人编码
    receUserIds：接收人编码集合[多个用;分隔]
	receContent：接收短信或邮件的内容[不传默认为content内容]
	receEmailFiles：邮件的附件[多个附件;分隔]
	recePhones：接收手机[多个;分隔]发送开关根据第一个接收人获取
	receEmails：接收邮箱[多个;分隔]发送开关根据第一个接收人获取
参考测试类：MsgSendTest.java
```

### 2. 删除我接收的消息
```
调用接口：/msgInfo/deleteRece
参数：
    id：消息编号
    sysNo：系统编码
    userId：用户编号
参考测试类：MsgInfoTest.java
```

### 3. 标记消息的阅读状态
```
调用接口：/msgInfo/updateIsRead
参数：
    id：消息编号
    sysNo：系统编码
    userId：用户编号
    isRead：是否阅读[0否、1是]
参考测试类：MsgInfoTest.java
```


# 消息 - 查询
### 1. 获取用户的未读消息数
```
调用接口：/msgInfo/getCountUnread
参数：
    sysNo：系统编码
    userId：用户编号
	type：类型[10阅读、20待办]
参考测试类：MsgQueryTest.java
```

### 2. 获取用户的未读消息列表
```
调用接口：/msgInfo/pageQueryUnread
参数：
    page：页码
    size：每页大小
    sysNo：系统编码
    userId：用户编号
    groupId：分组编号，多个;隔开
	type：类型[10阅读、20待办]
参考测试类：MsgQueryTest.java
```

### 3. 获取用户的消息列表
```
调用接口：/msgInfo/pageQuery
参数：
    page：页码
    size：每页大小
    sysNo：系统编码
    userId：用户编号
    isRead：是否阅读[0否、1是]不传入获取所有状态的消息
    groupId：分组编号，多个;隔开
	type：类型[10阅读、20待办]
参考测试类：MsgQueryTest.java
```

### 4. 根据分组获取未读记录的列表
```
调用接口：/msgInfo/findGroupUnread
参数：
    sysNo：系统编码
    userId：用户编号
	type：类型[10阅读、20待办]
参考测试类：MsgQueryTest.java
```

### 5. 获取消息详情
```
调用接口：/msgInfo/getDtl
参数：
    id：消息编号
    sysNo：系统编码
    userId：用户编号
参考测试类：MsgQueryTest.java
```

### 6. 根据扩展字段获取消息列表
```
调用接口：/msgInfo/findByExt
参数：
    sysNo：系统编码
    ext1：扩展1
    ext2：扩展2
    ext3：扩展3
参考测试类：MsgQueryTest.java
```


# 管理后台
```
http://127.0.0.1:6070/index.jsp
帐号：admin
密码：123456
```

### 接入系统的维护页面
![接入系统管理](https://gitee.com/uploads/images/2018/0111/152221_fabf8009_126057.jpeg "接入系统管理")

### 发送的消息列表页面
![消息管理](https://gitee.com/uploads/images/2018/0111/152321_0b005d1c_126057.jpeg "消息管理")

更多完善中。。。

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)