

------

环境：

[jkd8+]()

[mysql5.6+]()

[flowable6.4.0]()



# 1、子流程



##  1.1 描述

*子流程（sub-process）是包含其他的活动、网关、事件等的活动。其本身构成一个流程，并作为更大流程的一部分。子流程完全在父流程中定义（这就是为什么经常被称作嵌入式*子流程）。

子流程有两个主要的使用场景：

- 子流程可以**分层建模**。很多建模工具都可以*折叠*子流程，隐藏子流程的所有细节，而只显示业务流程的高层端到端总览。
- 子流程会创建新的**事件范围**。在子流程执行中抛出的事件可以通过子流程边界上的[边界事件](https://tkjohn.github.io/flowable-userguide/#bpmnBoundaryEvent)捕获，为该事件创建了限制在子流程内的范围。

使用子流程也要注意以下几点：

- 子流程只能有**一个空启动事件**，而不允许有其他类型的启动事件。请注意BPMN 2.0规范允许省略子流程的启动与结束事件，但目前Flowable的实现尚不支持省略。
- **顺序流不能跨越子流程边界。**

## 1.2 示例

### 1.2.1 说明

​		下面的流程模型展示了这种用法：*investigate software（调查硬件）/investigate hardware（调查软件）*两个任务需要并行执行，且需要在给定时限内，在*Level 2 support（二级支持）*响应前完成。在这里，定时器的范围（即需要按时完成的活动）通过子流程进行限制。

### 1.2.2  流程图

![](./images/subprocess.png)

### 1.2.3 测试--SubProcessTest

- 部署

```java
public void deploy() {
		DeploymentBuilder deploymentBuilder = repositoryService
												.createDeployment()
													.category("subprocesstest")
													.name("subprocesstest")
													.addClasspathResource("process/子流程.bpmn20.xml");
		Deployment deploy = deploymentBuilder.deploy();

		System.out.println("流程ID: " + deploy.getId());
	}
```



- 睡眠，以便于定时器执行

```java
	/**
	 * 睡眠5分钟
	 * @throws InterruptedException 
	 */
	@Test
	public void sleep() throws InterruptedException {
		Long millis = 300000L;
		Thread.sleep(millis);
	}
```

- 启动流程实例

```java
	/**
	 * 启动流程实例 
	 * 
	 */
	@Test
	public void start() {
		String processDefinitionKey = "subprocesstest";
    	

        Map  vars = new HashMap ();
		runtimeService.startProcessInstanceByKey(processDefinitionKey,vars);
	}
```

- 查看数据库表

```
SELECT * FROM flowable.act_ru_timer_job;
SELECT * FROM flowable.act_ru_task;
SELECT * FROM flowable.act_ru_execution;
```

- 完成任务

```java
	/**
	 * 完成任务
	 */
	@Test
	public void complete() {
		String taskId = "152505";
		taskService.complete(taskId);
	}
```



# 2、事件子流程 

## 2.1 描述

​	事件子流程（event sub-process）是BPMN 2.0新定义的。事件子流程是通过事件触发的子流程。可以在流程级别，或者任何子流程级别，添加事件子流程。用于触发事件子流程的事件，使用启动事件进行配置。因此可知，不能在事件子流程中使用空启动事件。事件子流程可以通过消息事件、错误事件、信号时间、定时器事件或补偿事件等触发。在事件子流程的宿主范围（流程实例或子流程）创建时，创建对启动事件的订阅。当该范围销毁时，删除订阅。

​	事件子流程可以是中断或不中断的。中断的子流程将取消当前范围内的任何执行。非中断的事件子流程将创建新的并行执行。宿主范围内的每个活动，只能触发一个中断事件子流程，而非中断事件子流程可以多次触发。子流程是否是中断的，通过触发事件子流程的启动事件配置。

​	事件子流程不能有任何入口或出口顺序流。事件子流程是**由事件触发的**，因此入口顺序流不合逻辑。当事件子流程结束时，要么同时结束当前范围（中断事件子流程的情况），要么是非中断子流程创建的并行执行结束。

​	**目前的限制：**

- Flowable支持错误、定时器、信号与消息启动事件触发事件子流程。

## 2.2 示例

### 2.2.1 示例1---	事件子流程处于“流程级别”

下面是使用错误启动事件触发事件子流程的例子。该事件子流程处于“流程级别”，即流程实例的范围：

#### 2.2.1.1 流程图：

![](./images/eventsubprocessInprocess.png)

#### 2.2.1.2 测试--EventSubprocessInProcessTest

- 部署
- 启动流程示例
- 查看数据库

```sql
SELECT * FROM flowable.act_ru_task;
SELECT * FROM flowable.act_ru_execution;
```

- 依次完成任务

### 2.2.2 示例2---事件子流程也可以添加到嵌入式子流程内

事件子流程也可以添加到嵌入式子流程内。若添加到嵌入式子流程内，可以代替边界事件的功能。例如在下面两个流程图中，嵌入式子流程都抛出错误事件。错误事件都被捕获，并由用户任务处理。

#### 2.2.2.1 流程图：

![](./images/eventsubprocessInsubprocess.png)

#### 2.2.2.2 测试--EventSubprocessInSubProcessTest

- 部署
- 启动流程示例
- 查看数据库

```sql
SELECT * FROM flowable.act_ru_task;
SELECT * FROM flowable.act_ru_execution;
```

- 依次完成任务

# 3、事物子流程

## 3.1描述

事务子流程（transaction sub-process）是一种嵌入式子流程，用于将多个活动组织在一个事务里。事务是工作的逻辑单元，可以组织一组独立活动，使得它们可以一起成功或失败。

**事务的可能结果：**事务有三种不同的结果：

- 若未被取消，或被意外终止，则事务*成功(successful)*。若事务子流程成功，将使用出口顺序流离开。若流程后面抛出了补偿事件，成功的事务可以被补偿。*请注意：*与“普通”嵌入式子流程一样，可以使用补偿抛出中间事件，在事务成功完成后补偿。
- 若执行到达取消结束事件时，事务被*取消(canceled)*。在这种情况下，所有执行都将被终止并移除。只会保留一个执行，设置为取消边界事件，并将触发补偿。在补偿完成后，事务子流程通过取消边界事件的出口顺序流离开。
- 若由于抛出了错误结束事件，且未被事务子流程所在的范围捕获，则事务会被*意外(hazard)*终止。错误被事件子流程的边界捕获也一样。在这种情况下，不会进行补偿。

**目前的限制：**

- BPMN规范要求，流程引擎响应底层事务协议提交的事务。如果在底层协议中发生了取消事件，则取消事务。作为嵌入式的引擎，Flowable当前不支持这点。查看下面介绍一致性的段落，了解其后果。

**基于ACID事务与乐观锁（optimistic concurrency）的一致性：**BPMN事务在如下情况保证一致性：所有活动都成功完成；或若部分活动不能执行，则所有已完成活动都被补偿。两种方法都可以达到最终一致性状态。然而需要了解的是：Flowable中BPMN事务的一致性模型，以流程执行的一致性模型为基础。Flowable以事务的方式执行流程，并通过乐观锁标记处理并发。在Flowable中，BPMN的错误、取消与补偿事件，都建立在相同的ACID事务与乐观锁之上。例如，只有在实际到达时，取消结束事件才能触发补偿。如果服务任务抛出了非受检异常，导致并未实际到达取消结束事件；或者，由于底层ACID事务中的其他操作，将事务设置为rollback-only（回滚）状态，导致补偿处理器的操作不能提交；或者，当两个并行执行到达一个取消结束事件时，补偿会被两次触发，并由于乐观锁异常而失败。这些情况下都不能真正完成补偿。想说明的是，当在Flowable中实现BPMN事务时，与实施“普通”流程与子流程，需要遵守相同的规则。因此实现流程时需要有效地保证一致性，需要将乐观锁、事务执行模型纳入考虑范围。

## 3.2 示例

​	下面的流程图展示这三种不同的结果：

![](./images/transationsubprocess.png)

## 3.3 测试--TransationSubProcessTest

- 部署
- 启动流程示例
- 查看数据库

# 4、调用活动（子流程）

## 4.1描述

​	尽管看起来很相像，但在BPMN 2.0中，调用活动（call activity）有别于一般的*子流程*——通常也称作*嵌入式子流程*。从概念上说，两者都在流程执行到达该活动时，调用一个子流程。

​	两者的区别为，调用活动引用一个流程定义外部的流程，而*子流程*嵌入在原有流程定义内。调用活动的主要使用场景是，在多个不同流程定义中调用一个可复用的流程定义。

​	当流程执行到达*调用活动*时，会创建一个新的执行，作为到达调用活动的执行的子执行。这个子执行用于执行子流程，也可用于创建并行子执行（与普通流程中行为类似）。父执行将等待子流程完成，之后沿原流程继续执行。

## 4.2 引用同一部署中的流程

​	默认会使用引用流程最后部署的流程定义版本。但有的时候也会想引用与主流程一起部署的引用流程定义。这需要将主流程与引用流程放在同一个部署单元中，以便引用相同的部署。

在`callActivity`元素中，将`sameDeployment`属性设置为`true`，即可引用相同部署的流程。

​	如下例所示：

```x&#39;m
 
...
 
```

`sameDeployment`默认值为false。

## 4.3 传递变量

可以向子流程传递与接收流程变量。数据将在子流程启动时复制到子流程，并在其结束时复制回主流程。

```xml
 
     
         
         
     
 
```

也可以通过将选项设置`inheritVariables`为true 将所有流程变量传递给子流程。

```xml
 
```

## 4.4 流程图

主流程：

![](./images/callacititiedofmainprocess.png)

子流程：

![](./images/callacititiedofsubprocess.png)

## 4.5 测试--CallActivitiesTest

- 注意：

​	本例采用 【引用同一部署中的流程】方式同时部署主流程和子流程；

​	inheritVariables`为true 将所有流程变量传递给子流程。

- 部署
- 启动流程示例
- 查看数据库

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)