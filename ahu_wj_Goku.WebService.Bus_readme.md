# Goku.WebService.Bus
基于SpringBoot + Spring +  Apache CXF +Mybatis 开发SOAP的 WebService 服务

# 备注 
| **版本** |  **说明**| 
| ------   |:------:|
| 1.0.0版本| |
| 2.0.0版本|springboot启动|

# 原理
Mybatis基于动态代理实现Mapper接口，实现快速开发SOAP的WebService接口服务

# 功能

#### 1.支持日志记录，黑白名单控制 
#### 2.支持数据库配置velocity sql查询语句(支持mybatis.velocity指令） 
#### 3.基础配置获取增加mybatis缓存机制 
##### 4.支持下列业务操作

| 操作类型|交易方法|说明|
| ------------- |:-------------:| -------------:|
|新增|insert|可批量|
|修改|update|可批量|
|删除|delete|可批量|  
|查询单个|SelectOne|  
|查询列表|SelectList|支持分页，需要入参带分页标志参数|  
|存储过程处理|SelectProc|支持分页，需要入带待分页标志参数|  
|新增或修改|insertOrupdate|待完善|  

##### 5.待完善

| 功能 |说明|
| ------------- |:-------------:|
|值域验证|字典值域验证，筛选|
|字段验证|字段类型，格式验证|

# xml格式

## 1.新增或者修改

入参：
```xml
  
    
     
     22   
     
     22   
     
     insertOrupdate   
     
     sysUserMapper  
     
    
     
      
       113   
       mnbhkl  
       
     
      
       666   
       3344  
      
    
 

```

出参：
```xml
 
   
     成功 
     0 
   
 

```
## 2.查询列表

入参：
```xml
  
   
     22   
     22   
     SelectList   
     sysUserMapper  
     
    
      
       fjx  
      
    
 

```

出参：
```xml
 
   
     
       
       E1C879F8-C493-D26A-699D-604DE42A2BE6-COMPANY 
       *** 
       Y 
       90 
       *** 
       yYSu0BSux2I6VPBZHaB6hf1Ldi0= 
       **** 
       nbfujx@qq.com 
       *** 
       *** 
       N 
       2017-08-04 09:07:26.0 
       
       
       fjx 
       
       normal 
       2013-07-03 14:53:30.0 
       1 
     
     成功 
     0 
   
 
```

# 分页查询

入参：
```xml
  
    
     fjx   
     1   
     SelectList   
     sysUserMapper   
      
     Y   
      
     1   
      
     10  
     
    
      
       fjx  
      
    
 
```
出参：
```xml
 
   
     
	...
     
     
	...
     
     
	...
     
     
	...
     
     
	...
     
     
	...
     
     
	...
     
     
	...
     
     
	...
     
     
	...
     
     0 
     成功! 
     
     1 
     
     649 
   
 
```



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)