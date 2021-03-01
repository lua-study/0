

------

环境：

[jkd8+]()

[mysql5.6+]()



# 1、原理

## 1.1 条件序列流

​	在连线上设置条件表达式。

## 1.2 网关默认出线 

在连线上**不指定出线条件**，网关的条件不满足时，默认按此出线继续执行。

```
 
 
```

## 1.3 消息事件 



### 1.3.1 消息事件定义

​	消息事件是引用命名消息的事件。消息具有名称和有效负载。与信号不同，消息事件始终指向**单个接收器**。

​	使用该`messageEventDefinition`元素声明消息事件定义。该属性`messageRef`引用`message`声明为`definitions`根元素的子元素的元素。以下是一个过程的摘录，其中两个消息事件由start事件和中间捕获消息事件声明和引用。

```xml
 

   
   

   

     
        
     
    ...
     
        
     
    ...
   

 
```

### 1.3.2  抛出一个消息事件

- 作为可嵌入的流程引擎，Flowable并不关心实际接收消息。这将取决于环境并且需要特定于平台的活动，例如连接到JMS（Java消息服务）队列/主题或处理Web服务或REST请求。因此，接收消息是您必须实现的过程引擎嵌入的应用程序或基础结构的一部分。


- 在应用程序中收到消息后，您必须决定如何处理它。如果消息应触发新流程实例的启动，请在运行时服务提供的以下方法之间进行选择：

```
ProcessInstance startProcessInstanceByMessage(String messageName);
ProcessInstance startProcessInstanceByMessage(String messageName, Map  processVariables);
ProcessInstance startProcessInstanceByMessage(String messageName, String businessKey,
    Map  processVariables);
```

​	**这些方法使用引用的消息启动流程实例。**

-  如果消息需要由现有流程实例接收，则首先必须将消息关联到特定流程实例（请参阅下一节），然后触发等待执行的继续。运行时服务提供以下方法，用于根据消息事件订阅触发执行：

```
void messageEventReceived(String messageName, String executionId);
void messageEventReceived(String messageName, String executionId, HashMap  processVariables);
```

### 1.3.3 查询消息事件订阅

- 在消息启动事件的情况下，消息事件订阅与特定的*流程定义*相关联。可以使用以下命令查询此类消息订阅`ProcessDefinitionQuery`：


```
ProcessDefinition processDefinition = repositoryService.createProcessDefinitionQuery()
      .messageEventSubscription("newCallCenterBooking")
      .singleResult();
```

- 由于特定邮件订阅只能有一个流程定义，因此查询始终返回零或一个结果。如果更新了流程定义，则只有最新版本的流程定义才能订阅消息事件。


- 在中间捕获消息事件的情况下，消息事件订阅与特定*执行*相关联。可以使用以下命令查询此类消息事件订阅`ExecutionQuery`：

```
Execution execution = runtimeService.createExecutionQuery()
      .messageEventSubscriptionName("paymentReceived")
      .variableValueEquals("orderId", message.getOrderId())
      .singleResult();
```

​	此类查询称为相关查询，通常需要有关流程的知识（在这种情况下，给定orderId最多只有一个流程实例）。

### 1.3.4 边界消息触发

​	消息在接收messageEventReceived的时候，会触发对应边界消息事件。



# 1.4  信号事件 

​	一个[信号](https://www.flowable.org/docs/userguide/index.html#bpmnSignalEventDefinition)启动事件可用于使用命名信号来启动一个过程实例。可以使用中间信号throw事件或通过API（*runtimeService.signalEventReceivedXXX*方法）从流程实例中*触发*信号。在这两种情况下，将启动具有相同名称的信号启动事件的所有流程定义。

请注意，在这两种情况下，还可以在流程实例的同步和异步启动之间进行选择。

在`signalName`必须在API中传递是在给定的名称`name`的属性`signal`被引用的元素`signalRef`的属性`signalEventDefinition`。

# 2、流程图

- 条件序列流

![](./images/conditionsequenceflow.png)

- 网关默认出线流程

![](./images/gatewaydefultoutsequenceflow.png)

- 消息开始事件流程

![](./images/messageprocess.png)

- 信号开始事件流程

![](./images/singalstartevent.png)

# ３、配置

## 3.1 条件序列流

在连线上设置条件表达式。

```xml
  
        10 }]]>	          
 
```



## 3.2 网关默认出线

在连线上**不指定出线条件**，网关的条件不满足时，默认按此出线继续执行。

```
 
 
```



## 3.3 消息事件

- 消息定义

  ```
    
  ```

- 中间消息抛出事件定义以及消息引用

```
 
        
 
```

- 边界消息事件定义以及消息引用


```xml
 
        
 
```



## 3.4  信号事件 

- 信号定义

```xml
  
```

- 引用信号

```
 
        
 
```



# ４、实践测试



- 运行demo
- 查看数据库表

```
 SELECT * FROM flowable.ACT_RU_EXECUTION;
 SELECT * FROM flowable.ACT_RU_EVENT_SUBSCR;
 SELECT * FROM flowable.ACT_RU_TASK;
```



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)