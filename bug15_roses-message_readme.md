# roses-message 消息中心（分布式事务解决方案，可靠消息最终一致性）

---
   
## 介绍
本项目为Roses系列微服务框架的模块之一，Roses基于`Spring Boot 2`和`Spring Cloud Finchley.RELEASE`，致力做更简洁的**分布式**和**服务化**解决方案，Roses拥有高效率的开发体验，提供可靠消息最终一致性分布式事务解决方案，提供基于调用链的服务治理，提供可靠的服务异常定位方案（Log + Trace）等等，**一个分布式框架不仅需要构建高效稳定的底层开发框架，更需要解决分布式带来的种种挑战**，请关注Roses微服务框架[https://gitee.com/stylefeng/roses](https://gitee.com/stylefeng/roses)

---

## 本项目模块介绍

| 模块名称 | 说明 | 端口 | 备注 |
| :---: | :---: | :---: | :---: |
| roses-message-service | 消息服务 | 9001 | 可靠消息最终一致性（柔性事务解决方案） | 
| roses-message-checker | 消息恢复和消息状态确认子系统 | 9002 | 可靠消息最终一致性（柔性事务解决方案） |
| roses-example-order | 订单服务 | 9003 | 演示如何解决分布式事务 |
| roses-example-account | 账户服务 | 9004 | 演示如何解决分布式事务 |

---

## 注意事项

> * 开发环境为jdk 1.8
> * maven推荐使用阿里云镜像，拉取jar包保证成功
> * 运行roses-system之前，需要先运行roses-config-server（如果启用分布式配置的话），roses-cloud-register（服务注册发现）
> * 请确数据库url，账号和密码等配置设置正确，如果开启了分布式配置，这些配置都在git配置仓库中，如果没开启请配置本地的application.yml

---

## 启动步骤

> 1. 启动roses-message-service
> 2. 启动roses-message-checker
> 3. 启动roses-example-order
> 4. 启动roses-example-account

---
 
##分布式事务解决方案（可靠消息最终一致性）
首先，分布式事务在不同业务场景下，解决方案是不一样的，时效性要求较高的场景下，例如订单支付成功后，更改订单状态，给用户账户加款，给积分账户加积分，三个操作在三个不同的服务下，这个时候可以用TCC方式解决事务问题；在时效性要求较为不严格下，例如订单支付成功后，需要异步录入会计凭证（不严格要求时效性），这个时候可以用可靠消息最终一致性解决。

Roses中实现了可靠消息最终一致性的解决方案（如上所说第二个例子），TCC方案目前未集成到系统。

### 实现原理
单纯依靠消息队列无法实现消息的可靠投递和消费，所以借助预发送待确认消息，业务执行成功后再发送确认消息来保证消息的可靠投递，并且通过中间服务（消息服务）来控制统一的消息预存储和确认发送，统一执行发送到消息队列的操作，并且消息服务有单独的消息表来记录消息是否已经投递成功。

Roses中roses-message-service为消息服务，为可靠消息最终一致性实现的核心，roses-message-checker为定时任务执行器，每隔一定时间来轮训消息表中是否有消息不一致的数据，若消息不一致则从业务系统中调用接口来查询具体业务的执行状态，从而来更新消息表中的消息。

roses-example-order和roses-example-account两个模块，模拟了分布式事务的场景，首先通过order模块下一个单（/place接口），再执行完成此订单（/finish接口），在完成订单过程中，先调用了预发送消息接口（preSaveMessage），之后执行完业务后调用确认并发送消息（confirmAndSendMessage）。在account模块中有消息的监听器，监听到消息后存储账号交易流水记录（recordFlow）。account和order模块为了演示业务流程用，数据库设计比较简单，不合理处请见谅。
```
//创建预发送消息
ReliableMessage reliableMessage = createMessage(order);

//预发送消息
messageServiceConsumer.preSaveMessage(reliableMessage);

//更新订单为成功状态(百分之50几率失败，模拟错误数据)（此处错误已添加到消息表的数据会被roses-message-checker轮询时删除掉）
updateToSuccess(order);

//确认消息
messageServiceConsumer.confirmAndSendMessage(reliableMessage.getMessageId());
```

### 幂等性校验
消息的投递有重试机制，所以在消息的消费端需要加上幂等性校验，使得多次消费消息也可以让业务实际只执行一次，在account模块中幂等性的判断通过订单号来标识操作的唯一性。

```

//幂等判断
EntityWrapper  wrapper = new EntityWrapper<>();
wrapper.eq("order_id", goodsFlowParam.getId());

List  flowRecords = this.selectList(wrapper);
if (flowRecords != null && !flowRecords.isEmpty()) {
    return;
}
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)