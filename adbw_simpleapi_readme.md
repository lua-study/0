# 简易api for php+mysql
> 简易api for php+mysql是一个简单的php api编写助手

## 无需框架
1. 上手可用，万用接口！
1. 可快速为app及小程序等编写自定义api接口。
1. 含常用的msql操作方法及常用post方法。

## 使用方法
1. config.php 配置文件
1. demo.php db方法演示
1. every_api 万用api
1. adminer.php 数据库管理

## every_api
> 正确时返回status:200，data;
> 错误时返回错误原因

### url
>every_api.php

### insert
#### 参数：
```
op:insert //
table:ssc_data //表名
//以下数字段：
type:2
time:112233445
number:19910
data:9,2,4,5
title:标题
```
#### 返回
```
{
    "status": "200",
    "data": "2" //写入的id
}
```


### update
#### 参数：
```
op:update //
table:ssc_data //表名
where:id=11643  /条件
//以下数字段：
type:2
time:112233445
number:19910
data:9,2,4,5
title:标题
```

#### 返回
```
{
    "status": "200",
    "data": "update success!"
}
```

### find
#### 参数：
```
op:find //
table:ssc_data //表名
where:id=11643  /条件
cols:id,title  //可选,查询字段，默认为*
```

#### 返回
```
{
    "status": "200",
    "data": {
        "id": "11643",
        "type": "2",
        "time": "22222",
        "number": "199104",
        "data": "9,2,4,5",
        "title": "??11111111update"
    }
}
```
### select
#### 参数：
```
op:select //
table:ssc_data //表名
where:id>0  //条件
cols:id,title  //可选,查询字段，默认为*
```

#### 返回
```
{
    "status": "200",
    "data": [
        {
            "id": "11643",
            "title": "??11111111update"
        },
        {
            "id": "11644",
            "title": "??"
        }
    ]
}
```

### column
#### 参数：
```
op:column //
table:ssc_data //表名
where:id=1  //条件
cols:id  //字段
```

#### 返回
```
{
    "status": "200",
    "data": "11643"
}
```




## db常用方法

### 写入 $db->insert
~~~
$db->insert($tablename,$data);
~~~
#### 参数
~~~
1. $tablename：string，表名
1. $data：array,内容数组
1. 返回值：int,写入的id
~~~


### 更新  $db->update
~~~
$db->update($tablename,$data,$where);
~~~
#### 参数
~~~
1. $tablename：表名
1. $data：array,内容数组
1. $where：string，条件。如: id = 1
1. 返回值：int,影响的条数
~~~


### 删除 $db->delete
~~~
$db->delete($tablename,$where);
~~~
#### 参数
~~~
1. $tablename：表名
1. $where：string，条件。如: id = 1
1. 返回值：int,影响的条数
~~~



### 单条查询 $db->find
~~~
$db->find($tablename,'*',$where);
$result = $db->fetch_assoc();
~~~
#### 参数
~~~
1. $tablename：表名
1. 字段 : string，星号（全部）或字段,如: id,name,title。
1. $where：string，条件。如: id = 1
1. 返回值：array,返回的内容
~~~


### 多条查询 $db->select
~~~
$db->select($tablename,'*',$where);
~~~
#### 参数
1. $tablename：表名
1. 字段 : string，星号（全部）或字段,如: id,name,title。
1. $where：string，条件。如: id = 1
1. 返回值：array,返回的内容


## 返回json 写法
~~~
 if($result){
	$re['status'] = '200';
	$re['msg'] =  $result;
 }else{
	$re['status'] = '110';
	$re['msg'] = $op.' failed!';;
 }
 	die(json_encode($re));
 }
 ~~~

## 更多方法
~~~
1. count( $table,$fileds,$where )
1. sum( $table,$fileds,$where )
1. create_database( $database )
1. show_databases( )
1. show_tables( $database ) 
1. query( $rts )
1. fetch_assoc( )
1. fetch_row( )
1. fetch_Object( )
1. findall( $table ) 
1. getip( )
1. tiao( $title,$url ) 提示并跳转
1. postForm($url,$params=false,$ispost=0) 以 form方式post
1. postJson($url,$params=false,$ispost=0) 以 json方式post
1. postJump($url,$data) 模拟表单、提交并跳转
 ~~~

更多方法及详细请查看  lib/Base.class.php


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)