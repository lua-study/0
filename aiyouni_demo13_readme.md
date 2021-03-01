

------

环境：

[jkd8+]()

[mysql5.6+]()

[flowable6.4.0]()



# 1、Data objects

## 1.1 描述

​	BPMN提供了将数据对象定义为流程或子流程元素的一部分的可能性。根据BPMN规范，数据对象可以包含复杂的XML结构，并可以从XSD定义中引入。下列XSD类型为Flowable支持的第一批数据对象：

```xml
 
 
 
 
 
 
```

数据对象定义使用*name*属性值作为新变量的名字，将其自动转换为流程变量。另外，Flowable也提供了为变量设置默认值的扩展元素。下面的BPMN代码片段示例：

```xml
 
   
     
       Testing123 
     
   
  ...
```

## 1.2 示例

![](./images/dataobjects.png)





## 1.3 测试--DataobjectsTest

- 部署
- 启动流程实例

- 查看数据库表

```sql
SELECT * FROM flowable.act_ru_execution;
SELECT * FROM flowable.act_ru_task;
```

- 获取变量

```java
public void getVariablesLocal() {
		String executionId = "32508";
		Map  vars = runtimeService.getVariables(executionId);
		for (Map.Entry  entity: vars.entrySet()) {
      	  String key = entity.getKey();
      	  Object value = entity.getValue();
      	  System.out.println("============获取流程变量：【key:" + key + "】,【value:" + value + "】============");
        }
}
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