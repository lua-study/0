 **#osmp Osgi Service Management Platform** 

交流QQ群:335898216


- 基于OSGI、SERVICEMIX开发
- 组件化的开发方式，封装了大量的基础组件，可以直接用于实际项目
- 动态的数据源添加、动态的SQL支持，提供DEMO可快速零成本入门
- 在线BUNDLE服务安装、部署、升级、卸载
- 通过CXF提供基于RESTFUL的微服务访问，通过client可以方便灵活的扩展多种通讯协议
- 通过ZOOKEEPER实现基于分布式的服务注册、发现、路由、负责均衡
- 全局日志集中式管理，方便快捷的日志查询
- 提供多种维度的监控管理，数据库监控、服务监控、BUNDLE监控、性能监控、缓存监控等
- 提供基于策略的灰度升级、安全拦截、可实现参数级别的软负载和服务路由
- 提供强大的扩展能力，可以自由扩展组件以适应项目需要
- 提供强大的WEB管理界面，集中式的管理各NODE节点


![分布式部署、去中心化](http://git.oschina.net/uploads/images/2016/0826/100752_cc06b354_350222.png "分布式部署、去中心化")

![基本功能架构](http://git.oschina.net/uploads/images/2016/0826/100558_08b1dc02_350222.jpeg "基本功能架构")

![注册中心](http://git.oschina.net/uploads/images/2016/0826/101241_998951d7_350222.png "注册中心")

![技术架构体系](http://git.oschina.net/uploads/images/2016/0826/101352_90d64fdc_350222.png "技术架构体系")

![输入图片说明](http://git.oschina.net/uploads/images/2016/0826/101627_f2ff96b6_350222.png "在这里输入图片标题")

![输入图片说明](http://git.oschina.net/uploads/images/2016/0826/101642_76fd394e_350222.png "在这里输入图片标题")


 **入门开发**

环境：jdk1.7以上
服务器:apache-servicemix5.1.0 目前高版本由于spring不兼容。需要修改spring配置，有兴趣的TX可以自己修改


1、添加数据源，新增数据源配置文件，并直接上传到服务器 /etc/datasource 目录下即可,系统会自动扫描并动态添加数据

com.osmp.jdbc.properties
```
osmp.jdbc.name=osmp
osmp.jdbc.driverClassName=com.mysql.jdbc.Driver
osmp.jdbc.url=jdbc:mysql://10.2.2.1:3306?autoReconnect=true&useUnicode=true&characterEncoding=UTF-8
osmp.jdbc.username=root
osmp.jdbc.password=root
osmp.jdbc.initialSize=5
osmp.jdbc.maxActive=100
osmp.jdbc.minIdle=5
osmp.jdbc.maxWait=3000
osmp.jdbc.validationQuery=select 1
osmp.jdbc.timeBetweenEvictionRunsMillis=100000
osmp.jdbc.minEvictableIdleTimeMillis=30000
osmp.jdbc.removeAbandonedTimeout=30000


```

2、添加后可以直接访问 http://ip:8181/druid查看是否添加成功

3、开发服务组件
   3.1参照提供的osmp-demo组件，建立 pom 插件工程，pom如下：

```
 
	 4.0.0 
	 
		 com.osmp.baseweb 
		 osmp-parent 
		 1.0.0 
	 

	 osmp-demo 
	 bundle 
	 osmp-demo 

	 
		 
			 
				 org.apache.felix 
				 maven-bundle-plugin 
				 true 
				 
					 
						 ${project.artifactId} 
						  
						 
							org.springframework.aop,
							org.springframework.aop.framework,
							org.springframework.cglib,
							org.springframework.cglib.proxy,
							org.springframework.cglib.core,
							org.springframework.cglib.reflect,
							org.aopalliance.aop,
							org.aopalliance.intercept,
							*;resolution:=optional
						 
					 
				 
			 
		 
	 

	 
		 
			 com.osmp.baseweb 
			 osmp-intf-define 
			 ${osmp.version} 
		 
		 
			 com.osmp.baseweb 
			 osmp-jdbc 
			 ${osmp.version} 
		 
		
		 
			 com.osmp.baseweb 
			 osmp-cache-osgi 
			 ${osmp.version} 
		 
		
		 
			 org.springframework.osgi 
			 spring-osgi-core 
		 
		
		 
			 org.osgi 
			 org.osgi.core 
		 
	 
 
```



   3.2并编写服务类，服务类需要实现 BaseDateService接口如下：
    ```
/*   
 * Project: OSMP
 * FileName: TestServiceImpl.java
 * version: V1.0
 */
package com.osmp.demo.service;


import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Component;

import com.osmp.intf.define.model.Parameter;
import com.osmp.intf.define.service.BaseDataService;
import com.osmp.demo.service.user.UserService;
import com.osmp.demo.service.user.entity.User;

/**
 * Description:
 * 
 * @author: wangkaiping
 * @date: 2014年9月26日 下午3:03:55
 */
@Component
public class TestServiceImpl implements BaseDataService {

	@Autowired
	private UserService userservice;

	@Override
	public Object execute(Parameter parameter) {
		String name = parameter.getQueryMap().get("name");
		String age = parameter.getQueryMap().get("age");
		userservice.getUserAge(age);
		userservice.getUserName(name);
		User u = new User();
		u.setAge(userservice.getUserAge(age));
		u.setName(userservice.getUserName(name));
		return u;
	}

}

```

3.3发布为osgi服务，配置文件如下：
```
 
 

	 
	 
	
	
	  
	
	 
	 
		 
			 
			 
		 
	 

 

```

3.4 maven install打包后，发布，将打好的包直接复制到servicemix/deploy即可
3.5 访问服务 http://192.168.2.206:8181/cxf/service/osmp-demo?source={"from":"demo"}&parameter={"name":"gg","age":"12"}
    访问规则 ip:port/cxf/service/发布的服务名称?source参数表示来源的客户端,可以自由扩展，但是frmo不能少, parameter 参数，json格式


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)