# APIJSON 
[![GitHub release](https://img.shields.io/github/release/TommyLemon/APIJSON.svg)](https://github.com/TommyLemon/APIJSON/releases)
[![Java API](https://img.shields.io/badge/Java-1.6%2B-brightgreen.svg?style=flat)](http://www.oracle.com/technetwork/java/api-141528.html) 
[![Android API](https://img.shields.io/badge/Android-15%2B-brightgreen.svg?style=flat)](https://developer.android.com/guide/topics/manifest/uses-sdk-element.html#ApiLevels) 
[![JavaScrpit API](https://img.shields.io/badge/JavaScript-ES5%2B-brightgreen.svg?style=flat)](http://www.ecma-international.org/publications/standards/Standard.htm)
[![License](https://img.shields.io/badge/license-Apache%202-4EB1BA.svg)](https://www.apache.org/licenses/LICENSE-2.0.html)

 

[Java-Server](https://github.com/TommyLemon/APIJSON/tree/master/APIJSON-Java-Server)    [Android](https://github.com/TommyLemon/APIJSON/tree/master/APIJSON-Android)    [JavaScript](https://github.com/TommyLemon/APIJSON/tree/master/APIJSON-JavaScript)    [Vue.js](https://github.com/TommyLemon/APIJSON-JS-Vue)

[English Document](https://github.com/TommyLemon/APIJSON/blob/master/README(English).md)

[在线测试](http://139.196.140.118)

 

* ### [1.简介](#1)
* ### [2.对比传统方式](#2)
* [2.1 开发流程](#2.1)
* [2.2 客户端请求](#2.2)
* [2.3 服务端操作](#2.3)
* [2.4 客户端解析](#2.4)
* [2.5 对应不同需求的请求](#2.5)
* [2.6 对应不同请求的结果](#2.6)
* ### [3.对应关系总览](#3)
* [3.1 操作方法](#3.1)
* [3.2 功能符](#3.2)
* ### [4.快速上手](#4)
* [4.1 下载解压](#4.1)
* [4.2 导入table](#4.2)
* [4.3 运行服务端工程](#4.3)
* [4.4 运行客户端工程](#4.4)
* [4.4 操作客户端App](#4.5)
* ### [5.其它](#5)
* [5.1 相关推荐](#5.1)
* [5.2 关于作者](#5.2)
* [5.3 下载试用](#5.3)
* [5.4 更新日志](#5.4)
* [5.5 Star&Fork](#5.5)

##  1.简介 

APIJSON是一种JSON传输结构协议。 

客户端可以定义任何JSON结构去向服务端发起请求，服务端就会返回对应结构的JSON，所求即所得。 
一次请求任意结构任意数据，方便灵活，不需要专门接口或多次请求。 
支持增删改查、模糊搜索、远程函数、权限管理等。还能去除重复数据，节省流量提高速度！ 

从此HTTP传输JSON数据没有接口，更不需要文档！ 
客户端再也不用和服务端沟通接口或文档问题了！再也不会被文档各种错误坑了！ 
服务端再也不用为了兼容旧版客户端写新版接口和文档了！再也不会被客户端随时随地没完没了地烦了！
 
[为什么要用APIJSON？](https://github.com/TommyLemon/APIJSON/wiki)

![](https://raw.githubusercontent.com/TommyLemon/APIJSON/master/picture/apijson_all_pages_0.jpg) 
![](https://raw.githubusercontent.com/TommyLemon/APIJSON/master/picture/apijson_all_pages_1.jpg) 
![](https://raw.githubusercontent.com/TommyLemon/APIJSON/master/picture/apijson_all_pages_2.jpg) 
![](https://raw.githubusercontent.com/TommyLemon/APIJSON/master/picture/apijson_all_pages_3.jpg) 

![](https://raw.githubusercontent.com/TommyLemon/APIJSON/master/picture/server_idea_log_complex.jpg) 

![](https://raw.githubusercontent.com/TommyLemon/APIJSON/master/picture/mysql_workbench_request.jpg) 
![](https://raw.githubusercontent.com/TommyLemon/APIJSON/master/picture/mysql_workbench_user.jpg) 
![](https://raw.githubusercontent.com/TommyLemon/APIJSON/master/picture/mysql_workbench_moment.jpg) 

 
 

### 举几个例子:

#### 查询用户
请求：
  
{
  "User":{
  }
}
  

[点击这里测试](http://139.196.140.118:8080/get/{"User":{}})

返回：
  
{
  "User":{
    "id":38710,
    "sex":0,
    "name":"TommyLemon",
    "certified":true,
    "tag":"Android&Java",
    "phone":13000038710,
    "head":"http://static.oschina.net/uploads/user/1218/2437072_100.jpg?t=1461076033000",
    "date":1485948110000,
    "pictureList":[
      "http://static.oschina.net/uploads/user/1218/2437072_100.jpg?t=1461076033000",
      "http://common.cnblogs.com/images/icon_weibo_24.png"
    ]
  },
  "code":200,
  "msg":"success"
}
  

 

#### 查询用户列表
请求：
  
{
  "[]":{
    "count":3,             //只要3个
    "User":{
      "@column":"id,name"  //只要id,name这两个字段
    }
  }
}
  

[点击这里测试](http://139.196.140.118:8080/get/{"[]":{"count":3,"User":{"@column":"id,name"}}})

返回：
  
{
  "[]":[
    {
      "User":{
        "id":38710,
        "name":"TommyLemon"
      }
    },
    {
      "User":{
        "id":70793,
        "name":"Strong"
      }
    },
    {
      "User":{
        "id":82001,
        "name":"Android"
      }
    }
  ],
  "code":200,
  "msg":"success"
}
  

 

#### 查询动态及发布者用户
请求：
  
{
  "Moment":{
  },
  "User":{
    "id@":"Moment/userId"  //User.id = Moment.userId
  }
}
  

[点击这里测试](http://139.196.140.118:8080/get/{"Moment":{},"User":{"id@":"Moment%252FuserId"}})

返回：
  
{
  "Moment":{
    "id":12,
    "userId":70793,
    "date":"2017-02-08 16:06:11.0",
    "content":"1111534034"
  },
  "User":{
    "id":70793,
    "sex":0,
    "name":"Strong",
    "tag":"djdj",
    "head":"http://static.oschina.net/uploads/user/585/1170143_50.jpg?t=1390226446000",
    "contactIdList":[
      38710,
      82002
    ],
    "date":"2017-02-01 19:21:50.0"
  },
  "code":200,
  "msg":"success"
}
  

 

#### 查询类似微信朋友圈的动态列表
请求：
  
{
  "[]":{                             //请求一个数组
    "page":0,                        //数组条件
    "count":2,
    "Moment":{                       //请求一个名为Moment的对象
      "content$":"%a%"               //对象条件，搜索content中包含a的动态
    },
    "User":{
      "id@":"/Moment/userId",        //User.id = Moment.userId  缺省引用赋值路径，从所处容器的父容器路径开始
      "@column":"id,name,head"       //指定返回字段
    },
    "Comment[]":{                    //请求一个名为Comment的数组，并去除Comment包装
      "count":2,
      "Comment":{
        "momentId@":"[]/Moment/id"   //Comment.momentId = Moment.id  完整引用赋值路径
      }
    }
  }
}
  

[点击这里测试](http://139.196.140.118:8080/get/{"[]":{"page":0,"count":2,"Moment":{"content$":"%2525a%2525"},"User":{"id@":"%252FMoment%252FuserId","@column":"id,name,head"},"Comment[]":{"count":2,"Comment":{"momentId@":"[]%252FMoment%252Fid"}}}})

返回：
  
{
  "[]":[
    {
      "Moment":{
        "id":15,
        "userId":70793,
        "date":1486541171000,
        "content":"APIJSON is a JSON Transmission Structure Protocol…",
        "praiseUserIdList":[
          82055,
          82002,
          82001
        ],
        "pictureList":[
          "http://static.oschina.net/uploads/user/1218/2437072_100.jpg?t=1461076033000",
          "http://common.cnblogs.com/images/icon_weibo_24.png"
        ]
      },
      "User":{
        "id":70793,
        "name":"Strong",
        "head":"http://static.oschina.net/uploads/user/585/1170143_50.jpg?t=1390226446000"
      },
      "Comment[]":[
        {
          "id":176,
          "toId":166,
          "userId":38710,
          "momentId":15,
          "date":1490444883000,
          "content":"thank you"
        },
        {
          "id":1490863469638,
          "toId":0,
          "userId":82002,
          "momentId":15,
          "date":1490863469000,
          "content":"Just do it"
        }
      ]
    },
    {
      "Moment":{
        "id":58,
        "userId":90814,
        "date":1485947671000,
        "content":"This is a Content...-435",
        "praiseUserIdList":[
          38710,
          82003,
          82005,
          93793,
          82006,
          82044,
          82001
        ],
        "pictureList":[
          "http://static.oschina.net/uploads/img/201604/22172507_aMmH.jpg"
        ]
      },
      "User":{
        "id":90814,
        "name":7,
        "head":"http://static.oschina.net/uploads/user/51/102723_50.jpg?t=1449212504000"
      },
      "Comment[]":[
        {
          "id":13,
          "toId":0,
          "userId":82005,
          "momentId":58,
          "date":1485948050000,
          "content":"This is a Content...-13"
        },
        {
          "id":77,
          "toId":13,
          "userId":93793,
          "momentId":58,
          "date":1485948050000,
          "content":"This is a Content...-77"
        }
      ]
    }
  ],
  "code":200,
  "msg":"success"
}
  


 

[在线测试](http://139.196.140.118)

 
 
 
##  2.对比传统RESTful方式 

###  2.1 开发流程 
 开发流程 | 传统方式 | APIJSON
-------- | ------------ | ------------
 接口传输 | 等服务端编辑接口，然后更新文档，客户端再按照文档编辑请求和解析代码 | 客户端按照自己的需求编辑请求和解析代码。 没有接口，更不需要文档！客户端再也不用和服务端沟通接口或文档问题了！
 兼容旧版 | 服务端增加新接口，用v2表示第2版接口，然后更新文档 | 什么都不用做！
 
  
 
###  2.2 客户端请求 
 客户端请求 | 传统方式 | APIJSON
-------- | ------------ | ------------
 要求 | 客户端按照文档在对应URL后面拼接键值对 | 客户端按照自己的需求在固定URL后拼接JSON
 结构 | 同一个URL内table_name只能有一个    base_url/get/table_name? key0=value0&key1=value1... | 同一个URL后TableName可传任意数量个    base_url/get/ {  &nbsp;&nbsp; TableName0:{  &nbsp;&nbsp;&nbsp;&nbsp; key0:value0,  &nbsp;&nbsp;&nbsp;&nbsp; key1:value1,  &nbsp;&nbsp;&nbsp;&nbsp; ...  &nbsp;&nbsp; },  &nbsp;&nbsp; TableName1:{  &nbsp;&nbsp;&nbsp;&nbsp; ...  &nbsp;&nbsp; }  &nbsp;&nbsp; ...  }
 URL | 不同的请求对应不同的URL，基本上有多少个不同的请求就得有多少个接口URL | 相同的操作方法(增删改查)都用同一个URL， 大部分请求都用7个通用接口URL的其中一个
 键值对 | key=value | key:value
 
  
 
###  2.3 服务端操作 
 服务端操作 | 传统方式 | APIJSON
-------- | ------------ | ------------
 解析和返回 | 取出键值对，把键值对作为条件用预设的的方式去查询数据库，最后封装JSON并返回给客户端 | 把Parser#parse方法的返回值返回给客户端就行
 返回JSON结构的设定方式 | 由服务端设定，客户端不能修改 | 由客户端设定，服务端不能修改
 
  
 
###  2.4 客户端解析 
 客户端解析 | 传统方式 | APIJSON
-------- | ------------ | ------------
 查看方式 | 查文档或问后端，或等请求成功后看日志 | 看请求就行，所求即所得，不用查、不用问、不用等。也可以等请求成功后看日志
 解析方法 | 用JSON解析器来解析JSONObject | 可以用JSONResponse解析JSONObject，或使用传统方式
 
  
 
###  2.5 客户端对应不同需求的请求 
 客户端的请求 | 传统方式 | APIJSON
-------- | ------------ | ------------
 User | base_url/get/user?id=38710 | [base_url/get/ {  &nbsp;&nbsp; "User":{  &nbsp;&nbsp;&nbsp;&nbsp; "id":38710  &nbsp;&nbsp; } }](http://139.196.140.118:8080/get/{"User":{"id":38710}})
 Moment和对应的User | 分两次请求 Moment:   base_url/get/moment?userId=38710  User:   base_url/get/user?id=38710 | [base_url/get/ {  &nbsp;&nbsp; "Moment":{  &nbsp;&nbsp;&nbsp;&nbsp; "userId":38710  &nbsp;&nbsp; },   &nbsp;&nbsp; "User":{  &nbsp;&nbsp;&nbsp;&nbsp; "id":38710  &nbsp;&nbsp; } }](http://139.196.140.118:8080/get/{"Moment":{"userId":38710},"User":{"id":38710}})
 User列表 | base_url/get/user/list? page=0&count=3&sex=0 | [base_url/get/ {  &nbsp;&nbsp; "User[]":{  &nbsp;&nbsp;&nbsp;&nbsp; "page":0,  &nbsp;&nbsp;&nbsp;&nbsp;  "count":3,   &nbsp;&nbsp;&nbsp;&nbsp; "User":{  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "sex":0  &nbsp;&nbsp;&nbsp;&nbsp; }  &nbsp;&nbsp; } }](http://139.196.140.118:8080/get/{"User[]":{"page":0,"count":3,"User":{"sex":0}}})
 Moment列表， 每个Moment包括 1.发布者User 2.前3条Comment | Moment里必须有 1.User对象 2.Comment数组   base_url/get/moment/list? page=0&count=3&commentCount=3 | [base_url/get/ {  &nbsp;&nbsp; "[]":{  &nbsp;&nbsp;&nbsp;&nbsp; "page":0,   &nbsp;&nbsp;&nbsp;&nbsp; "count":3,   &nbsp;&nbsp;&nbsp;&nbsp; "Moment":{},   &nbsp;&nbsp;&nbsp;&nbsp; "User":{  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "id@":"/Moment/userId"  &nbsp;&nbsp;&nbsp;&nbsp; },  &nbsp;&nbsp;&nbsp;&nbsp; "Comment[]":{  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "count":3,  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "Comment":{  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "momentId@":"[]/Moment/id"  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; }  &nbsp;&nbsp;&nbsp;&nbsp; }  &nbsp;&nbsp; } }](http://139.196.140.118:8080/get/{"[]":{"page":0,"count":3,"Moment":{},"User":{"id@":"%252FMoment%252FuserId"},"Comment[]":{"count":3,"Comment":{"momentId@":"[]%252FMoment%252Fid"}}}})
 User发布的Moment列表，  每个Moment包括  1.发布者User  2.前3条Comment | 1.Moment里必须有User对象和Comment数组  2.字段名必须查接口文档，例如评论数量字段名可能是  commentCount,comment_count或者简写cmt_count等各种奇葩写法...    base_url/get/moment/list? page=0&count=3 &commentCount=3&userId=38710 | 有以下几种方式:   ① 把以上请求里的 "Moment":{}, "User":{"id@":"/Moment/userId"} 改为 ["Moment":{"userId":38710}, "User":{"id":38710}](http://139.196.140.118:8080/get/{"[]":{"page":0,"count":3,"Moment":{"userId":38710},"User":{"id":38710},"Comment[]":{"count":3,"Comment":{"momentId@":"[]%252FMoment%252Fid"}}}})    ② 或把User放在上面的最外层省去重复的User [base_url/get/ {  &nbsp;&nbsp; "User":{  &nbsp;&nbsp;&nbsp;&nbsp; "id":38710  &nbsp;&nbsp; },  &nbsp;&nbsp; "[]":{  &nbsp;&nbsp;&nbsp;&nbsp; "page":0,  &nbsp;&nbsp;&nbsp;&nbsp; "count":3,   &nbsp;&nbsp;&nbsp;&nbsp; "Moment":{  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "userId":38710  &nbsp;&nbsp;&nbsp;&nbsp; },   &nbsp;&nbsp;&nbsp;&nbsp; "Comment[]":{  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "count":3,  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "Comment":{  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "momentId@":"[]/Moment/id"  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; }  &nbsp;&nbsp;&nbsp;&nbsp; }  &nbsp;&nbsp; } }](http://139.196.140.118:8080/get/{"User":{"id":38710},"[]":{"page":0,"count":3,"Moment":{"userId":38710},"Comment[]":{"count":3,"Comment":{"momentId@":"[]%252FMoment%252Fid"}}}})   ③ 如果User之前已经获取到了，还可以不传User来节省请求和返回数据的流量并提升速度 [base_url/get/ {  &nbsp;&nbsp; "[]":{  &nbsp;&nbsp;&nbsp;&nbsp; "page":0,  &nbsp;&nbsp;&nbsp;&nbsp; "count":3,   &nbsp;&nbsp;&nbsp;&nbsp; "Moment":{  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "userId":38710  &nbsp;&nbsp;&nbsp;&nbsp; },  &nbsp;&nbsp;&nbsp;&nbsp; "Comment[]":{  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "count":3,  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "Comment":{  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "momentId@":"[]/Moment/id"  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; }  &nbsp;&nbsp;&nbsp;&nbsp; }  &nbsp;&nbsp; } }](http://139.196.140.118:8080/get/{"[]":{"page":0,"count":3,"Moment":{"userId":38710},"Comment[]":{"count":3,"Comment":{"momentId@":"[]%252FMoment%252Fid"}}}})
 
  
 
###  2.6 服务端对应不同请求的返回结果 
 服务端的返回结果 | 传统方式 | APIJSON
-------- | ------------ | ------------
 User | {  &nbsp;&nbsp; "data":{  &nbsp;&nbsp;&nbsp;&nbsp; "id":38710,  &nbsp;&nbsp;&nbsp;&nbsp; "name":"xxx",  &nbsp;&nbsp;&nbsp;&nbsp; ...  &nbsp;&nbsp; },  &nbsp;&nbsp; "code":200,  &nbsp;&nbsp; "msg":"success" } | {  &nbsp;&nbsp; "User":{  &nbsp;&nbsp;&nbsp;&nbsp; "id":38710,  &nbsp;&nbsp;&nbsp;&nbsp; "name":"xxx",  &nbsp;&nbsp;&nbsp;&nbsp; ...  &nbsp;&nbsp; },  &nbsp;&nbsp; "code":200,  &nbsp;&nbsp; "msg":"success" }
 Moment和对应的User | 分别返回两次请求的结果，获取到Moment后取出userId作为User的id条件去查询User    Moment:   {  &nbsp;&nbsp; "data":{  &nbsp;&nbsp;&nbsp;&nbsp; "id":235,  &nbsp;&nbsp;&nbsp;&nbsp; "content":"xxx",  &nbsp;&nbsp;&nbsp;&nbsp; ...  &nbsp;&nbsp; },  &nbsp;&nbsp; "code":200,  &nbsp;&nbsp; "msg":"success" }    User:   {  &nbsp;&nbsp; "data":{  &nbsp;&nbsp;&nbsp;&nbsp; "id":38710,  &nbsp;&nbsp;&nbsp;&nbsp; "name":"xxx",  &nbsp;&nbsp;&nbsp;&nbsp; ...  &nbsp;&nbsp; },  &nbsp;&nbsp; "code":200,  &nbsp;&nbsp; "msg":"success" } | 一次性返回，没有传统方式导致的 长时间等待结果、两次结果间关联、线程多次切换 等问题    {  &nbsp;&nbsp; "Moment":{  &nbsp;&nbsp;&nbsp;&nbsp; "id":235,  &nbsp;&nbsp;&nbsp;&nbsp; "content":"xxx",  &nbsp;&nbsp;&nbsp;&nbsp; ...  &nbsp;&nbsp; },  &nbsp;&nbsp; "User":{  &nbsp;&nbsp;&nbsp;&nbsp; "id":38710,  &nbsp;&nbsp;&nbsp;&nbsp; "name":"xxx",  &nbsp;&nbsp;&nbsp;&nbsp; ...  &nbsp;&nbsp; },  &nbsp;&nbsp; "code":200,  &nbsp;&nbsp; "msg":"success" }
 User列表 | {  &nbsp;&nbsp; "data":[  &nbsp;&nbsp;&nbsp;&nbsp; {  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "id":38710,  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "name":"xxx",  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ...  &nbsp;&nbsp;&nbsp;&nbsp; },  &nbsp;&nbsp;&nbsp;&nbsp; {  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "id":82001,  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ...  &nbsp;&nbsp;&nbsp;&nbsp; },  &nbsp;&nbsp;&nbsp;&nbsp; ...  &nbsp;&nbsp; ],  &nbsp;&nbsp; "code":200,  &nbsp;&nbsp; "msg":"success" } | {  &nbsp;&nbsp; "User[]":[  &nbsp;&nbsp;&nbsp;&nbsp; {  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "id":38710,  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "name":"xxx",  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ...  &nbsp;&nbsp;&nbsp;&nbsp; },  &nbsp;&nbsp;&nbsp;&nbsp; {  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "id":82001,  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ...  &nbsp;&nbsp;&nbsp;&nbsp; },  &nbsp;&nbsp;&nbsp;&nbsp; ...  &nbsp;&nbsp; ],  &nbsp;&nbsp; "code":200,  &nbsp;&nbsp; "msg":"success" }
 Moment列表，每个Moment包括发布者User和前3条Comment | Moment里必须有 1.User对象 2.Comment数组    {  &nbsp;&nbsp; "data":[  &nbsp;&nbsp;&nbsp;&nbsp; {  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "id":235,  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "content":"xxx",  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ...,  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "User":{  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ...  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; },  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "Comment":[  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ...  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ]  &nbsp;&nbsp;&nbsp;&nbsp; },  &nbsp;&nbsp;&nbsp;&nbsp; {  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "id":301,  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "content":"xxx",  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ...,  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "User":{  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ...  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; },  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ...  &nbsp;&nbsp;&nbsp;&nbsp; },  &nbsp;&nbsp;&nbsp;&nbsp; ...  &nbsp;&nbsp; ],  &nbsp;&nbsp; "code":200,  &nbsp;&nbsp; "msg":"success" } | 1.高灵活，可任意组合 2.低耦合，逻辑很清晰  {  &nbsp;&nbsp; "[]":[  &nbsp;&nbsp;&nbsp;&nbsp; {  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "Moment":{  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "id":235,  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "content":"xxx",  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ...  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; },  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "User":{  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ...  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; },  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "Comment[]":[  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ...  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ]  &nbsp;&nbsp;&nbsp;&nbsp; },  &nbsp;&nbsp;&nbsp;&nbsp; {  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "Moment":{  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "id":301,  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "content":"xxx",  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ...  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; },  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "User":{  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ...  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; },  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ...  &nbsp;&nbsp;&nbsp;&nbsp; },  &nbsp;&nbsp;&nbsp;&nbsp; ...  &nbsp;&nbsp; ],  &nbsp;&nbsp; "code":200,  &nbsp;&nbsp; "msg":"success" }
 User发布的Moment列表，每个Moment包括发布者User和前3条Comment | 1.大量重复User，浪费流量和服务器性能 2.优化很繁琐，需要后端扩展接口、写好文档，前端/客户端再配合优化  {  &nbsp;&nbsp; "data":[  &nbsp;&nbsp;&nbsp;&nbsp; {  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "id":235,  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "content":"xxx",  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ...,  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "User":{  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "id":38710,  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "name":"Tommy"  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ...  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; },  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "Comment":[  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ...  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ]  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ...  &nbsp;&nbsp;&nbsp;&nbsp; },  &nbsp;&nbsp;&nbsp;&nbsp; {  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "id":470,  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "content":"xxx",  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ...,  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "User":{  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "id":38710,  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "name":"Tommy"  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ...  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; },  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "Comment":[  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ...  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ]  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ...  &nbsp;&nbsp;&nbsp;&nbsp; },  &nbsp;&nbsp;&nbsp;&nbsp; {  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "id":511,  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "content":"xxx",  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ...,  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "User":{  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "id":38710,  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "name":"Tommy"  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ...  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; },  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "Comment":[  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ...  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ]  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ...  &nbsp;&nbsp;&nbsp;&nbsp; },  &nbsp;&nbsp;&nbsp;&nbsp; {  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "id":595,  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "content":"xxx",  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ...,  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "User":{  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "id":38710,  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "name":"Tommy"  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ...  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; },  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "Comment":[  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ...  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ]  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ...  &nbsp;&nbsp;&nbsp;&nbsp; },  &nbsp;&nbsp;&nbsp;&nbsp; ...  &nbsp;&nbsp; ],  &nbsp;&nbsp; "code":200,  &nbsp;&nbsp; "msg":"success" } | 以上不同请求方式的结果:   ① 常规请求   {  &nbsp;&nbsp; "[]":[  &nbsp;&nbsp;&nbsp;&nbsp; {  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "Moment":{  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "id":235,  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "content":"xxx",  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ...  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; },  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "User":{  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "id":38710,  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "name":"Tommy"  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ...  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; },  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "Comment[]":[  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ...  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ]  &nbsp;&nbsp;&nbsp;&nbsp; },  &nbsp;&nbsp;&nbsp;&nbsp; ...  &nbsp;&nbsp; ],  &nbsp;&nbsp; "code":200,  &nbsp;&nbsp; "msg":"success" }   ② 省去重复的User   {  &nbsp;&nbsp; "User":{  &nbsp;&nbsp;&nbsp;&nbsp; "id":38710,  &nbsp;&nbsp;&nbsp;&nbsp; "name":"Tommy",  &nbsp;&nbsp;&nbsp;&nbsp; ...  &nbsp;&nbsp; },  &nbsp;&nbsp; "[]":[  &nbsp;&nbsp;&nbsp;&nbsp; {  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "Moment":{  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "id":235,  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "content":"xxx",  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ...  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; },  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "Comment[]":[  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ...  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ]  &nbsp;&nbsp;&nbsp;&nbsp; },  &nbsp;&nbsp;&nbsp;&nbsp; ...  &nbsp;&nbsp; ],  &nbsp;&nbsp; "code":200,  &nbsp;&nbsp; "msg":"success" }   ③ 不查询已获取到的User   {  &nbsp;&nbsp; "[]":[  &nbsp;&nbsp;&nbsp;&nbsp; {  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "Moment":{  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "id":235,  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "content":"xxx",  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ...  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; },  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "Comment[]":[  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ...  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ]  &nbsp;&nbsp;&nbsp;&nbsp; },  &nbsp;&nbsp;&nbsp;&nbsp; ...  &nbsp;&nbsp; ],  &nbsp;&nbsp; "code":200,  &nbsp;&nbsp; "msg":"success" }


1.base_url指基地址，一般是顶级域名，其它分支url都是在base_url后扩展。如base_url:http://www.google.com/ ，对应的GET分支url:http://www.google.com/get/ 。下同。 
2.请求中的key或value任意一个为null值时，这个 key:value键值对 被视为无效。下同。 
3.请求中的 / 需要转义。JSONRequest.java已经用URLEncoder.encode转义，不需要再写；但如果是浏览器或Postman等直接输入url/request，需要把request中的所有 / 都改成 %252F 。下同。 
4.code，指返回结果中的状态码，200表示成功，其它都是错误码，值全部都是HTTP标准状态码。下同。 
5.msg，指返回结果中的状态信息，对成功结果或错误原因的详细说明。下同。 
6.code和msg总是在返回结果的同一层级成对出现。对所有请求的返回结果都会在最外层有一对总结式code和msg。对非GET类型的请求，返回结果里面的每个JSONObject里都会有一对code和msg说明这个JSONObject的状态。下同。 
7.id等字段对应的值仅供说明，不一定是数据库里存在的，请求里用的是真实存在的值。下同。

 
 

##  3.对应关系总览 

###  3.1 操作方法 

  方法及说明 | URL | Request | Response
------------ | ------------ | ------------ | ------------
GET:   普通获取数据，  明文，  可用浏览器调试 | base_url/get/ | {  &nbsp;&nbsp; TableName:{  &nbsp;&nbsp;&nbsp;&nbsp; …   &nbsp;&nbsp; } }   {…}内为限制条件   例如获取一个id为235的Moment： {  &nbsp;&nbsp; "Moment":{  &nbsp;&nbsp;&nbsp;&nbsp; "id":235  &nbsp;&nbsp; } } | {  &nbsp;&nbsp; TableName:{  &nbsp;&nbsp;&nbsp;&nbsp; ...  &nbsp;&nbsp; },  &nbsp;&nbsp; "code":200,  &nbsp;&nbsp; "msg":"success" } 例如 {  &nbsp;&nbsp; "Moment":{  &nbsp;&nbsp;&nbsp;&nbsp; "id":235,  &nbsp;&nbsp;&nbsp;&nbsp; "userId":38710,  &nbsp;&nbsp;&nbsp;&nbsp; "content":"APIJSON,let interfaces and documents go to hell !"  &nbsp;&nbsp; },  &nbsp;&nbsp; "code":200,  &nbsp;&nbsp; "msg":"success"  }
HEAD:   普通获取数量，  明文，  可用浏览器调试 | base_url/head/ | {  &nbsp;&nbsp; TableName:{  &nbsp;&nbsp;&nbsp;&nbsp; …  &nbsp;&nbsp; }  }   {…}内为限制条件    例如获取一个id为38710的User所发布的Moment总数： {  &nbsp;&nbsp; "Moment":{  &nbsp;&nbsp;&nbsp;&nbsp; "userId":38710  &nbsp;&nbsp; } } | {  &nbsp;&nbsp; TableName:{  &nbsp;&nbsp;&nbsp;&nbsp; "code":200,  &nbsp;&nbsp;&nbsp;&nbsp; "msg":"success",  &nbsp;&nbsp;&nbsp;&nbsp; "count":10  &nbsp;&nbsp; },  &nbsp;&nbsp; "code":200,  &nbsp;&nbsp; "msg":"success" }   例如 {  &nbsp;&nbsp; "Moment":{  &nbsp;&nbsp;&nbsp;&nbsp; "code":200,  &nbsp;&nbsp;&nbsp;&nbsp; "msg":"success",  &nbsp;&nbsp;&nbsp;&nbsp; "count":10  &nbsp;&nbsp; },  &nbsp;&nbsp; "code":200,  &nbsp;&nbsp;  "msg":"success" }
POST_GET:   安全/私密获取数据， 非明文，  用于获取钱包等 对安全性要求高的数据 | base_url/post_get/ | 最外层加一个"tag":tag，其它同GET | 同GET
POST_HEAD:   安全/私密获取数量， 非明文，  用于获取银行卡数量等 对安全性要求高的数据总数 | base_url/post_head/ | 最外层加一个"tag":tag，其它同HEAD | 同HEAD
POST:   新增数据，  非明文 | base_url/post/ | {  &nbsp;&nbsp; TableName:{  &nbsp;&nbsp;&nbsp;&nbsp; …  &nbsp;&nbsp; },  &nbsp;&nbsp; "tag":tag }   {…}中id由服务端生成，不能传   例如一个id为38710的User发布一个新Moment： {  &nbsp;&nbsp; "Moment":{  &nbsp;&nbsp;&nbsp;&nbsp; "userId":38710,  &nbsp;&nbsp;&nbsp;&nbsp; "content":"APIJSON,let interfaces and documents go to hell !"  &nbsp;&nbsp; },  &nbsp;&nbsp; "tag":"Moment" } | {  &nbsp;&nbsp; TableName:{  &nbsp;&nbsp;&nbsp;&nbsp; "code":200,  &nbsp;&nbsp;&nbsp;&nbsp; "msg":"success",  &nbsp;&nbsp;&nbsp;&nbsp; "id":38710  &nbsp;&nbsp; },  &nbsp;&nbsp; "code":200,  &nbsp;&nbsp; "msg":"success" } 例如 {  &nbsp;&nbsp; "Moment":{  &nbsp;&nbsp;&nbsp;&nbsp; "code":200,  &nbsp;&nbsp;&nbsp;&nbsp; "msg":"success",  &nbsp;&nbsp;&nbsp;&nbsp; "id":120  &nbsp;&nbsp; },  &nbsp;&nbsp; "code":200,  &nbsp;&nbsp; "msg":"success" }
PUT:   修改数据，  非明文，  只修改所传的字段 | base_url/put/ | {  &nbsp;&nbsp; TableName:{  &nbsp;&nbsp;&nbsp;&nbsp; "id":id,  &nbsp;&nbsp;&nbsp;&nbsp; …  &nbsp;&nbsp; },  &nbsp;&nbsp; "tag":tag }   {…}中id必传   例如修改id为235的Moment的content： {  &nbsp;&nbsp; "Moment":{  &nbsp;&nbsp;&nbsp;&nbsp; "id":235,  &nbsp;&nbsp;&nbsp;&nbsp; "content":"APIJSON,let interfaces and documents go to hell !"  &nbsp;&nbsp; },  &nbsp;&nbsp; "tag":"Moment" } | 同POST
DELETE:   删除数据，  非明文 | base_url/delete/ | {  &nbsp;&nbsp; TableName:{  &nbsp;&nbsp;&nbsp;&nbsp; "id":id  &nbsp;&nbsp; },  &nbsp;&nbsp; "tag":tag }   {…}中id必传，一般只传id   例如删除id为120的Moment： {  &nbsp;&nbsp; "Moment":{  &nbsp;&nbsp;&nbsp;&nbsp; "id":120  &nbsp;&nbsp; },  &nbsp;&nbsp; "tag":"Moment" } | 同POST


1.TableName指要查询的数据库表Table的名称字符串。第一个字符为大写字母，剩下的字符要符合英语字母、数字、下划线中的任何一种。对应的值的类型为JSONObject，结构是 {...}，里面放的是Table的字段(列名)。下同。 
2."tag":tag 后面的tag是非GET、HEAD请求中匹配请求的JSON结构的key，一般是要查询的table的名称，由服务端Request表中指定。下同。 
3.GET、HEAD请求是开放请求，可任意组合任意嵌套。其它请求为受限制的安全/私密请求，对应的 方法、tag、结构 都必须和 服务端Request表中所指定的 一一对应，否则请求将不被通过。下同。 
4.POST_GET与GET、POST_HEAD与HEAD分别为同一类型的操作方法，请求稍有不同但返回结果相同。下同。 
5.在HTTP通信中，GET、HEAD方法一般用HTTP GET请求，其它一般用HTTP POST请求。下同。 
6.所有JSONObject都视为容器(或者文件夹)，结构为 {...} ，里面可以放普通对象或子容器。下同。 
7.每个对象都有一个唯一的路径(或者叫地址)，假设对象名为refKey，则用 key0/key1/.../refKey 表示。下同。

 

###  3.2 功能符 
 
 功能 | 键值对格式 | 使用示例
------------ | ------------ | ------------
 查询数组 | "key[]":{}，后面是JSONObject，key可省略。当key和里面的Table名相同时，Table会被提取出来，即 {Table:{Content}} 会被转化为 {Content} | [{"User[]":{"User":{}}}](http://139.196.140.118:8080/get/{"User[]":{"count":3,"User":{}}})，查询一个User数组。这里key和Table名都是User，User会被提取出来，即 {"User":{"id", ...}} 会被转化为 {"id", ...} 
 匹配选项范围 | "key{}":[]，后面是JSONArray，作为key可取的值的选项 | ["id{}":[38710,82001,70793]](http://139.196.140.118:8080/get/{"User[]":{"count":3,"User":{"id{}":[38710,82001,70793]}}})，查询id符合38710,82001,70793中任意一个的一个User数组
 匹配条件范围 | "key{}":"条件0,条件1..."，条件为任意SQL比较表达式字符串，非Number类型必须用''包含条件的值，如'a' | ["id{}":" 90000"](http://139.196.140.118:8080/get/{"User[]":{"count":3,"User":{"id{}":" 90000"}}})，查询id符合id\ 90000的一个User数组
 包含选项范围 | "key ":Object  =>  "key ":[Object]，key对应值的类型必须为JSONArray，Object类型不能为JSON |  ["contactIdList ":38710](http://139.196.140.118:8080/get/{"User[]":{"count":3,"User":{"contactIdList ":38710}}})，查询contactIdList包含38710的一个User数组
 远程调用函数 | "key()":"函数表达式"，函数表达式为 function(Type0:value0,Type1:value1...)。函数参数类型为Object或泛型时可省略类型，即 Object:value 改写为 value | ["isPraised()":"isContain(Collection:praiseUserIdList,userId)"](http://139.196.140.118:8080/get/{"Moment":{"id":301,"isPraised()":"isContain(Collection:praiseUserIdList,userId)"}})，请求完成后会调用 boolean isContain(Collection collection, Object object) 函数，然后变为 "isPraised":true 这种（假设点赞用户id列表包含了userId，即这个User点了赞）
 引用赋值 | "key@":"引用路径"，引用路径为用/分隔的字符串。以/开头的是缺省引用路径，从声明key所处容器的父容器路径开始；其它是完整引用路径，从最外层开始。  被引用的refKey必须在声明key的上面。如果对refKey的容器指定了返回字段，则被引用的refKey必须写在@column对应的值内，例如 "@column":"refKey,key1,..." | ["Moment":{  &nbsp;&nbsp; "userId":38710 }, "User":{  &nbsp;&nbsp; "id@":"/Moment/userId" }](http://139.196.140.118:8080/get/{"Moment":{"userId":38710},"User":{"id@":"%252FMoment%252FuserId"}})  User内的id引用了与User同级的Moment内的userId， 即User.id = Moment.userId，请求完成后  "id@":"/Moment/userId" 会变成 "id":38710
 模糊搜索 | "key$":"SQL搜索表达式"  =>  "key$":["SQL搜索表达式"]，任意SQL搜索表达式字符串，如 %key%(包含key), key%(以key开始), %k%e%y%(包含字母k,e,y) 等，%表示任意字符 | ["name$":"%m%"](http://139.196.140.118:8080/get/{"User[]":{"count":3,"User":{"name$":"%2525m%2525"}}})，查询name包含"m"的一个User数组
 正则匹配 | "key?":"正则表达式"  =>  "key?":["正则表达式"]，任意正则表达式字符串，如 ^[0-9]+$ ，可用于高级搜索 | ["name?":"^[0-9]+$"](http://139.196.140.118:8080/get/{"User[]":{"count":3,"User":{"name%253F":"^[0-9]%252B$"}}})，查询name中字符全为数字的一个User数组
 新建别名 | "name:alias"，name映射为alias，用alias替代name。可用于 column,Table,SQL函数 等。只用于GET类型、HEAD类型的请求 | ["@column":"toId:parentId"](http://139.196.140.118:8080/get/{"Comment":{"@column":"id,toId:parentId","id":51}})，将查询的字段toId变为parentId返回
 增加 或 扩展 | "key+":Object，Object的类型由key指定，且类型为Number,String,JSONArray中的一种。如 82001,"apijson",["url0","url1"] 等。只用于PUT请求 | "praiseUserIdList+":[82001]，添加一个点赞用户id，即这个用户点了赞
 减少 或 去除 | "key-":Object，与"key+"相反 | "balance-":100.00，余额减少100.00，即花费了100元
 逻辑运算 | &, \|, ! 逻辑运算符。 ① & 可用于"key&{}":"条件"等 ② \| 可用于"key\|{}":"条件", "key\|{}":[]等，一般可省略 ③ ! 可单独使用，如"key!":Object，也可像&,\|一样配合其他功能符使用 |  ① ["id&{}":">80000, 80000, 80000 & id  ② ["id\|{}":">90000, 90000, 90000, 90000 \| id  ③ ["id!{}":[82001,38710]](http://139.196.140.118:8080/head/{"User":{"id!{}":[82001,38710]}})，即id满足 ! (id=82001 \| id=38710)，可过滤黑名单的消息
 数组关键词 | "key":Object，key为 "[]":{} 中{}内的关键词，Object的类型由key指定 ① "count":Integer，指定查询数量，假设允许查询数组的最大数量为max，则当count在1~max范围内时，查询count个；否则查询max个  ② "page":Integer，指定查询页码，从0开始，一般和count一起用 ③ "query":Integer，指定查询内容 0-对象，1-总数，2-以上全部 总数关键词为total，和query同级，通过引用赋值得到，如 "total@":"/[]/total"  这里query及total仅为GET类型的请求提供方便，一般可直接用HEAD类型的请求获取总数 | ① 查询User数组，最多5个： ["count":5](http://139.196.140.118:8080/get/{"[]":{"count":5,"User":{}}})  ② 查询第3页的User数组，每页5个： ["count":5, "page":3](http://139.196.140.118:8080/get/{"[]":{"count":5,"page":3,"User":{}}})  ③ 查询User数组和对应的User总数： ["[]":{  &nbsp;&nbsp; "query":2,  &nbsp;&nbsp; "User":{} }, "total@":"/[]/total"](http://139.196.140.118:8080/get/{"[]":{"query":2,"count":5,"User":{}},"total@":"%252F[]%252Ftotal"})
 对象关键词，可自定义 | "@key":Object，@key为 Table:{} 中{}内的关键词，Object的类型由@key指定 ① "@about":true, 查询字段属性 ② "@column":"key0,key1...", 指定返回字段 ③ "@order":"key0,key1+,key2-..."，指定排序方式 ④ "@group":"key0,key1,key2..."，指定分组方式。如果@column里声明了Table的id，则id也必须在@group中声明；其它情况下必须满足至少一个条件: 1.分组的key在@column里声明 2.Table主键在@group中声明  ⑤ "@having":"function0(...)?valu0,function1(...)?valu1,function2(...)?value2..."，指定SQL函数条件，一般和@group一起用，函数一般在@column里声明 | ① 查询User表中字段的属性： ["@about":true](http://139.196.140.118:8080/get/{"User[]":{"User":{"@about":true}}})  ② 只查询id,sex,name这几列并且请求结果也按照这个顺序： ["@column":"id,sex,name"](http://139.196.140.118:8080/get/{"User":{"@column":"id,sex,name","id":38710}})  ③ 查询按 name降序、id默认顺序 排序的User数组： ["@order":"name-,id"](http://139.196.140.118:8080/get/{"[]":{"count":10,"User":{"@column":"name,id","@order":"name-,id"}}})  ④ 查询按userId分组的Moment数组： ["@group":"userId,id"](http://139.196.140.118:8080/get/{"[]":{"count":10,"Moment":%7B"@column":"userId,id","@group":"userId,id"}}})  ⑤ 查询 按userId分组、id最大值>=100 的Moment数组： ["@column":"userId,max(id)", "@group":"userId", "@having":"max(id)>=100"](http://139.196.140.118:8080/get/{"[]":{"count":10,"Moment":{"@column":"userId,max(id)","@group":"userId","@having":"max(id)>=100"}}}) 还可以指定函数返回名： ["@column":"userId,max(id):maxId", "@group":"userId", "@having":"maxId>=100"](http://139.196.140.118:8080/get/{"[]":{"count":10,"Moment":{"@column":"userId,max(id):maxId","@group":"userId","@having":"maxId>=100"}}})  ⑥ 从pictureList获取第0张图片： ["@position":0, //这里@position为自定义关键词 "firstPicture()":"get(Collection:pictureList,int:@position)"](http://139.196.140.118:8080/get/{"User":{"id":38710,"@position":0,"firstPicture()":"get(Collection:pictureList,int:@position)"}})  ...

 
 

##  4.快速上手 

###  4.1 下载后解压APIJSON工程 

Clone or download &gt; Download ZIP &gt; 解压到一个路径并记住这个路径。

#### 你可以跳过步骤4.2和步骤4.3，用我的服务器IP地址 139.196.140.118:8080 来测试服务端对客户端请求的返回结果。

###  4.2 导入MySQL table文件 

服务端需要MySQL Server和MySQLWorkbench，没有安装的都先下载安装一个。 
我的配置是Windows 7 + MySQL Community Server 5.7.16 + MySQLWorkbench 6.3.7 和 OSX EI Capitan + MySQL Community Server 5.7.16 + MySQLWorkbench 6.3.8，其中系统和软件都是64位的。

启动MySQLWorkbench &gt; 进入一个Connection &gt; 点击Server菜单 &gt; Data Import &gt; 选择刚才解压路径下的APIJSON-Master/table &gt; Start Import &gt; 刷新SCHEMAS, 左下方sys/tables会出现添加的table。

###  4.3 用Eclipse for JavaEE或IntellIJ IDEA Ultimate运行服务端工程 

如果以上编辑器一个都没安装，运行前先下载安装一个。 
我的配置是Windows 7 + JDK 1.7.0_71 + Eclipse 4.6.1 + IntellIJ 2016.3 和 OSX EI Capitan + JDK 1.8.0_91 + Eclipse 4.6.1 + IntellIJ 2016.2.5

#### Eclipse for JavaEE

1.导入 
File > Import > Maven > Existing Maven Projects > Next > Browse > 选择刚才解压路径下的APIJSON-Master/APIJSON(Server)/APIJSON(Eclipse_JEE) > Finish

2.运行 
Run > Run As > Java Application > 选择APIJSONApplication > OK

#### IntellIJ IDEA Ultimate

1.导入 
Open > 选择刚才解压路径下的APIJSON-Master/APIJSON(Server)/APIJSON(Idea) > OK

2.运行 
Run > Run APIJSONApplication

###  4.4 用ADT Bundle或Android Studio运行客户端工程 

可以跳过这个步骤，直接下载下方提供的客户端App。

如果以上编辑器一个都没安装，运行前先下载安装一个。 
我的配置是Windows 7 + JDK 1.7.0_71 + ADT Bundle 20140702 + Android Studio 2.2 和 OSX EI Capitan +（JDK 1.7.0_71 + ADT Bundle 20140702）+（JDK 1.8.0_91 + Android Studio 2.1.2），其中系统和软件都是64位的。

#### ADT Bundle

1.导入 
File > Import > Android > Existing Android Code Into Workspace > Next > Browse > 选择刚才解压路径下的APIJSON-Master/APIJSON(Android)/APIJSON(ADT) > Finish

2.运行 
Run > Run As > Android Application

#### Android Studio

1.导入 
Open an existing Android Studio project > 选择刚才解压路径下的APIJSON-Master/APIJSON(Android)/APIJSON(AndroidStudio)/APIJSONApp （或APIJSONTest） > OK

2.运行 
Run > Run app

###  4.5 操作客户端App 

选择发送APIJSON请求并等待显示结果。 
如果默认url不可用，修改为一个可用的，比如正在运行APIJSON服务端工程的电脑的IPV4地址，然后点击查询按钮重新请求。

 
 

##  5.其它 

###  5.1 相关推荐 
[APIJSON, 让接口和文档见鬼去吧！](https://my.oschina.net/tommylemon/blog/805459)

[仿QQ空间和微信朋友圈，高解耦高复用高灵活](https://my.oschina.net/tommylemon/blog/885787)

[3步创建APIJSON服务端新表及配置](https://my.oschina.net/tommylemon/blog/889074)

###  5.2 关于作者 
TommyLemon：[https://github.com/TommyLemon](https://github.com/TommyLemon) 

如果有什么问题或建议可以[提ISSUE](https://github.com/TommyLemon/APIJSON/issues)或者[发我邮件](https://github.com/TommyLemon)，交流技术，分享经验。 
如果你解决了某些bug，或者新增了一些通用性强的功能，欢迎[贡献代码](https://github.com/TommyLemon/APIJSON/pulls)，感激不尽^_^

###  5.3 下载试用客户端App 

仿微信朋友圈动态实战项目 
[APIJSONApp.apk](http://files.cnblogs.com/files/tommylemon/APIJSONApp.apk)

测试及自动生成代码工具 
[APIJSONTest.apk](http://files.cnblogs.com/files/tommylemon/APIJSONTest.apk)

###  5.4 更新日志 
[https://github.com/TommyLemon/APIJSON/commits/master](https://github.com/TommyLemon/APIJSON/commits/master)

###  5.5 点Star支持我，点Fork研究它 

[https://github.com/TommyLemon/APIJSON](https://github.com/TommyLemon/APIJSON)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)