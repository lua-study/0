

------

环境：

[jkd8+]()

[mysql5.6+]()

[flowable6.4.0]()



# 1、原理

## 1.1 用户任务

​	一个*用户任务*被用来模拟需要由人来完成的工作。当流程执行到达此类用户任务时，将在分配给该任务的任何用户或组的任务列表中创建新任务。

## 1.2 脚本任务

### 1.2.1 脚本任务是一种自动活动。当进程执行到达脚本任务时，将执行相应的脚本。

### 1.2.2 属性：

- **name**：任务属性，用于指示任务的名称
- **type**：任务属性，其值必须为“script”以指示任务的类型
- **scriptFormat**：指示脚本语言的扩展属性（例如，javascript，groovy）
- **script**：要执行的脚本，定义为名为“script”的字段元素中的字符串
- **autoStoreVariables**：可选的任务属性标志（默认值：false），指示脚本中定义的变量是否将存储在执行上下文中（请参阅下面的注释）
- **resultVariableName**：可选的任务属性，当存在时，将在Execution上下文中使用脚本评估结果存储具有指定名称的变量（请参阅下面的注释）

### 1.2.3 flowable支持三种脚本任务类型：Javascript、groovy、juel。

 通过指定**脚本**和**scriptFormat**来定义脚本任务类型，其中Groovy脚本引擎与groovy-all JAR捆绑在一起，必须引入相关依赖:

```xml
 
		 org.codehaus.groovy 
		 groovy-all 
		 2.5.4 
		 pom 
 
```
### 1.2.4 脚本中的变量：

```javascript
var sum = a+b;
execution.setVariable("sum",sum);
```

