#AuthServer

参考oauth2.0, 基于jfinal2.0,jfinal-ext2-1.0,jfinal-ext-3.1.4.

实现了三个功能点

- authorize： 此阶段主要获取code
- access_token：  此阶段获取accessToken;
- refresh_token此阶段更新accessToken;

####authorize 请求参数说明
	
- response_type: 必须为code;
- scope: 为系统定义的范围；
- state : 为系统定义的state;
- client_id : 为系统分配的client_id，具体规则自定义；

####authorize 返回参数说明

- code : 系统下方的code；
- state : 请求参数中的state;
- scope : 请求参数中的scope;

#####access_token 参数说明
	
- response_type : 必须为 token;
- grant_type : 必须为 access_token;
- code : authorize下发的code；
- client_id ： 系统分配的client_id；
- client_secret ： 系统分配的client_secret；
- username ： 用户名；
- password : 用户密码；
- scope: 为系统定义的范围；
- state : 为系统定义的state;


#####access_token 返回参数说明

- access_token ： token值；
- expires_in ： 过期时间；
- refresh_token ： 下次用于刷新token的refresh_token；
- scope: 为系统定义的范围；
- state : 为系统定义的state;


#####refresh_token 参数说明

- response_type : 必须为token;
- grant_type : 必须为refresh_token；
- refresh_token ： access_token下发的refresh_token；
- client_id ： 系统分配的client_id；
- client_secret ： 系统分配的client_secret；
- username ： 用户名；
- password : 用户密码；
- scope: 为系统定义的范围；
- state : 为系统定义的state;

#####refresh_token 返回参数说明

与access_token返回相同


#### 错误返回参数
	
- error ： 错误信息；
- error_description : 错误描述；
- scope: 为系统定义的范围；
- state : 为系统定义的state;

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)