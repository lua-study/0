#uncode-session


非常小巧的集群session公享组件，代码千行以内，避免使用应用容器插件的多种烦恼。



# 功能概述

1. 非常小巧的集群session公享组件，类似于spring-session。
2. 总代码不超过1000行。
3. 易于使用和扩展。




------------------------------------------------------------------------

# 配置

## 1. web.xml
	
	 
	 
	     SessionSharingFilter 
	     cn.uncode.session.SessionSharingFilter 
	 
	 
	     SessionSharingFilter 
	     /* 
	 

## 2. 基于Redis的Spring配置


	 
	 
		 
    		 
    			 127.0.0.1:26379 
    			 127.0.0.2:26379 
    		 
    	 
    	 
		 
		 
		 
		 
	 
	
## 3. 基于Memcached的Spring配置
	
	 
         
             
                 127.0.0.1:11211 
             
         
     
------------------------------------------------------------------------
	
# 自定义扩展


## 1. 自定义实现类

	public class CustomSessionCache implements SessionCache{
	
		@Override
		public void put(String sessionId, SessionMap sessionMap, int timeout) {
		
		}
	
		@Override
		public SessionMap get(String sessionId) {
		
		}
	
		@Override
		public void setMaxInactiveInterval(String sessionId, int interval) {
		
		}
	
		@Override
		public void destroy(String sessionId) {
		
		}
	}
	

## 2. 配置管理器


	 
	 
	
	 
	 
		 
		 
		 
		-->
	 

------------------------------------------------------------------------


# 版权

作者：冶卫军（ywj_316@qq.com）

技术支持QQ群：47306892

Copyright 2016 www.uncode.cn


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)