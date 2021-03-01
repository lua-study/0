#activeMQ 
    是学习java消息队列的实现项目，使用jfinal + jfinal-ext + activeMQ + quartz快速构建。

##1.消息队列
    消息队列，其实是一种基于数据结构实现的服务。而java语言中的实现，有apache的activeMQ，比较主流。

##2.环境搭建
    首先去apache的官网下载apache-activeMQ-...-.zip的包，解压后，运行bin中的activeMQ服务。
    在浏览器中输入http://localhost:8186/admin,出现登陆界面输入admin/admin登陆即可。
![](./1.png)
    然后创建一个FirstQueue队列（给后面的实例提供服务）。
    
##3.activeMQ原始操作
    记住activeMQ服务一定要一直开启，发送者和接收者都会通过tcp协议去链接服务器，以取得消息队列中的消息体。
	如下图是我的服务器cmd截图：
![](./4.png)
    
###3.1.首先建立发送者Sender.java
``` java
package com.mg.demo;

import javax.jms.Connection;
import javax.jms.ConnectionFactory;
import javax.jms.DeliveryMode;
import javax.jms.Destination;
import javax.jms.MessageProducer;
import javax.jms.Session;
import javax.jms.TextMessage;

import org.apache.activemq.ActiveMQConnection;
import org.apache.activemq.ActiveMQConnectionFactory;

public class Sender {
    private static final int SEND_NUMBER = 5;

	public static void main(String[] args) {
		// ConnectionFactory ：连接工厂，JMS 用它创建连接
		ConnectionFactory connectionFactory; 
		// Connection ：JMS 客户端到JMS
		// Provider 的连接
		Connection connection = null; 
		// Session： 一个发送或接收消息的线程
		Session session; 
		// Destination ：消息的目的地;消息发送给谁.
		Destination destination; 
		// MessageProducer：消息发送者
		MessageProducer producer; 
		// TextMessage message;
		// 构造ConnectionFactory实例对象，此处采用ActiveMq的实现jar
		connectionFactory = new ActiveMQConnectionFactory(ActiveMQConnection.DEFAULT_USER,
				ActiveMQConnection.DEFAULT_PASSWORD, "tcp://localhost:61616");
		try { // 构造从工厂得到连接对象
			connection = connectionFactory.createConnection();
			// 启动
			connection.start();
			// 获取操作连接
			session = connection.createSession(Boolean.TRUE, Session.AUTO_ACKNOWLEDGE);
			// 获取session注意参数值xingbo.xu-queue是一个服务器的queue，须在在ActiveMq的console配置
			destination = session.createQueue("FirstQueue");
			// 得到消息生成者【发送者】
			producer = session.createProducer(destination);
			// 设置不持久化，此处学习，实际根据项目决定
			producer.setDeliveryMode(DeliveryMode.NON_PERSISTENT);
			// 构造消息，此处写死，项目就是参数，或者方法获取
			sendMessage(session, producer);
			session.commit();
		} catch (Exception e) {
			e.printStackTrace();
		} finally {
			try {
				if (null != connection)
					connection.close();
			} catch (Throwable ignore) {
			}
		}
	}

	public static void sendMessage(Session session, MessageProducer producer) throws Exception {
		for (int i = 1; i <= SEND_NUMBER; i++) {
			TextMessage message = session.createTextMessage("ActiveMq 发送的消息" + i);
			// 发送消息到目的地方

			System.out.println("发送消息：" + "ActiveMq 发送的消息" + i);
			producer.send(message);
		}
	}
}

```
###3.2.再创建接收者Receiver.java
``` java
package com.mg.demo;

import javax.jms.Connection;
import javax.jms.ConnectionFactory;
import javax.jms.Destination;
import javax.jms.MessageConsumer;
import javax.jms.Session;
import javax.jms.TextMessage;

import org.apache.activemq.ActiveMQConnection;
import org.apache.activemq.ActiveMQConnectionFactory;

public class Receiver{
    public static void main(String[] args) {
		// ConnectionFactory ：连接工厂，JMS 用它创建连接
		ConnectionFactory connectionFactory;
		// Connection ：JMS 客户端到JMS Provider 的连接
		Connection connection = null;
		// Session： 一个发送或接收消息的线程
		Session session;
		// Destination ：消息的目的地;消息发送给谁.
		Destination destination;
		// 消费者，消息接收者
		MessageConsumer consumer;
		connectionFactory = new ActiveMQConnectionFactory(ActiveMQConnection.DEFAULT_USER,
				ActiveMQConnection.DEFAULT_PASSWORD, "tcp://localhost:61616");
		try {
			// 构造从工厂得到连接对象
			connection = connectionFactory.createConnection();
			// 启动
			connection.start();
			// 获取操作连接
			session = connection.createSession(Boolean.FALSE, Session.AUTO_ACKNOWLEDGE);
			// 获取session注意参数值xingbo.xu-queue是一个服务器的queue，须在在ActiveMq的console配置
			destination = session.createQueue("FirstQueue");
			consumer = session.createConsumer(destination);
			while (true) {
				// 设置接收者接收消息的时间，为了便于测试，这里谁定为100s
				TextMessage message = (TextMessage) consumer.receive(100000);
				if (null != message) {
					System.out.println("收到消息" + message.getText());
				} else {
					break;
				}
			}
		} catch (Exception e) {
			e.printStackTrace();
		} finally {
			try {
				if (null != connection)
					connection.close();
			} catch (Throwable ignore) {
			}
		}
	}
}
```
###3.3.测试结果
    先运行接收者Receiver.java，在运行Sender.java。
    得到结果如下图：(2个控制台都会输出如下图数据)
![](./2.png)

##4.使用jfinal-ext中的jms插件操作activeMQ
    整合quartz任务调度框架，实现每10秒发送一次消息到队列。

###4.1.核心代码
``` java
public static void main(String[] args) throws InstantiationException, IllegalAccessException, ClassNotFoundException {
	JmsPlugin jp = new JmsPlugin("jms.properties");
	jp.start();
	PropertyConfig pc = PropertyConfig.me();
	pc.loadPropertyFile("job.properties");
	QuartzPlugin qp = new QuartzPlugin();
	if (pc.getPropertyToBoolean("a.enable")) {
		qp.add(pc.getProperty("a.cron"), (Job) Class.forName(pc.getProperty("a.job")).newInstance());
    }
	qp.start();
}
```
###4.2.配置文件jms.properties
``` txt
################################
#          server info         #
################################
# jms服务器地址
serverUrl=tcp://localhost:61616
username=admin
password=admin

################################
#          queue info          #
################################
# 发送的队列名字，用“，”号分隔
sendQueues=firstMQ

# 接受的队列的名字，用“，”号分隔
receiveQueues=firstMQ
# 队列firstMQ上消息名字为a的消息号
queue.firstMQ.a=10000
#接受到队列q1上消息名字为a的消息的时候调用的处理器
queue.firstMQ.a.resolver=com.mg.jfinal.ext.demo.resolver.MGResolver
```
###4.3.配置文件job.properties
``` txt
#JobA
a.job=com.mg.jfinal.task.JobA
a.cron=*/10 * * * * ?
a.enable=true
```
###4.4.运行结果
    如图：
![](./3.png)

##5.代码地址
http://git.oschina.net/mgang/activeMQ




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)