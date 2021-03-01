

------

环境：

[jkd8+]()

[mysql5.6+]()

[flowable6.4.0]()



# 1、流程启动认证

## 1.1 描述

​	默认情况下，任何人都可以启动已部署流程定义的新流程实例。可以使用流程启动认证功能定义用户与组，让Web客户端可以选择性的限制能够启动新流程实例的用户。请注意Flowable引擎**不会**用任何方式验证认证定义。这个功能只是为了开发人员可以简化Web客户端认证规则的实现。语法与为用户任务指派用户的语法类似：可以使用flowable:potentialStarter标签，将用户或组指派为流程的潜在启动者。这里有一个例子：

```xml
 
   
     
        
          group2, group(group3), user(user3) 
        
     
   

   
  ...
```

在上面的XML中，*user(user3)直接引用用户user3*，而*group(group3)引用组group3*。不显式标明的话，默认为组。也可以使用标签提供。

也可以使用标签提供的flowable:candidateStarterUsers与flowable:candidateStarterGroups的属性。这里有一个例子：

```xml
 
    ...
```

这些属性可以同时使用。



## 1.2 示例

![](./images/ProcessInitiationAuthorization.png)





## 1.3 测试--ProcessInitiationAuthorizationTest

- 部署
- 获取给定用户启动的流程定义列表

```java
public void startableByUser() {
		String userId = "lisi";
		List  processDefinitions = repositoryService.createProcessDefinitionQuery().startableByUser(userId).list();
		for (ProcessDefinition processDefinition : processDefinitions ) {
			System.out.println("===================================" );
			System.out.println("======id: " + processDefinition.getId());
			System.out.println("======name: " + processDefinition.getName());
			System.out.println("======key: " + processDefinition.getKey());
		}
	}
```



- 根据流程定义id，获取启动者的身份关联

```java
public void getIdentityLinksForProcessDefinition() {
		String processDefinitionId = "processInitiationAuthorization:1:3";
		List  identityLinks = repositoryService.getIdentityLinksForProcessDefinition(processDefinitionId);
		for (IdentityLink identityLink : identityLinks ) {
			System.out.println("===================================" );
			System.out.println("======processInstanceId: " + identityLink.getProcessInstanceId());
			System.out.println("======user: " + identityLink.getUserId());
			System.out.println("======group: " + identityLink.getGroupId());
		}
	}
```



- 根据流程定义id，获取启动者的用户列表

```java
public void getUser() {
		String processDefinitionId = "processInitiationAuthorization:1:3";
		List  users = identityService.getPotentialStarterUsers(processDefinitionId);
		for (User user : users ) {
			System.out.println("==================user=================" );
			System.out.println("======id: " + user.getId());
			System.out.println("======firstName: " + user.getFirstName());
			System.out.println("======lastName: " + user.getLastName());
		}
	}
```



- 根据流程定义id，获取启动者的用户组列表

```java
public void getGroup() {
		String processDefinitionId = "processInitiationAuthorization:1:3";
		List  groups = identityService.getPotentialStarterGroups(processDefinitionId);
		for (Group group : groups ) {
			System.out.println("==================group=================" );
			System.out.println("======id: " + group.getId());
			System.out.println("======name: " + group.getName());
		}
}
```



- 启动自己名下的流程实例

```java
public void getMyProcessDefinitionAndStart() {
		String userId = "lisi";
		List  processDefinitions = repositoryService.createProcessDefinitionQuery().startableByUser(userId).list();
		for (ProcessDefinition processDefinition : processDefinitions ) {
			System.out.println("===================================" );
			System.out.println("======id: " + processDefinition.getId());
			System.out.println("======name: " + processDefinition.getName());
			System.out.println("======key: " + processDefinition.getKey());
			
			//启动流程实例
			runtimeService.startProcessInstanceById(processDefinition.getId());
		}
}
```



- 查看数据库表

```sql
SELECT * FROM flowable.act_re_procdef;
SELECT * FROM flowable.act_ru_identitylink;
SELECT * FROM flowable.act_ru_execution;
SELECT * FROM flowable.act_ru_task;
```



- 完成任务

```java
public void complete() {
		String taskId = "7505";
		taskService.complete(taskId);
}
```



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)