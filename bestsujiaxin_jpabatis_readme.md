# jpabatis
## 一、介绍
基于mybatis封装jpa-batis插件，方便使用jpa的项目能像使用mybatis一样能非常方便的处理复杂的查询sql语句。
主要是为了复杂的查询而生，所以我把insert、update、delete的支持都干掉了，只支持select。

因是基于mybatis改装的，所以mapper.xml里的写法跟mybatis一模一样，底层与数据库交互是基于jpa的EntityManager类来实现的。

各位码友觉得有用的给个star，也可以fork去完善完善，觉得无用的勿喷，谢谢。

## 二、软件架构
软件架构说明
基于：

1、[mybatis-3](https://github.com/mybatis/mybatis-3)

2、Spring Data JPA

## 三、安装教程
当前版本是基于springboot1.5.10.RELEASE版本封装，如果想使用高版本springboot，自己修改parent的版本即可
```
 
	 org.springframework.boot 
	 spring-boot-starter-parent 
	 1.5.10.RELEASE 
 
```
在您的工程里引入jpa-batis.jar包
```
 
     com.yinsin 
     jpabatis 
     0.0.1-SNAPSHOT 
 
```

## 四、使用说明

### 1、在springboot配置文件中增加Mapper.xml文件的路径配置
```java
batis:
    mapper: mappers # 假如mapper.xml在，src/main/resources/mappers/ 目录下
```
或者
```java
batis.mapper=mappers # 假如mapper.xml在，src/main/resources/mappers/ 目录下
```

### 2、编写Mapper.xml：
```java
 
 
 
     
         
         
         
         
         
         
         
         
         

     
    
     
    	select 
		  ui.row_id, ui.account, ui.name, ui.mobile,
		  ui.email, ui.headimage, ui.status,
		  ugi.game_integral, ugi.game_level
		from
		  cll_user_info ui 
		  left join cll_user_game_info ugi 
		    on ui.row_id = ugi.user_id 
		where ugi.game_no = #{gameNo,jdbcType=VARCHAR}
		order by ugi.game_integral desc,
		  ugi.game_level desc,
		  ui.lastlogindate desc
     
 
```

### 3、需要使用jpabatis的类中注入JpaSession类：
```java
@JpaMapper
private JpaSession session;
```
  
### 4、执行调用：
#### 4.1 查询单条记录
```java
Map  param = new HashMap<>();
param.put("gameNo", "xx");
// mapperid -> mapper的namespace +  的id
// 例如：com.yinsin.lifechess.domain.game.CllUserGameInfo.loadCChessRankingList
Map  result = session.selectOne("mapperid", param);
// TODO ...
```

#### 4.2 查询多条记录
```java
Map  param = new HashMap<>();
param.put("gameNo", "xx");
// mapperid -> mapper的namespace +  的id
// 例如：com.yinsin.lifechess.domain.game.CllUserGameInfo.loadCChessRankingList
List > dataList = session.selectList("mapperid", param);
// TODO ...
```

#### 4.3 查询多条记录并分页
```java
// 分页查询和非分页查询，只有一个Pageable参数的区别，mapper中的sql不需要写limit
Map  param = new HashMap<>();
param.put("gameNo", "xx");
Pageable pageable = new PageRequest(0, 10); //1.x版本
//Pageable pageable = Pageable.of(0, 10); //2.x版本
// mapperid -> mapper的namespace +  的id
// 例如：com.yinsin.lifechess.domain.game.CllUserGameInfo.loadCChessRankingList
Page > dataList = session.selectList("mapperid", param, pageable);
// TODO ...
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)