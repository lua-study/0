# 微服务神经元(Neural)

[TOC]

	     
     
         QQ交流群： 191958521 (微服务基础设施) 
         微信交流群： echo-lry (加我个人微信，备注拉群要求) 
         微信公众号： 蚂蚁技术栈  
     
     &nbsp; 
     
           
           
           
     
 r
    - T max = b/(M-r) 承受最大传输速率的时间
    - B max = T max * M 承受最大传输速率的时间内传输的流量

**优点**：流量比较平滑，并且可以抵挡一定的流量突发情况


## 3 熔断（CircuitBreaker）
在分布式架构中，熔断的场景主要分为两种：injvm模式和cluster模式。

### 3.1事件统计熔断器（EventCountCircuitBreaker）
在指定时间周期内根据事件发生的次数来实现精简版熔断器。如10秒之内触发5次事件，则进行熔断。

### 3.2 门限熔断器（ThresholdCircuitBreaker）
TODO


## 4 降级（Degrade）（待完成）
服务降级是指当服务器压力剧增时，根据当前业务情况及流量对一些服务和页面有策略的降级，以此缓解了服务器资源压力，以保证核心任务的正常运行，同时也保证了部分甚至大部分客户得到正确响应。

### 4.1 管理方式
#### 4.1.1 直接管理方式：运维人员可以指定哪些模块降级
当服务器检测到压力增大，服务器监测自动发送通知给运维人员，运维人员根据自己或相关人员判断后通过配置平台设置当前运行等级来降级。降级首先可以对非核心业务进行接口降级。如果效果不显著，开始对一些页面进行降级，以此保证核心功能的正常运行。

#### 4.1.2 分级管理方式：运维人员无需关心业务细节，直接按级别降低即可
业务确定好对应业务的优先级别，指定好分级降级方案。当服务器检测到压力增大，服务检测自动发送通知给运维人员。运维人员根据情况选择运行等级。


## 5 重试（Retryer）
### 5.1 重试策略
#### 5.1.1 块策略（BlockStrategy）
使当前线程使用Thread.sleep()的方式进行休眠重试。

#### 5.1.2 停止策略（StopStrategy）

- **NeverStopStrategy**：从不停止策略
- **StopAfterAttemptStrategy**：尝试后停止策略
- **StopAfterDelayStrategy**：延迟后停止策略

#### 5.1.3 等待策略（WaitStrategy）

- **FixedWaitStrategy**：固定休眠时间等待策略
- **RandomWaitStrategy**：随机休眠时间等待策略，支持设置随机休眠时间的下限值（minmum）与上限值（maxmum）
- **IncrementingWaitStrategy**：定长递增休眠时间等待策略
- **ExponentialWaitStrategy**：指数函数（2^x，其中x表示尝试次数）递增休眠时间等待策略。支持设置休眠时间的上限值（maximumWait）
- **FibonacciWaitStrategy**：斐波那契数列递增休眠时间等待策略。支持设置休眠时间的上限值（maximumWait）
- **CompositeWaitStrategy**：复合等待策略，即支持以上等待策略的组合计算休眠时间，最终休眠时间是以上策略中休眠时间之和
- **ExceptionWaitStrategy**：异常等待策略

### 5.2 指定结果重试
**retryIfResult(Predicate  resultPredicate)**：设置重试不满足条件的结果

eg：如果返回结果为空则重试：retryIfResult(Predicates. isNull())

### 5.3 指定异常重试

- **retryIfException()**：重试所有异常
- **retryIfRuntimeException()**：重试运行时异常
- **retryIfExceptionOfType(Class  exceptionClass)**：重试指定类型异常
- **retryIfException(Predicate  exceptionPredicate)** ：自定义过滤后的异常重试

### 5.4 重试监听器（RetryListener）
**withRetryListener(RetryListener listener)**：添加重试监听器

### 5.5 尝试时间限制器（AttemptTimeLimiter）
**withAttemptTimeLimiter(AttemptTimeLimiter  attemptTimeLimiter)**：添加尝试时间限制器

## 6 JWT（JSON Web Token）
功能来源于java-jwt项目，但有一定的调整，后续会继续简化。

## 7 过滤器（Filter）
基于@NPI扩展方式和责任链模式实现的过滤器机制。

## 8 黑科技（Micro）
- **Perf**：性能测试工具
- **IPFilter**：IP黑白名单过滤器
- **SystemClock**：解决大并发场景中获取System.currentTimeMillis()的性能问题
- **Snowflake**：基于Snowflake算法实现的高性能Long型ID生成器。理论QPS > 400w/s
- **NUUID**：UUID扩展版。支持36/32/22/19位的UUID生成方式(不牺牲精度)，支持牺牲一定精度后的15位超短UUID




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)