#简介

基于OpenResty，本程序即为部署在其上的分流限流控制脚本，基于配置策略进行工作，也可以通过管理URI实时调整配置生效


#包括几个部分

lua_scripts  用于部署到OpenResty的Lua脚本，脚本插入点见nginx/conf/nginx.conf

lualib       用于部署到OpenResty的Lua库脚本，包括实现控制所需要的各种工具lua库文件

nginx/conf/nginx.conf  OpenResty的配置文件

lua_ext      安装依赖的扩展，包括uuid_ext,cookie_ext

deps         依赖的第三方库，uuid_ext依赖的uuid库源代码

#安装

1, 安装OpenResty

2, 安装uuid_ext和cookie_ext

3，把lua_scripts，lualib 拷贝到OpenResty安装的根目录下


#配置说明

lualib/ddtk/limit_policy.json
注意：该文件必须对于OpenResty的Worker进程运行用户有写权限。
{
    "version" : 1472000000,
    "enable_limit" : true,
    "personal_key" : "offline",
    "personal_qps" : 8,
    "entire_qps"   : 50,
    "entire_bucket": 200,
    "secret_key"      : "abcdefgsalt",
    "root_secret_key" : "123456789",
    "max_access_interval_secs" : 3600,
    "cookie_domain" : ".topdomain.com",
    "cookie_path" : "/",
    "deny_url"  : "http://192.168.1.110/deny",
    "login_url" : "http://192.168.1.116/login",
    "access_token_key_name" : "some_biz_token",
    "remote_user_type" : 0,
    "filters_top_logic_op" : "and",
    "filters" : [
        "read_params",
        "single_qps",
        "ip_black_list",
        [
            ["entire_qps", "reset_access_token"],
            ["check_root_token", "check_access_token", "reset_access_token"]
        ]
    ],
    "enable_split" : true,
    "spliters" : [
        "simple"
    ]
}

参数	        说明
version	        配置的版本号，直接使用1970以来的时间秒值就可以，为了更新生效，必须是递增的
enable_limit	限流开关，true表示打开，false表示关闭
enable_split	分流开关，true表示打开，false表示关闭
personal_key	个人用户标识方式，默认为offline，offline使用可以区分离线用户的方式，ip使用终端IP，token使用登录后的根令牌
personal_qps	单用户QPS
entire_qps	    全局QPS
entire_bucket	超过全局QPS允许的最大突发量
secret_key	    访问令牌的加密key，这个值在一个业务集群里保持一致即可
root_secret_key	根令牌的加密key，这个要与登录系统保持一致
max_access_interval_secs	最大的访问间隔时间，单位是秒
cookie_domain	在PC模式下，写Cookie的domain值
cookie_path	在PC模式下，写Cookie的path值
deny_url	在PC模式下，限流的重定向友好页面URL，要求目标URL可以处理URL参数returnurl，这个参数表示重试返回的地址
login_url	在PC模式下，检查无效根令牌的重定向登录URL
access_token_key_name	访问令牌的名字
remote_user_type	处理的终端类型
filters_top_logic_op   限流规则表达式的顶级逻辑关系，默认为and
filters	               限流规则表达式，这里是用递归列表的形式来表达的，逻辑关系是交替变化的，可以通过[]来改变逻辑关系
spliters	           分流器列表，如果有一个分流器得到了一个分流目标，则后续的分流器就不会被执行了
	

#特性

1，分流功能，方便对后端服务器进行线上的AB测试

2，限流功能，基于逻辑表达式方式的定义的过滤器集合，支持复杂的嵌套定义

3，降级功能，对于被限流的请求，如果具备降级配置，则会重定向到降级URL

4，分流限流和其他配置都支持线上直接通过访问控制URL进行修改，实时生效

5，分流器和限流过滤器都支持用户自己的扩展，遵守接口并且放入特定目录即可


#控制URL

1，更新策略  /update_limit_policy   
HTTP POST + JSON 
比如：关闭分流和限流
Request body:::
{
    "version" : 1472000002,
    "enable_limit" : false,
    "enable_split" : false
}

2，查询策略  /query_limit_policy
HTTP GET 

3，更新其他配置  /update_shared_memory
HTTP POST + JSON 
比如：增加降级配置
Request body:::
{
    "dic_name":"degrade_url_mapping",
    "operation":"insert",
    "records" : [
        {
            "key"   : "/query/user",
            "value"  : "http://backup.some.com/query/user"
        },
        {
            "key"   : "/query/logo",
            "value"  : "http://backup.some.com/query/logo"
        }
    ]
}


#联系
堂吉诃德 421093703@qq.com



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)