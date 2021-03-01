# Tomcat Clustering Redis Session Manager

Redis session manager is pluggable one. It uses to store sessions into Redis for easy distribution of HTTP Requests across a cluster of Tomcat servers. Sessions are implemented as as non-sticky i.e, each request is forwarded to any server in round-robin manner.

The HTTP Requests session setAttribute(name, value) method stores the session into Redis (session attribute values must be Serializable) immediately and the session getAttribute(name) method request directly from Redis. Also, the inactive sessions has been removed based on the session time-out configuration.

Supports redis default, sentinel and cluster mode, based on the configuration.

Going forward, we no need to enable sticky session (JSESSIONID) in Load balancer.

## Supports:
   - Apache Tomcat 7
   - Apache Tomcat 8
   - Apache Tomcat 9

## Downloads:
   - [latest version (3.0)](https://github.com/ran-jit/tomcat-cluster-redis-session-manager/releases/tag/3.0)
   - [older versions](https://github.com/ran-jit/tomcat-cluster-redis-session-manager/wiki)

#### Pre-requisite:
1. jedis.jar
2. commons-pool2.jar
3. commons-logging.jar

more details.. https://github.com/ran-jit/tomcat-cluster-redis-session-manager/wiki
    

#### Steps to be done,
1. Move the downloaded jars to tomcat/lib directory
	- **tomcat/lib/**
	
2. Add tomcat system property "catalina.base"
	- **catalina.base="TOMCAT_LOCATION"**
	     * edit the tomcat/bin/catalina.sh add JAVA_OPTS for example:
	     ```
	     JAVA_OPTS='-Dcatalina.base=/opt/tomcat'
	     ```

3. Extract downloaded package (tomcat-cluster-redis-session-manager.zip) to configure Redis credentials in redis-data-cache.properties file and move the file to tomcat/conf directory
	- **tomcat/conf/redis-data-cache.properties**

4. Add the below two lines in tomcat/conf/context.xml
	- **&#60;Valve className="tomcat.request.session.redis.SessionHandlerValve" &#47;&#62;**
	- **&#60;Manager className="tomcat.request.session.redis.SessionManager" &#47;&#62;**

5. Verify the session expiration time in tomcat/conf/web.xml
	- **&#60;session-config&#62;**
	- 	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **&#60;session-timeout&#62;60&#60;&#47;session-timeout&#62;**
	- **&#60;&#47;session-config&#62;**

### Note:
  - **All your session attribute values must implement java.io.Serializable.**
  - Supports redis default, sentinel and cluster mode, based on the redis-data-cache.properties configuration.

### Configuration Properties:
 
 
     
          Property  Description  
          redis.hosts  Redis server running instance IP address and port number - ex: 127.0.0.1:6379, 127.0.0.2:6379, 127.0.0.2:6380, .. - default: 127.0.0.1:6379  
          redis.password  Redis protected password  
          redis.database  Redis database selection. (Numeric value) - default: 0  
          redis.timeout  Redis connection timeout - default: 2000 ms  
          redis.cluster.enabled  To enable redis cluster mode - default: false - supported values: true/false  
          redis.sentinel.enabled  To enable redis sentinel mode - default: false - supported values: true/false  
          redis.sentinel.master  Redis sentinel master name - default: mymaster  
          lb.sticky-session.enabled  To enable redis and standard session mode  If enabled,  Must be enabled sticky session in your load balancer configuration. Else this manager may not return the updated session values  Session values are stored in local jvm and redis  If redis is down/not responding, requests uses jvm stored session values to process user requests. Redis comes back the values will be synced  - default: false  
     
 
 


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)