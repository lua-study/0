[上一篇：Spring Boot 整合 RocketMq](https://www.jianshu.com/p/8c4c2c2ab62e)

# RocketMq消息监听程序消除大量的if..else

承接上一篇文章，如果消费端订阅了多个topic和tag,则需要在消息监听器类中添加if..else，根据topic和tag处理不同的业务逻辑，使得消息监听类职责过重。

## 大概思路
消息监听器类只负责监听消息，获取到消息后通过topic和tag路由到需要调用的服务，消费者只需要编写对应的topic和tag的服务。

为了监听器类可以通过topic和tag路由到需要调用的服务，自定义一个消费者注解MQConsumeService（该注解包含topic和tag的定义），消费者实现类上添加该注解，然后就可以在监听器类中通过反射获取到实现类上面注解的topic和tag，和监听到的topic和tag比较，如果相同则调用该服务。

## 定义MQConsumeService注解

```
package com.clouds.common.rocketmq.annotation;

import java.lang.annotation.Documented;
import java.lang.annotation.ElementType;
import java.lang.annotation.Retention;
import java.lang.annotation.RetentionPolicy;
import java.lang.annotation.Target;

import org.springframework.stereotype.Service;

import com.clouds.common.rocketmq.TopicEnum;


/**
 * 此注解用于标注消费者服务
 * . 
 * 
 * Copyright: Copyright (c) 2017  zteits
 * 
 * @ClassName: MQConsumeService
 * @Description: 
 * @version: v1.0.0
 * @author: zhaowg
 * @date: 2018年3月2日 下午1:15:52
 * Modification History:
 * Date             Author          Version            Description
 *---------------------------------------------------------*
 * 2018年3月2日      zhaowg           v1.0.0               创建
 */
@Documented
@Retention(RetentionPolicy.RUNTIME)
@Target({ElementType.TYPE})
@Service
public @interface MQConsumeService {
    /**
     * 消息主题
     */
     TopicEnum topic();

    /**
     * 消息标签,如果是该主题下所有的标签，使用“*”
     */
     String[] tags();


}

```


## 定义消费者返回消息Bean

```
package com.clouds.common.rocketmq.consumer.processor;

import java.io.Serializable;
/**
 * 消费结果
 * . 
 * 
 * Copyright: Copyright (c) 2017  zteits
 * 
 * @ClassName: MQConsumeResult
 * @Description: 
 * @version: v1.0.0
 * @author: zhaowg
 * @date: 2018年3月1日 上午11:12:55
 * Modification History:
 * Date             Author          Version            Description
 *---------------------------------------------------------*
 * 2018年3月1日      zhaowg           v1.0.0               创建
 */
public class MQConsumeResult implements Serializable{

	private static final long serialVersionUID = 1L;
	/**
	 * 是否处理成功
	 */
	private boolean isSuccess;
	/**
	 * 如果处理失败，是否允许消息队列继续调用，直到处理成功，默认true
	 */
	private boolean isReconsumeLater = true;
	/**
	 * 是否需要记录消费日志，默认不记录
	 */
	private boolean isSaveConsumeLog = false;
	/**
	 * 错误Code
	 */
	private String errCode;
	/**
	 * 错误消息
	 */
	private String errMsg;
	/**
	 * 错误堆栈
	 */
	private Throwable e;
	
	//省略set和get方法
}
```


## 定义统一的消息处理接口

```
package com.clouds.common.rocketmq.consumer.processor;

import java.util.List;

import com.alibaba.rocketmq.common.message.MessageExt;

/**
 * 消息队列-消息消费处理接口
 * . 
 * 
 * Copyright: Copyright (c) 2017  zteits
 * 
 * @ClassName: MQMsgProcessorService
 * @Description: 
 * @version: v1.0.0
 * @author: zhaowg
 * @date: 2018年3月1日 上午9:57:57
 * Modification History:
 * Date             Author          Version            Description
 *---------------------------------------------------------*
 * 2018年3月1日      zhaowg           v1.0.0               创建
 */
public interface MQMsgProcessor {
	/**
	 * 消息处理 
	 * 如果没有return true ，consumer会重新消费该消息，直到return true 
	 * consumer可能重复消费该消息，请在业务端自己做是否重复调用处理，该接口设计为幂等接口
	 * @param topic 消息主题
	 * @param tag 消息标签
	 * @param msgs 消息
	 * @return
	 * 2018年3月1日 zhaowg
	 */
	MQConsumeResult handle(String topic, String tag, List  msgs);
}

```
## 定义抽象类实现上面的MQMsgProcessor接口

```
package com.clouds.common.rocketmq.consumer.processor;

import java.util.Arrays;
import java.util.List;

import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

import com.alibaba.rocketmq.common.message.MessageConst;
import com.alibaba.rocketmq.common.message.MessageExt;
/**
 * 所有消息处理继承该类
 * . 
 * 
 * Copyright: Copyright (c) 2017  zteits
 * 
 * @ClassName: AbstractMQMsgProcessorService
 * @Description: 
 * @version: v1.0.0
 * @author: zhaowg
 * @date: 2018年3月1日 上午11:14:25
 * Modification History:
 * Date             Author          Version            Description
 *---------------------------------------------------------*
 * 2018年3月1日      zhaowg           v1.0.0               创建
 */
public abstract class AbstractMQMsgProcessor implements MQMsgProcessor{
	
	protected static final Logger logger = LoggerFactory.getLogger(AbstractMQMsgProcessor.class);
    
	@Override
	public MQConsumeResult handle(String topic, String tag, List  msgs) {
		MQConsumeResult mqConsumeResult = new MQConsumeResult();
		/**可以增加一些其他逻辑*/
		
		for (MessageExt messageExt : msgs) {
			//消费具体的消息，抛出钩子供真正消费该消息的服务调用
			mqConsumeResult = this.consumeMessage(tag,messageExt.getKeys()==null?null:Arrays.asList(messageExt.getKeys().split(MessageConst.KEY_SEPARATOR)),messageExt);
		}
		
		/**可以增加一些其他逻辑*/
		return mqConsumeResult;
	}
	/**
	 * 消息某条消息
	 * @param tag 标签
	 * @param keys 消息关键字
	 * @param messageExt
	 * @return
	 * 2018年3月1日 zhaowg
	 */
	protected abstract MQConsumeResult consumeMessage(String tag,List  keys, MessageExt messageExt);

}

```
## 修改后的消费者监听器类

```
package com.clouds.common.rocketmq.consumer.processor;

import java.util.Arrays;
import java.util.List;
import java.util.Map;
import java.util.Map.Entry;
import java.util.stream.Collectors;

import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Component;
import org.springframework.util.CollectionUtils;

import com.alibaba.fastjson.JSON;
import com.alibaba.rocketmq.client.consumer.listener.ConsumeConcurrentlyContext;
import com.alibaba.rocketmq.client.consumer.listener.ConsumeConcurrentlyStatus;
import com.alibaba.rocketmq.client.consumer.listener.MessageListenerConcurrently;
import com.alibaba.rocketmq.common.message.MessageExt;
import com.clouds.common.rocketmq.annotation.MQConsumeService;
import com.clouds.common.rocketmq.constants.RocketMQErrorEnum;
import com.clouds.common.rocketmq.exception.AppException;
import com.clouds.common.rocketmq.exception.RocketMQException;
/**
 * 消费者消费消息路由
 * . 
 * 
 * Copyright: Copyright (c) 2017  zteits
 * 
 * @ClassName: RocketMQMessageListenerConcurrentlyProcessor
 * @Description: 
 * @version: v1.0.0
 * @author: zhaowg
 * @date: 2018年2月28日 上午11:12:32
 * Modification History:
 * Date             Author          Version            Description
 *---------------------------------------------------------*
 * 2018年2月28日      zhaowg           v1.0.0               创建
 */
@Component
public class MQConsumeMsgListenerProcessor implements MessageListenerConcurrently{
	private static final Logger logger = LoggerFactory.getLogger(MQConsumeMsgListenerProcessor.class);
    @Autowired
    private Map  mqMsgProcessorServiceMap;
	/**
	 *  默认msgs里只有一条消息，可以通过设置consumeMessageBatchMaxSize参数来批量接收消息 
	 *  不要抛异常，如果没有return CONSUME_SUCCESS ，consumer会重新消费该消息，直到return CONSUME_SUCCESS
	 */
	@Override
	public ConsumeConcurrentlyStatus consumeMessage(List  msgs, ConsumeConcurrentlyContext context) {
		if(CollectionUtils.isEmpty(msgs)){
			logger.info("接受到的消息为空，不处理，直接返回成功");
			return ConsumeConcurrentlyStatus.CONSUME_SUCCESS;
		}
		ConsumeConcurrentlyStatus concurrentlyStatus = ConsumeConcurrentlyStatus.CONSUME_SUCCESS;
		try{
			//根据Topic分组
			Map > topicGroups = msgs.stream().collect(Collectors.groupingBy(MessageExt::getTopic));
			for (Entry > topicEntry : topicGroups.entrySet()) {
				String topic = topicEntry.getKey();
				//根据tags分组
				Map > tagGroups = topicEntry.getValue().stream().collect(Collectors.groupingBy(MessageExt::getTags));
				for (Entry > tagEntry : tagGroups.entrySet()) {
					String tag = tagEntry.getKey();
					//消费某个主题下，tag的消息
					this.consumeMsgForTag(topic,tag,tagEntry.getValue());
				}
			}
		}catch(Exception e){
			logger.error("处理消息失败",e);
			concurrentlyStatus = ConsumeConcurrentlyStatus.RECONSUME_LATER;
		}
        // 如果没有return success ，consumer会重新消费该消息，直到return success
        return concurrentlyStatus;
	}
	/**
	 * 根据topic 和 tags路由，查找消费消息服务
	 * @param topic
	 * @param tag
	 * @param value
	 * 2018年3月1日 zhaowg
	 */
	private void consumeMsgForTag(String topic, String tag, List  value) {
		//根据topic 和  tag查询具体的消费服务
		MQMsgProcessor imqMsgProcessor = selectConsumeService(topic, tag);
		
		try{
			if(imqMsgProcessor==null){
				logger.error(String.format("根据Topic：%s和Tag:%s 没有找到对应的处理消息的服务",topic,tag));
				throw new RocketMQException(RocketMQErrorEnum.NOT_FOUND_CONSUMESERVICE);
			}
			logger.info(String.format("根据Topic：%s和Tag:%s 路由到的服务为:%s，开始调用处理消息",topic,tag,imqMsgProcessor.getClass().getName()));
			//调用该类的方法,处理消息
			MQConsumeResult mqConsumeResult = imqMsgProcessor.handle(topic,tag,value);
			if(mqConsumeResult==null){
				throw new RocketMQException(RocketMQErrorEnum.HANDLE_RESULT_NULL);
			}
			if(mqConsumeResult.isSuccess()){
				logger.info("消息处理成功："+JSON.toJSONString(mqConsumeResult));
			}else{
				throw new RocketMQException(RocketMQErrorEnum.CONSUME_FAIL,JSON.toJSONString(mqConsumeResult),false);
			}
			if(mqConsumeResult.isSaveConsumeLog()){
				logger.debug("开始记录消费日志");
				//TODO 记录消费日志
			}
		}catch(Exception e){
			if(e instanceof AppException){
				AppException mqe = (AppException)e;
				//TODO 记录消费失败日志
				throw new AppException(mqe.getErrCode(),mqe.getErrMsg(),false); 
			}else{
				//TODO 记录消费失败日志
				throw e;
			}
		}
	}
	/**
	 * 根据topic和tag查询对应的具体的消费服务
	 * @param topic
	 * @param tag
	 * @return
	 * 2018年3月3日 zhaowg
	 */
	private MQMsgProcessor selectConsumeService(String topic, String tag) {
		MQMsgProcessor imqMsgProcessor = null;
		for (Entry  entry : mqMsgProcessorServiceMap.entrySet()) {
			//获取service实现类上注解的topic和tags
			MQConsumeService consumeService = entry.getValue().getClass().getAnnotation(MQConsumeService.class);
			if(consumeService == null){
				logger.error("消费者服务："+entry.getValue().getClass().getName()+"上没有添加MQConsumeService注解");
				continue;
			}
			String annotationTopic = consumeService.topic().getCode();
			if(!annotationTopic.equals(topic)){
				continue;
			}
			String[] tagsArr = consumeService.tags();
			//"*"号表示订阅该主题下所有的tag
			if(tagsArr[0].equals("*")){
				//获取该实例
				imqMsgProcessor = entry.getValue();
				break;
			}
			boolean isContains = Arrays.asList(tagsArr).contains(tag);
			if(isContains){
				//获取该实例
				imqMsgProcessor = entry.getValue();
				break;
			}
		}
		return imqMsgProcessor;
	}

}
```
至此，通过topic和tag路由服务已经写完了，现在以新增订阅一个DemoTopic主题为例，编写消息接受方。

## 新建消费者类，继承AbstractMQMsgProcessor类
> 注意：该类必须继承AbstractMQMsgProcessor，且添加MQConsumeService注解，用于定义该类是针对那个topic和tag的消费服务。新增订阅主题，还需要在application.propertis中修改rocketmq.consumer.topics。


```
package com.clouds.common.demo;

import java.util.List;

import com.alibaba.rocketmq.common.message.MessageExt;
import com.clouds.common.rocketmq.TopicEnum;
import com.clouds.common.rocketmq.annotation.MQConsumeService;
import com.clouds.common.rocketmq.consumer.processor.AbstractMQMsgProcessor;
import com.clouds.common.rocketmq.consumer.processor.MQConsumeResult;

@MQConsumeService(topic=TopicEnum.DemoTopic,tags={"*"})
public class DemoNewTopicConsumerMsgProcessImpl extends AbstractMQMsgProcessor{

	@Override
	protected MQConsumeResult consumeMessage(String tag, List  keys, MessageExt messageExt) {
		String msg = new String(messageExt.getBody());
		logger.info("获取到的消息为："+msg);
		//TODO 判断该消息是否重复消费（RocketMQ不保证消息不重复，如果你的业务需要保证严格的不重复消息，需要你自己在业务端去重）
		
		//如果注解中tags数据中包含多个tag或者是全部的tag(*)，则需要根据tag判断是那个业务，
		//如果注解中tags为具体的某个tag，则该服务就是单独针对tag处理的
		if(tag.equals("某个tag")){
			//做某个操作
		}
		//TODO 获取该消息重试次数
		int reconsume = messageExt.getReconsumeTimes();
		//根据消息重试次数判断是否需要继续消费
		if(reconsume ==3){//消息已经重试了3次，如果不需要再次消费，则返回成功
			
		}
		MQConsumeResult result = new MQConsumeResult();
		result.setSuccess(true);
		return result;
	}

}

```


```
rocketmq.consumer.topics=DemoTopic~*;
```

## 运行测试类观察日志

```

  .   ____          _            __ _ _
 /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
 \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
  '  |____| .__|_| |_|_| |_\__, | / / / /
 =========|_|==============|___/=/_/_/_/
 :: Spring Boot ::        (v1.5.2.RELEASE)

2018-03-03 16:54:25.079  INFO 12496 --- [           main] c.c.c.SpringBootRocketMqApplication      : Starting SpringBootRocketMqApplication on DESKTOP-HS6GR38 with PID 12496 (D:\wsforjava\springboot-rocketmq\target\classes started by suolo in D:\wsforjava\springboot-rocketmq)
2018-03-03 16:54:25.086  INFO 12496 --- [           main] c.c.c.SpringBootRocketMqApplication      : No active profile set, falling back to default profiles: default
2018-03-03 16:54:25.201  INFO 12496 --- [           main] s.c.a.AnnotationConfigApplicationContext : Refreshing org.springframework.context.annotation.AnnotationConfigApplicationContext@236e3f4e: startup date [Sat Mar 03 16:54:25 CST 2018]; root of context hierarchy
2018-03-03 16:54:27.073  INFO 12496 --- [           main] c.c.c.r.p.MQProducerConfiguration        : producer is start ! groupName:[springboot-rocketmq],namesrvAddr:[47.97.8.22:9876]
2018-03-03 16:54:27.430  INFO 12496 --- [           main] c.c.c.r.c.MQConsumerConfiguration        : consumer is start !!! groupName:springboot-rocketmq,topics:DemoTopic~*;,namesrvAddr:47.97.8.22:9876
2018-03-03 16:54:27.747  INFO 12496 --- [           main] o.s.j.e.a.AnnotationMBeanExporter        : Registering beans for JMX exposure on startup
2018-03-03 16:54:27.764  INFO 12496 --- [           main] c.c.c.SpringBootRocketMqApplication      : Started SpringBootRocketMqApplication in 3.213 seconds (JVM running for 3.814)
2018-03-03 16:54:27.784  INFO 12496 --- [MessageThread_1] .c.c.r.c.p.MQConsumeMsgListenerProcessor : 根据Topic：DemoTopic和Tag:DemoTag 路由到的服务为:com.clouds.common.demo.DemoNewTopicConsumerMsgProcessImpl，开始调用处理消息
2018-03-03 16:54:30.162  INFO 12496 --- [MessageThread_1] c.c.c.r.c.p.AbstractMQMsgProcessor       : 获取到的消息为：demo msg test
2018-03-03 16:54:30.194  INFO 12496 --- [MessageThread_1] .c.c.r.c.p.MQConsumeMsgListenerProcessor : 消息处理成功：{"reconsumeLater":true,"saveConsumeLog":false,"success":true}

```

## 项目源码
https://gitee.com/zhaowg3/springboot-rocketmq/tree/master/



完成。



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)