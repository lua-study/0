# miniVoice

* 注册

 ```
    url:  /api/register
    POST
    参数：
       user_name    用户名称 -- 必填
       user_pass    密码     -- 必填,最小6位数
       mobile       手机号码
       nicname      实名
    返回：
        {
            "code": 0,
            "message": "Successful"
        }   
    
```
* 登陆
```
    url:  /api/login
    POST
    参数：
       user_name    用户名称 -- 必填
       user_pass    密码     -- 必填,最小6位数
    返回：
       {
           "code": 0,
           "message": "Successful",
           "data": {
               "token": "eyJpdiI6IlJXSzg1RnVicWc3Y3JJR0xcL1wvYjVjdz09IiwidmFsdWUiOiJVaW9tNUF4ZGtPb0ZuVGlNK24wa2NRPT0iLCJtYWMiOiJkNTlkMjM2NDVjMDliNDc3MGE2Y2M3YjEzMGRhZWNjZWY3OGViZGJiNTk5N2NkYTU4OTk2Mjk5YzY1MDhmNTk2In0=",
               "user": {
                   "user_id": 9,
                   "user_name": "test1666",
                   "mobile": null,
                   "nicname": null,
                   "picture": null,
                   "update_time": "2018-10-21 20:03:12",
                   "status": 5
               }
           }
       } 
```
* 获取内容列表
```
    url:  /api/get
    header  添加authorization 登陆的时候获取的token
    GET
        参数：
           user_id    -- 必填
           limit     每个页面的数量默认15
           page      第几页默认1
        返回：
        {
            "code": 0,
            "message": "Successful",
            "data": [
                {
                    "id": 59301,
                    "text": "گاۋ شۇجياڭ ، باشقا ئايال كىشىگە يېقىن كەلگەنلىكىڭىزنى بىلگەن بولسام ، سىز بىلەن ھەرگىز توي قىلمايتتىم !\r\n",
                    "voice_url": null,
                    "type": 1,
                    "user_id": 10,
                    "update_time": "2018-10-21 23:18:02"
                },
                {
                    "id": 59557,
                    "text": "پاراخودتا روسىيەلىك 15 ماتروس ۋە قىممىتى بىر مىليون دوللاردىن ئاشىدىغان ياغاچ ماتېرىياللىرى بار ئىكەن .\r\n",
                    "voice_url": null,
                    "type": 1,
                    "user_id": 10,
                    "update_time": "2018-10-21 23:18:02"
                }
            ],
            "count": 600
        }
        
* 备注：总页数获取方法  (count / limit)

```
* 提交数据
```
     url:  /api/set
     header  添加authorization 登陆的时候获取的token
     POST
         参数：
            id   用get获取的资源id -- 必填
            voice file 声音文件    -- 必填
         返回：
     {
         "code": 0,
         "message": "Successful"
     }
```

 

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)