​	也可以简单地调用*execution.setVariable("variableName", variableValue)*，在脚本中设置流程变量。默认情况下，变量不会自动储存（**请注意，在一些早期版本中是会储存的！**）。可以将`scriptTask`的`autoStoreVariables`参数设置为`true`，以自动保存任何在脚本中定义的变量（例如上例中的*sum*）。然而这并不是最佳实践。**最佳实践是显式调用execution.setVariable()**，因为在JDK近期的一些版本中，某些脚本语言不能自动保存变量。查看[这个链接](http://www.jorambarrez.be/blog/2013/03/25/bug-on-jdk-1-7-0_17-when-using-scripttask-in-activiti/)了解更多信息。

```xml
 
```

​	此参数的缺省值是`false`，这意味着如果从脚本任务定义中省略该参数，则所有声明的变量将仅在脚本的持续时间内存在。

### 1.2.5 脚本任务的结果

​	脚本任务的返回值，可以通过为脚本任务定义的*'flowable:resultVariable'*属性设置为流程变量。可以是已经存在的，或者新的流程变量。如果指定为已存在的流程变量，则流程变量的值会被脚本执行的结果值覆盖。如果不指定结果变量名，则脚本结果值将被忽略。

```xml
 
         
 
```



## 1.3 服务任务

### 1.3.1 有四种方法声明如何调用Java逻辑：

- 指定实现了JavaDelegate或ActivityBehavior的类
- 调用解析为委托对象（delegation object）的表达式
- 调用方法表达式（method expression）
- 对值表达式（value expression）求值

### 1.3.2 字段注入与线程安全

​	通常情况下，在服务任务中使用Java委托与字段注入是线程安全的。然而，有些情况下不能保证线程安全。这取决于设置，或Flowable运行的环境。

当使用*flowable:class*属性时，使用字段注入总是线程安全的（译者注：仍不完全安全，如对于多实例服务任务，使用的是同一个实例）。对于引用了某个类的每一个服务任务，都会实例化新的实例，并且在创建实例时注入一次字段。在不同的任务或流程定义中多次使用同一个类没有问题。

当使用*flowable:expression*属性时，不能使用字段注入。只能通过方法调用传递变量。总是线程安全的。

当使用*flowable:delegateExpression*属性时，委托实例的线程安全性，取决于表达式解析的方式。如果该委托表达式在多个任务或流程定义中重复使用，并且表达式总是返回相同的示例，则字段注入**不是线程安全的**。

### 1.3.3 线程安全最简单的解决方法是：

- 使用表达式代替直接使用Java委托，并将所需数据通过方法参数传递给委托。
- 或者，在每次委托表达式解析时，返回委托类的新实例。这意味着这个bean的scope必须是**prototype（原型）**（例如在委托类上加上@Scope(SCOPE_PROTOTYPE)注解）。

### 1.3.4 异常处理

- 抛出业务异常

​	可以在服务任务或脚本任务的用户代码中抛出BPMN错误。可以在Java委托、脚本、表达式与委托表达式中，抛出特殊的FlowableException：*BpmnError*。引擎会捕获这个异常，并将其转发至合适的错误处理器，如错误边界事件或错误事件子流程。

默认映射是一个不指定类的映射，可以匹配任何Java异常：

```xml
 
        
    	   
  	    
 
```

- 发生异常时，将流程执行路由至另一条路径

  ThrowingDelegate将会抛出BussinessException业务异常，errorcode为localError，Flowable会将`BussinessException`类，转换为带有指定错误代码的BPMN错误，边界错误捕获事件会捕获到此异常，并继续后续操作。

## 1.4 业务规则任务

​	业务规则任务（business rule task）用于同步地执行一条或多条规则。Flowable使用名为Drools Expert的Drools规则引擎执行业务规则。目前，业务规则中包含的.drl文件，必须与定义了业务规则服务并执行规则的流程定义一起部署。这意味着流程中使用的所有.drl文件都需要打包在流程BAR文件中，与任务表单等类似。要了解如何为Drools Expert创建业务规则，请访问位于[JBoss Drools](http://www.jboss.org/drools/documentation)的Drools文档。

​	如果想要使用自己的规则任务实现，比如希望通过不同方法使用Drools，或者想使用完全不同的规则引擎，则可以使用BusinessRuleTask的class或expression属性。这样它会与[服务任务](https://tkjohn.github.io/flowable-userguide/#bpmnJavaServiceTask)的行为完全相同。

​	要执行与流程定义在同一个BAR文件中部署的一条或多条业务规则，需要定义输入与结果变量。输入变量可以用流程变量的列表定义，使用逗号分隔。输出变量只能有一个变量名，将执行业务规则后的输出对象存储至流程变量。请注意结果变量会包含对象的List。如果没有指定结果变量名，默认为org.flowable.engine.rules.OUTPUT。

## 1.5  邮件任务

​	Flowable让你可以通过自动的邮件服务任务（email task），增强业务流程。可以向一个或多个收信人发送邮件，支持cc，bcc，HTML文本，等等。请注意邮件任务**不是**BPMN 2.0规范的“官方”任务（所以也没有专用图标）。因此，在Flowable中，邮件任务实现为一种特殊的服务任务。

## 1.6 Http任务

​	Http任务（Http task）用于**发出HTTP请求**，增强了Flowable的集成能力。请注意Http任务不是BPMN 2.0规范的“官方”任务（所以也没有专用图标）。因此，在Flowable中，Http任务实现为一种特殊的服务任务。

## 1.7 Camel任务

### 1.7.1 Camel任务

​	Camel任务（Camel task）可以向Camel发送消息，增强Flowable的集成特性。请注意Camel任务**不是**BPMN 2.0规范的“官方”任务（所以也没有专用图标）。因此，在Flowable中，Camel任务实现为一种特殊的服务任务。还请注意，需要在项目中包含Flowable Camel模块才能使用Camel任务。

### 1.7.2 连通性测试示例

将试着从Camel接收与发送消息。我们将发送一个字符串，Camel在其上附加一些文字并返回作为结果。发送部分比较普通，即以变量的格式将信息发送给Camel服务。

## 1.8 手动任务

​	手动任务（manual task）定义在BPM引擎之外的任务。它用于建模引擎不需要了解，也不需要提供系统或用户界面的工作。对于引擎来说，手动任务将按**直接穿过活动**处理，在流程执行到达手动任务时，自动继续执行流程。

## 1.9  Java接收任务

​	接收任务（receive task），是等待特定消息到达的简单任务。目前，我们只为这个任务实现了Java语义。当流程执行到达接收任务时，流程状态将提交至持久化存储。这意味着流程将保持等待状态，直到引擎接收到特定的消息，触发流程穿过接收任务继续执行。

​	要使流程实例从接收任务的等待状态中继续执行，需要使用到达接收任务的执行id，调用*runtimeService.signal(executionId)*。

### 1.10 Shell任务

​	Shell任务（Shell task）可以运行Shell脚本与命令。

​	将会运行"cat /etc/passwd | grep root" Shell脚本，等待其结束，并将其结果存入*resultVar*。

## 1.11 执行监听器

​	执行监听器（execution listener）可以在流程执行中发生特定的事件时，执行外部Java代码或计算表达式。可以被捕获的事件有：

- 流程实例的启动和结束。
- 流程执行转移。
- 活动的启动和结束。
- 网关的启动和结束。
- 中间事件的启动和结束。
- 启动事件的结束，和结束事件的启动。

## 1.12 任务监听器

​	任务监听器（task listener）用于在特定的任务相关事件发生时，执行自定义的Java逻辑或表达式。

任务监听器只能在流程定义中作为[用户任务](https://tkjohn.github.io/flowable-userguide/#bpmnUserTask)的子元素。请注意，任务监听器是一个Flowable自定义结构，因此也需要作为*BPMN 2.0 extensionElements*，放在*flowable*命名空间下。

*任务监听器*包含下列属性：

- event（事件）

  （必填）：触发任务监听器的任务事件类型。可用的事件有：

  - **create（创建）**：当任务已经创建，并且**所有任务参数都已经设置**时触发。
  - **assignment（指派）**：当任务已经指派给某人时触发。请注意：当流程执行到达用户任务时，在触发*create*事件**之前**，会首先触发*assignment*事件。这顺序看起来不太自然，但是有实际原因的：当收到*create*事件时，我们通常希望能看到任务的所有参数，包括办理人。
  - **complete（完成）**：当任务已经完成，从运行时数据中删除前触发。
  - **delete（删除）**：在任务即将被删除前触发。请注意任务由completeTask正常完成时也会触发。

- **class**：需要调用的委托类。这个类必须实现`org.flowable.engine.delegate.TaskListener`接口。

- **expression**：（不能与*class*属性一起使用）：指定在事件发生时要执行的表达式。可以为被调用的对象传递`DelegateTask`对象与事件名（使用`task.eventName`）作为参数。

- **delegateExpression**：指定一个能够解析为`TaskListener`接口实现类的对象的表达式。[与服务任务类似](https://tkjohn.github.io/flowable-userguide/#bpmnJavaServiceTaskXML)。

- 较早之前，我们也引入了新的执行监听器类型，org.flowable.engine.impl.bpmn.listener.ScriptTaskListener。这个脚本任务监听器可以为一个任务监听器事件执行一段脚本代码。

  ```hxml
   
     
       
        def bar = "BAR";  // local variable
        foo = "FOO"; // pushes variable to execution context
        task.setOwner("kermit"); // test access to task instance
        bar // implicit return value
       
     
     
     
   
  ```

## 1.13 多实例

​	实例活动（multi-instance activity）是在业务流程中，为特定步骤定义重复的方式。在编程概念中，多实例类似**for each**结构：可以为给定集合中的每一条目，**顺序或并行地**，执行特定步骤，甚至是整个子流程。

*多实例*是一个普通活动，加上定义（被称作“*多实例*特性的”）额外参数，会使得活动在运行时被多次执行。下列活动可以成为*多实例活动：*

- [用户任务](https://tkjohn.github.io/flowable-userguide/#bpmnUserTask)
- [脚本任务](https://tkjohn.github.io/flowable-userguide/#bpmnScriptTask)
- [Java服务任务](https://tkjohn.github.io/flowable-userguide/#bpmnJavaServiceTask)
- [Web服务任务](https://tkjohn.github.io/flowable-userguide/#bpmnWebserviceTask)
- [业务规则任务](https://tkjohn.github.io/flowable-userguide/#bpmnBusinessRuleTask)
- [邮件任务](https://tkjohn.github.io/flowable-userguide/#bpmnEmailTask)
- [人工任务](https://tkjohn.github.io/flowable-userguide/#bpmnManualTask)
- [接收任务](https://tkjohn.github.io/flowable-userguide/#bpmnReceiveTask)
- [（嵌入式）子流程](https://tkjohn.github.io/flowable-userguide/#bpmnSubProcess)
- [调用活动](https://tkjohn.github.io/flowable-userguide/#bpmnCallActivity)

[网关](https://tkjohn.github.io/flowable-userguide/#bpmnGateways)与[事件](https://tkjohn.github.io/flowable-userguide/#bpmnEvents)**不能**设置为多实例。

按照BPMN2.0规范的要求，用于为每个实例创建执行的父执行，会提供下列变量：

- **nrOfInstances**：实例总数。
- **nrOfActiveInstances**：当前活动的（即未完成的），实例数量。对于顺序多实例，这个值总为1。
- **nrOfCompletedInstances**：已完成的实例数量。

可以调用`execution.getVariable(x)`方法获取这些值。

另外，每个被创建的执行，都有局部变量（对其他执行不可见，也不存储在流程实例级别）：

- **loopCounter**：给定实例在*for-each循环中的index*。可以通过Flowable的**elementIndexVariable**属性为loopCounter变量重命名。



## 1.14 补偿处理器

​	如果要使用一个活动补偿另一个活动的影响，可以将其声明为*补偿处理器（compensation handler）*。补偿处理器不在正常流程中执行，而只在流程抛出补偿事件时才会执行。

​	补偿处理器不得有入口或出口顺序流。

​	补偿处理器必须通过单向的连接，关联一个补偿边界事件。

​	中间补偿事件抛出**补偿事件**给对应的（activityRef指定的节点）节点的**补偿处理程序**处理。

# 2、流程图

- 用户任务

![](./images/usertask.png)

- 脚本任务

![](./images/scripttask.png)

- 服务任务

![](./images/servicetask.png)

- 服务任务异常处理

![](./images/exceptionsericetask.png)

- 业务规则任务

![](./images/businessruletask.png)

- 邮件任务

![](./images/mailtask.png)

- Http任务

![](./images/httptask.png)

- Camel任务


![](./images/cameltask.png)



- 手动任务

![](./images/manualtaskprocess.png)

- Java接收任务

![](./images/receivetask.png)

- Shell任务

![](./images/shelltask.png)

- 执行监听器

![](./images/executionlistener.png)

- 任务监听器

![](./images/tasklistener.png)

- 多实例

![](./images/multiinstace.png)

- 补偿处理器

![](./images/compensationhandler.png)



# 3、配置

## 3.1 用户任务

**fakeLdapService必须是spring 中的bean**

```xml
 
 
```

Groovy脚本引擎与groovy-all JAR捆绑在一起，必须引入相关依赖:

```xml
 
		 org.codehaus.groovy 
		 groovy-all 
		 2.5.4 
		 pom 
 
```



## 3.2 脚本任务



## 3.3 服务任务

- spring bean配置详见flowable-context.xml：


```xml
 
 	 
 	 
 	 
 	 
 	 
```

- 发生异常时，将流程执行路由至另一条路径:

```xml
  
      
      
      
```

```java
public class ThrowsExceptionBehavior implements ActivityBehavior {
	private static final long serialVersionUID = 1L;

	public void execute(DelegateExecution execution) {
		System.out.println("====发生异常时，将流程执行路由至另一条出线继续执行==");
		String var = (String) execution.getVariable("exception");

		String sequenceFlowToTake = null;
		try {
			executeLogic(var);
			sequenceFlowToTake = "no-exception";
		} catch (Exception e) {
			sequenceFlowToTake = "exception";
		}
		DelegateHelper.leaveDelegate(execution, sequenceFlowToTake);
	}

	protected void executeLogic(String value) {
		if (value.equals("throw-exception")) {
			throw new RuntimeException();
		}
	}
}
```



## 3.4 业务规则任务

```xml
  
```



## 3.5 邮件任务

- 在*flowable.cfg.xml*配置文件中设置：

```xml
 
 
 
 
 
 设置-->账户-->开启服务-->POP3/SMTP服务-->开启)" />  
 
```

## 3.6 Http任务

### 3.6.1 添加flowable-http依赖

Http任务的默认行为类是org.flowable.http.impl.HttpActivityBehaviorImpl，此类在flowable-http中。

```xml
 
     org.flowable 
     flowable-http 
     6.4.0 
 
```

### 3.6.2 创建自定义Http任务行为类

​	也可以使用自定义的实现，覆盖Http任务的默认行为。 需要扩展org.flowable.http.HttpActivityBehavior，并覆盖perform()方法。

​	**详见源码DefaultActivityBehaviorFactory中createHttpActivityBehavior方法解析field name为httpActivityBehaviorClass，并利用反射实例化此类。**

```xml
 
   
     
         
           
         
     
   
 	
```

### 3.6.2 配置Http客户端

```xml
 
...
	 
	 
 
     
     
     
     
 
```

## 3.7 Camel任务

### 3.7.1 camelContext配置

详见generic-camel-flowable-context.xml文件

```xml
 
	     
	    	 com.study.demo.camel 
	  	 
 
```

### 3.7.2 引入camel依赖包

```xml
 
     org.flowable 
     flowable-camel 
     6.4.0 
 
```
### 3.7.3 路由及Endpoint 配置

字符串"world"会在结尾连接上名为“input”的参数，并存储在camelBody变量中；

```java
public class SimpleCamelCallRoute extends RouteBuilder{

	@Override
	public void configure() throws Exception {
		from("flowable:camelprocess:simpleCall").transform().simple("${property.input} World");
		
	}

}
```

## 3.8 手动任务



## 3.9 Java接收任务

### 3.10 Shell任务

## 3.11 执行监听器

## 3.12 任务执行器

## 3.13 多实例

- 多实例配置及完成条件动态指定:

```xml
 
       
         ${mulitiInstance.completeTask(execution)} 
       
 
```

```java
public class MulitiInstanceCompleteCondition {
	public boolean completeTask(DelegateExecution execution) {
		FlowElement flowElement = execution.getCurrentFlowElement();
		System.out.println("总的任务数量：" + execution.getVariable("nrOfInstances") + "当前获取的任务数量："
				+ execution.getVariable("nrOfActiveInstances") + " - " + "已经完成的会签任务数量："
				+ execution.getVariable("nrOfCompletedInstances"));

		System.out.println("=======【当前节点：】========" + flowElement.getName());
		// isComplete为true,直接完成
		String isComplete = execution.getVariable("isComplete").toString();
		
		if ("true".equals(isComplete)) {
			return true;
		}
		return false;
	}
}
```



### 3.13.1 流程定义包含了六个执行监听器：

- 流程启动的时候执行监听器，实现接口ExecutionListener：

  ```java
  public class ExampleExecutionListenerOne implements ExecutionListener {
  
  	/**
  	 * 
  	 */
  	private static final long serialVersionUID = 1L;
  
  	public void notify(DelegateExecution execution) {
          System.out.println("=========================执行器,流程启动时执行=========================");
  		execution.setVariable("variableSetInExecutionListener", "firstValue");
  		execution.setVariable("eventNameReceived", execution.getEventName());
  		execution.setVariable("businessKeyInExecution", execution.getProcessInstanceBusinessKey());
  
  	}
  
  }
  ```

- 第一个人工任务节点，开始的时候执行监听器，实现接口ExecutionListener：

  ```java
  public class ExampleExecutionListenerTwo implements ExecutionListener {
  
  	/**
  	 * 
  	 */
  	private static final long serialVersionUID = 1L;
  
  	public void notify(DelegateExecution execution) {
  		FlowElement currentFlowElement = DelegateHelper.getFlowElement(execution);
          System.out.println("========================【执行器，当前节点】：" + currentFlowElement.getName()+ "=========================");
          
  		execution.setVariable("variableSetInExecutionListener", "secondValue");
          execution.setVariable("eventNameReceived", execution.getEventName());
          
  	}
  
  }
  ```

- 第二个人工任务节点，结束的时候执行监听器，表达式类型：${myExpression.getEventName(execution.eventName)}

  ```java
  public class MyExpressionExecutionListener {
  
  
  	public String  getEventName(String name) {
  		
  		System.out.println("====================表达式执行监听器,eventName:" + name+"========================");
  		return "expression:" + name ;
  	}
  
  }
  ```


- 第三个人工任务节点，开始的时候执行监听器，委托表达式类型(实现JavaDelegate)：${myDelegateExpression}

  ```java
  public class MyDelegateExpression implements JavaDelegate {
  
  	public void execute(DelegateExecution execution) {
  		FlowElement currentFlowElement = DelegateHelper.getFlowElement(execution);
          System.out.println("=========================【执行器，当前节点】：" + currentFlowElement.getName() + "=========================");
  
  	}
  
  }
  ```


- 第四个人工任务节点，开始的时候执行监听器,脚本类型：ScriptExecutionListener

- 第五个人工任务节点，开始的时候执行监听器,实现接口ExecutionListener：ExampleFieldInjectedExecutionListener

  ```java
  public class ExampleFieldInjectedExecutionListener implements ExecutionListener {
  
  	/**
  	 * 
  	 */
  	private static final long serialVersionUID = 1L;
  
  	private Expression fixedValue;
  	private Expression dynamicValue;
  	public void notify(DelegateExecution execution) {
  		FlowElement currentFlowElement = DelegateHelper.getFlowElement(execution);
          System.out.println("=========================【执行器，当前节点】：" + currentFlowElement.getName() + "=========================");
  		execution.setVariable("dynamicValue", fixedValue.getValue(execution).toString() +
  		dynamicValue.getValue(execution).toString());
  	}
  
  }
  ```


## 3.14 补偿处理器

### 3.14.1 补偿处理器配置：

​	要将一个活动声明为补偿处理器，需要将`isForCompensation`属性设置为true：

```xml
  
```

### 3.14.2 中间补偿事件配置：

​	中间补偿事件抛出补偿事件给对应的（activityRef指定的节点）节点的补偿处理程序处理

```xml
 
	 
 
```



# 4、测试

## 4.1 用户任务--UserTaskTest

- 运行demo
- 查看数据库表

```sql
 SELECT * FROM flowable.ACT_RU_EXECUTION;
 SELECT * FROM flowable.ACT_RU_TASK;
 SELECT * FROM flowable.ACT_RU_VARIABLE;
```

## 4.2 脚本任务--ScriptTaskTest

- 运行demo
- 查看数据库表

```sql
SELECT * FROM flowable.ACT_RU_EXECUTION;
SELECT * FROM flowable.ACT_RU_TASK;
```



## 4.3 服务任务

### ​4.3.1 测试类 ServiceTaskTest

- 线程安全：

​	在运行上面流程定义的流程实例后，*INSTANCE_COUNT*的值为*2*。这是因为每次解析*${prototypeDelegateExpressionBean}*时，都会创建新实例。可以看到三个*Expression*成员字段的注入没有任何问题。

​	在对于单例bean，*INSTANCE_COUNT*总是*1*。在这个委托中，没有*Expression*成员字段（使用*MIXED*模式）。而在*COMPATIBILITY*模式下，就会抛出异常，因为需要有成员字段。这个bean也可以使用*DISABLED*模式，但会禁用上面进行了字段注入的原型bean。

​	单例bean是线程不安全的。

- 发生异常时，将流程执行路由至另一条路径

```xml
  
      
      
      
```

### 4.3.2 测试类 ExceptionForServiceTaskTest

- 服务任务异常处理

  ​	ThrowingDelegate将会抛出BussinessException业务异常，errorcode为localError，Flowable会将`BussinessException`类，转换为带有指定错误代码的BPMN错误，监听在此错误上的边界错误捕获事件会捕获到此异常，并继续后续操作。

## 4.4 业务规则任务--BusinessRuleTaskTest

- 运行demo

- 查看数据库表

## 4.5 邮件任务--MailTaskTest

- 运行demo
- 查看数据库表

## 4.6 Http任务--HttpTaskTest

- 运行demo
- 查看数据库表

## 4.7 Camel任务--CamelTaskTest

- CamelTaskTest测试类说明

  在这个例子里，将试着从Camel接收与发送消息。我们将发送一个字符串，Camel在其上附加一些文字并返回作为结果。发送部分比较普通，即以变量的格式将信息发送给Camel服务。这是我们的调用代码：

```java
	/**
	 * 启动流程实例并测试连通性
	 * 
	 */
	@Test
	public void testPingPong() {
        Map  variables = new HashMap ();

        variables.put("input", "Hello");
        Map  outputMap = new HashMap ();
        variables.put("outputMap", outputMap);

        runtimeService.startProcessInstanceByKey("camelprocess", variables);
        System.out.println("==============outputMap: " + outputMap);
    }
```

​	“input”变量是实际上是Camel路由的输入，而outputMap用于捕获Camel传回的结果。

​	请注意SaveOutput服务任务会从上下文中取出“Output”变量，并存储至上面提到的OutputMap。现在需要		了解变量如何发送至Camel，以及如何返回。这就需要了解Camel行为（Behavior）的概念。变量与Camel通信的方式可以通过CamelBehavior配置。在这个例子里使用默认配置。

- 查看数据库表

```sql
SELECT * FROM flowable.act_ru_task;
SELECT * FROM flowable.act_ru_variable;
```

## 4.8 手动任务--ManualTaskTest

- 运行demo
- 查看数据库表

## 4.9 Java接收任务--ReceiveTaskTest

- 运行demo
- 查看数据库表

### 4.10 Shell任务--ShellTaskTest

​	将会运行"cat /etc/passwd | grep root" Shell脚本，等待其结束，并将其结果存入*resultVar*。

- 运行demo
- 查看数据库表

## 4.11 执行监听器--ExecutionListenerTest

- 运行demo
- 查看数据库表



## 4.12 任务监听器--TaskListenerTest

- 运行demo
- 查看数据库表

## 4.13 多实例--MultilInstanceTest

- 运行demo
- 查看数据库表

## 4.14 补偿处理器--CompensationHandlerTest

- 运行demo
- 查看数据库表

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)