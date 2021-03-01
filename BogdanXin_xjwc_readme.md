# 教务处评分系统

- [1.教务处评分系统-API](#1-教务处评分系统-API)

  - [1.1. tips](#11-tips)
  - [1.2. 登陆相关](#12-登录相关)
    - [1.2.1. 登陆](#121-登陆)
    - [1.2.2. 退出](#122-退出)
  - [1.3. 管理员系统](#13-管理员系统)
    - [1.3.1. 增加专家信息](#131-增加专家信息)
    - [1.3.2. 修改专家密码](#132-修改专家密码)
    - [1.3.3. 修改专家信息](#133-修改专家信息)
    - [1.3.4. 查询专家信息](#134-查询专家信息)
    - [1.3.5. 增加活动信息](#135-增加活动信息)
    - [1.3.6. 删除活动信息](#136-删除活动信息)
  	- [1.3.7. 修改活动信息](#137-修改活动信息)
  	- [1.3.8. 查询活动信息](#138-查询活动信息)
    - [1.3.9. 增加项目信息](#139-增加项目信息)
    - [1.3.10. 删除项目信息](#1310-删除项目信息)
  	- [1.3.11. 修改项目信息](#1311-修改项目信息)
  	- [1.3.12 查看所有项目](#1312-查看所有项目)
  	- [1.3.13 上传项目文件](#1313-上传项目文件)
  	- [1.3.14. 删除项目文件](#1314-删除项目文件)
  	- [1.3.15. 查询项目评分人数](#1315-查询项目评分人数)
  	- [1.3.16. 查看项目各个评分](#1316-查看项目各个评分)
  	- [1.3.17. 查看项目是否评分完成](#1317-查看项目是否评分完成)
  - [1.4. 专家系统](#14-专家系统)
    - [1.4.1. 修改专家密码](#141-修改专家密码)
    - [1.4.2. 修改专家信息](#142-修改专家信息)
    - [1.4.3. 查询活动信息](#143-查询活动信息)
  	- [1.4.4. 查看项目信息](#144-查看项目信息)
    - [1.4.5. 查看项目文件](#145-查看项目文件)
    - [1.4.6. 下载项目文件](#146-下载项目文件)
    - [1.4.7. 增加项目评分](#147-增加项目评分)
    - [1.4.8. 修改项目评分](#148-修改项目评分)
    - [1.4.9. 查看项目评分](#149-查看项目评分)
	- [1.4.10. 预览项目文件](#1410-预览项目文件)
	- [1.4.11. 查看活动下项目信息](#1411-查看活动下项目信息)


## 1.1. tips

- 用户类别：
  - 1 ： 管理员
  - 2 ： 专家
- code ：
  - 0 ： 正常
  - 1 ： 添加 message 字段展示相关信息。（例如：删除，更新，插入。会有 “删除成功/失败” 信息）
  - 2 ： 登录失败

- data ： 返回数据
- url ：host + url
  - example ：
    - host ： 
    - url ：/login
    - url :  


```json
{
  "projectId" : 139,
  "docUrl" : "https://www.nowcoder.com/discuss/398473?type=all&order=time&pos=&page=1"
}
```

- url意思是超链接，file意思是正常的文件，

```json
{
    "resultCode": 200,
    "message": "OK",
    "data": {
        "url": null,
        "file": [
            "http://140.143.194.109:8080/file/27-AbcFileTest/146-李希文的TestFile/视频.mp4",
            "http://140.143.194.109:8080/file/27-AbcFileTest/146-李希文的TestFile/excel.pdf",
            "http://140.143.194.109:8080/file/27-AbcFileTest/146-李希文的TestFile/趣味气象.pdf",
            "http://140.143.194.109:8080/file/27-AbcFileTest/146-李希文的TestFile/JAVA开发工程师.pdf",
            "http://140.143.194.109:8080/file/27-AbcFileTest/146-李希文的TestFile/林业可视化中期.pdf"
        ]
    }
}
```


## 1.2. 登陆相关

### 1.2.1. 登陆

- GET   / login?phone=11111111111&password=123456

return
```json
{
    "resultCode": 200,
    "message": "OK",
    "data": {
        "userId": "7249f5b5c62c47f0a72b9fa90b054fcc",
        "userName": "aaa",
        "password": "",
        "phone": "11111111111",
        "role": 1,
        "roles": [
            {
                "roleId": 2,
                "roleName": "doctor",
                "accesses": [
                    {
                        "accessId": 2,
                        "name": "doctor",
                        "url": "/"
                    },
                    {
                        "accessId": 3,
                        "name": "guest",
                        "url": null
                    }
                ]
            },
            {
                "roleId": 3,
                "roleName": "guest",
                "accesses": [
                    {
                        "accessId": 3,
                        "name": "guest",
                        "url": null
                    }
                ]
            },
            {
                "roleId": 1,
                "roleName": "admin",
                "accesses": [
                    {
                        "accessId": 2,
                        "name": "doctor",
                        "url": "/"
                    },
                    {
                        "accessId": 3,
                        "name": "guest",
                        "url": null
                    },
                    {
                        "accessId": 1,
                        "name": "admin",
                        "url": "/"
                    }
                ]
            }
        ]
    }
}
```

error

```json
{
    "resultCode": 500,
    "message": "输入的用户名或密码错误",
    "data": null
}
```
### 1.2.2. 退出

- GET  /logout

return 
```json
{
    "resultCode": 200,
    "message": "OK",
    "data": null
}
```

error

```json
{
    "resultCode": 500,
    "message": "登录超时或未登录,请重新登录",
    "data": null
}
```
## 1.3. 管理员系统

### 1.3.1. 增加专家信息
- POST   /register 
- payload

```json
{
	"userName" : "abc",
	"phone" : "33333333333",
	"password": "123456"
}
```

return

```json
{
	"resultCode": 200,
    "message": "OK",
    "data": 1
}
```

error
```json
{
    "resultCode": 500,
    "message": "该号码已被注册，请重试",
    "data": null
}
```

### 1.3.2. 修改专家密码
 - PUT   /updatePassword
 - payload

```json
{
	"phone" : "33333333333",
	"password": "12345678"
}
```

return

```json
{
	"resultCode": 200,
    "message": "OK",
    "data": 1
}
```

error
```json
{
    "resultCode": 500,
    "message": "修改失败",
    "data": null
}
```

### 1.3.3. 修改专家信息
- PUT   /updateInfo
- payload

```json
{
	"userId" : "383afb7f007e4d538fe5c4058ab5ef89",
	"userName" : "abcde"
}
```

return

```json
{
	"resultCode": 200,
    "message": "OK",
    "data": 1
}
```

error
```json
{
    "resultCode": 500,
    "message": "修改失败",
    "data": null
}
```
### 1.3.4. 查询专家信息
- POST  /user
- 密码没查,查也没用，存的是加密过的，这个是所有的，role=1代表管理员，role=2代表专家，必须传
- payload
```json
{
	"role" : "1"
}
```
return
```json
{
    "resultCode": 200,
    "message": "OK",
    "data": [
        {
            "userId": "1",
            "userName": "lxw",
            "password": null,
            "phone": "13091896371",
            "role": 1,
            "roles": null,
            "activity": null,
            "unit": null
        },
        {
            "userId": "3517a790ad8f4aa790eced70cfe024c6",
            "userName": "bbb",
            "password": null,
            "phone": "22222222222",
            "role": 1,
            "roles": null,
            "activity": null,
            "unit": null
        },
        {
            "userId": "7249f5b5c62c47f0a72b9fa90b054fcc",
            "userName": "aaa",
            "password": null,
            "phone": "11111111111",
            "role": 1,
            "roles": null,
            "activity": null,
            "unit": null
        }
    ]
}
```

error
```json
{
    "resultCode": 500,
    "message": "查询用户失败，请重试",
    "data": null
}
```

- POST  /userInfo
- 单独查一个用户的所有信息
- payload
```json
{
	"userId": "05d711f87e0e403d9243a93ed5d8b7b5"
}

```
return
```json
{
    "resultCode": 200,
    "message": "OK",
    "data": [
        {
            "userId": "05d711f87e0e403d9243a93ed5d8b7b5",
            "userName": "44",
            "password": "42c8ae37803bab71179c69270fc06765",
            "phone": "55",
            "role": 2,
            "roles": null,
            "activity": "33",
            "unit": "2"
        }
    ]
}
```

error
```json
{
    "resultCode": 500,
    "message": "查询用户失败，请重试",
    "data": null
}
```

### 1.3.5. 增加活动信息
- POST /activity
- **注意日期格式。。。年月日**。后面查询返回的也是这个格式，也是年月日
- PayLoad
```json
{
	"name" : "best",
 	"info" : "best",
 	"unit" : "best",
 	"list" : ["cc1dee9f141a4c0d83f043c12698d6f7"],
	"tag" : [
		{	
			"index" : 0,
			"lName" : "123",
			"value" : 80.0,
			"part" : 0.5
		},
		{	
			"index" : 1,
			"lName" : "123",
			"value" : 90.0,
			"part" : 0.5
		}
	],
	"type" : 1,
	"startTime" : "2020-03-31T16:00:00.000Z",
	"endTime" : "2020-03-31T16:00:00.000Z"
}
```

- return

```json
{
    "resultCode": 200,
    "message": "OK",
    "data": "新建活动成功"
}
```


### 1.3.6. 删除活动信息
- DELETE   /activity/{activityId}
- 同时删除这个活动内的所有项目文件
- return
```json
{
    "resultCode": 200,
    "message": "OK",
    "data": "删除活动成功"
}
```
error
```json
{
    "resultCode": 500,
    "message": "删除活动失败，请重新尝试!",
    "data": null
}
```


### 1.3.7. 修改活动信息
- PUT /activity
- payload
  - 注意activityId，一定要有，是根据这个条件进行更新的。
```json
{
	"activityId" : 5,
	"name" : "lxw1",
	"info" : "lxw1",
	"startTime" : "2020-02-12",
	"endTime" : "2020-02-12",
	"unit" : "lxw"
}
```


### 1.3.8. 查询活动信息
**支持下面所有字段的任意组合条件查询，例子如下**
- GET   , **`参数一定不要加双引号`**
- http://localhost:8090/activity?startTime=2020-02-08&endTime=2020-02-08&name=lxw 
  
    - "activityId": 数据库自增主键
    - "name":  活动名称 
    - "info":  活动信息          
    - "unit": "lxw"      活动单位

return 
返回的activityId在update和delete时会用到，页面可以不显示出来。
```json
{
    "resultCode": 200,
    "message": "OK",
    "data": [
        {
            "activityId": 20,
            "unit": "best",
            "name": "best",
            "startTime": "2020-03-31",
            "endTime": "2020-03-31",
            "tag": "[{\"index\":0,\"part\":0.5,\"value\":80},{\"index\":1,\"part\":0.5,\"value\":90}]",
            "type": null,
            "list": "[[{\"activity\":\"lxw\",\"password\":\"30f5f93f82e24d4d9c8dcf9db7852eed\",\"phone\":\"22222\",\"role\":2,\"unit\":\"2\",\"userId\":\"cc1dee9f141a4c0d83f043c12698d6f7\",\"userName\":\"11\"}]]",
            "info": "best"
        },
        {
            "activityId": 21,
            "unit": "best",
            "name": "best",
            "startTime": "2020-03-31",
            "endTime": "2020-03-31",
            "tag": "[\"cc1dee9f141a4c0d83f043c12698d6f7\"]",
            "type": null,
            "list": "[[{\"activity\":\"lxw\",\"password\":\"30f5f93f82e24d4d9c8dcf9db7852eed\",\"phone\":\"22222\",\"role\":2,\"unit\":\"2\",\"userId\":\"cc1dee9f141a4c0d83f043c12698d6f7\",\"userName\":\"11\"}]]",
            "info": "best"
        }
    ]
}
```

error
```json
{
    "resultCode": 500,
    "message": "没有该条件下的活动，请重新尝试!",
    "data": null
}
```


### 1.3.9. 增加项目信息
- POST   /project
- payload 

```json
{
	"name" : "abc",
	"info" : "abc",
	"unit" : "abc",
	"leader" : "abc",
	"score"  : 0,
	"activityId" : 1
}
```
return

```json
{
	"resultCode": 200,
    "message": "OK",
    "data": 1
}
```
error
```json
{
    "resultCode": 500,
    "message": "新建项目失败，请重新尝试!",
    "data": null
}
```
### 1.3.10. 删除项目信息
- DELETE   /project
- payload 
```json
{
	"projectId" : 2
}
```
return

```json
{
	"resultCode": 200,
    "message": "OK",
    "data": 1
}
```
error
```json
{
    "resultCode": 500,
    "message": "删除项目失败，请重新尝试!",
    "data": null
}
```
### 1.3.11. 修改项目信息
- PUT   /project
- payload 

```json
{
	"name" : "abc",
	"info" : "abc",
	"unit" : "abc",
	"leader" : "abc",
	"score"  : 0,
	"activityId" : 1,
	"projectId" : 2
}
```
return

```json
{
	"resultCode": 200,
    "message": "OK",
    "data": 1
}
```
error
```json
{
    "resultCode": 500,
    "message": "更新项目失败，请重新尝试!",
    "data": null
}
```
### 1.3.12. 查看所有项目
- POST   /pro
- payload 

```json
{
	"activityId" : 2
}
```
return

```json
{
    "resultCode": 200,
    "message": "OK",
    "data": [
        {
            "activityId": null,
            "leader": "x",
            "score": 2.0,
            "unit": "x",
            "name": "x",
            "projectId": 1,
            "info": "x"
        }
    ]
}
```
error
```json
{
    "resultCode": 500,
    "message": "查询项目出现异常，请重新尝试!",
    "data": null
}
```

### 1.3.13. 上传项目文件
- POST    /document/upload/{projectId}

- 注意，现在写的是，一个项目一个压缩包，只能有一个压缩包！！，如果要重复上传，需要先删除原先文件，再上传。

```json
{
    "resultCode": 200,
    "message": "OK",
    "data": "上传成功"
}
```


### 1.3.14. 删除项目文件
- DELETE   /document/del?projectId=1&name=压缩包.zip
  - name ：文件名字
- http://localhost:8090/document/del?projectId=1&name=压缩包.zip
- return
```json
{
    "resultCode": 200,
    "message": "OK",
    "data": "删除成功"
}
```


### 1.3.15. 查询项目评分人数
- GET   /scoreNumber

- payload
```json
{
	"projectId" : 2
}
```

return 
```json
{
    "resultCode": 200,
    "message": "OK",
    "data": 2
}
```

error
```json
{
    "resultCode": 500,
    "message": "查询评分失败，请重试",
    "data": null
}
```
### 1.3.16. 查看项目各个评分
- POST   /scoreList

- payload
```json
{
	"projectId" : 2
}
```

return 
```json
{
    "resultCode": 200,
    "message": "OK",
    "data": [
        {
            "scoreId": 1,
            "userId": "383afb7f007e4d538fe5c4058ab5ef89",
            "projectId": 2,
            "score": 90.0
        },
        {
            "scoreId": 2,
            "userId": "3517a790ad8f4aa790eced70cfe024c6",
            "projectId": 2,
            "score": 80.0
        }
    ]
}
```

error
```json
{
    "resultCode": 500,
    "message": "查询评分失败，请重试",
    "data": null
}
```

1.3.17. 查看项目是否评分完成

- POST   /scoreOver

- payload

  ```json
  {
  	"projectId" : 87
  }
  ```

- return 

  ```json
  {
      "resultCode": 200,
      "message": "OK",
      "data": true
  }
  ```

- error

  ```json
  {
      "resultCode": 500,
      "message": "查询失败，请检查活动是否存在,
      "data": null
  }
  ```

  

### 1.4. 专家系统

### 1.4.1. 修改专家密码
同1.3.1
### 1.4.2. 修改专家信息
同1.3.2
### 1.4.3. 查询活动信息

- GET   /activity/now?userId={userId}

- /activity/now?userId=cc1dee9f141a4c0d83f043c12698d6f7

- return 

  ```json
  {
      "resultCode": 200,
      "message": "OK",
      "data": [
          {
              "activityId": 10,
              "unit": "lxw",
              "name": "qwert",
              "startTime": "2020-03-12",
              "endTIme": "2020-04-12",
              "info": "qwert"
          }
      ]
  }
  ```

### 1.4.4. 查看项目信息


### 1.4.5. 查看项目文件
- GET    /document/search/{projectId}

- return
```json
{
    "resultCode": 200,
    "message": "OK",
    "data": "压缩包.zip"
}
```

### 1.4.6. 下载项目文件
- GET   /document/download/{projectId}/{name}
  - name : 文件名称
- http://localhost:8090/document/download/1/压缩包.zip

- return
成功直接就下载了。。

error

```json
{
    "resultCode":500,
    "message":"未查询到此文件",
    "data":null
}
```

### 1.4.7. 增加项目评分

- POST   /score

- payload

  ```json
  {
  	"userId" : "cc1dee9f141a4c0d83f043c12698d6f7",
  	"projectId" : 87,
  	"tag" : [
    		{	
    			"index" : 0,
    			"lName" : "123",
    			"part" : 0.5
    		},
    		{	
    			"index" : 1,
    			"lName" : "123",
    			"part" : 0.5
    		}
    	],
  	"message" : "真棒"
  }
  ```

  

- return 

  ```json
  {
      "resultCode": 200,
      "message": "OK",
      "data": 1
  }
  ```

- error

  ```json
  {
      "resultCode": 500,
      "message": "添加评分失败，请重试",
      "data": null
  }
  ```

  

### 1.4.8. 修改项目评分

- PUT   /score

- payload

  ```json
  {
  	"scoreId" : 4,
  	"score" : 91,
  	"message" : "真棒"
  }
  ```

- return

  ```json
  {
      "resultCode": 200,
      "message": "OK",
      "data": 1
  }
  ```

- error

  ```json
  {
      "resultCode": 500,
      "message": "修改评分失败或未评分，请重试",
      "data": null
  }
  ```

  

### 1.4.9. 查看项目评分

- POST    /scoreExist

- payload

  ```json
  {
  	"userId" : "cc1dee9f141a4c0d83f043c12698d6f7",
  	"projectId" : 87
  }
  ```

- return

  ```json
  {
      "resultCode": 200,
      "message": "OK",
      "data": 91.0
  }
  ```

- error

  ```json
  {
      "resultCode": 500,
      "message": "查询评分失败，请重试",
      "data": null
  }
  ```

  

### 1.4.10. 预览项目文件

### 1.4.10. 下载分析文件
大文件分片上传/多线程上传 : https://www.sohu.com/a/223553425_100012573
这个到时候再问

### 1.4.11 查看活动下项目信息

- GET /project/user?userId=cc1dee9f141a4c0d83f043c12698d6f7&activityId=15

- return 
```json
{
    "resultCode": 200,
    "message": "OK",
    "data": [
        {
            "activityId": 15,
            "leader": "11",
            "score": 0.0,
            "unit": "11",
            "name": "11",
            "projectId": 91,
            "isScored": "0",
            "info": "111"
        },
        {
            "activityId": 15,
            "leader": "11",
            "score": 0.0,
            "unit": "11",
            "name": "11",
            "projectId": 92,
            "isScored": "0",
            "info": "111"
        }
    ]
}
```

- error

  ```json
  {
      "resultCode": 500,
      "message": "查询项目出现异常，请重新尝试!",
      "data": null
  }
  ```
  
## 评分表相关

### 上传评分表

- POST /excel/upload

- payload
file = 。。。

### 获取所有评分表

- GET /excel/get

- return
返回表名列表
```json
  {
      "resultCode": 200,
      "message": "OK",
      "data": ["hahha","lalala"]
  }
  ```

### 生成excel表
  
- GET /excel/project-total/export/{projectId}/{excelName}
  
excelName就是上面查的名字。目前只有 “评审打分汇总表样表1.xls”

### 下载excel表

- GET /excel/project-total/download/{projectId}




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)