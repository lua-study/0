# Lua 流控工具说明

----
*如发现缺陷，或者有改进意见请联系我，mahaixing@gmail.com*

----
*文件说明*

1. `limiters`  
目录，包含所有限流规则，新增限流规则需要放到该目录中
2. `restry`  
目录，包含 openrestry 的 cookie 处理类，我安装的环境中没有这个类
3. `limit_conf.lua.sample`  
限流配置文件示例
4. `limit.lua`  
限流主文件，参考下方文档
5. `nginx.conf.test`  
测试的 openresty 配置文件，可以直接使用
6. `test*.lua`  
测试文件，可以作为示例参考
7. `utils.lua`  
工具方法文件
----

## 1. 思路
限流脚本的设计思路源于规则链，用户请求进入 nginx 后，请求会进入限流脚本配置的限流链，在链中的规则中逐个匹配处理，如果某条限流规则匹配此请求，那么将跳出规则链执行循环，返回被限流信息，除非此规则明确说明需要参考链中下一条规则。

## 2. 流控工具使用
需要编写限流脚本，脚本可以参考如下（`some_business_limit.lua`)：
```
    local conf = {
        redis = {...}
        some_limit_rule_1 = {...}
        some_limit_rule_2 = {...}
    }

    -- 如果不传 conf 那么会在 package.path 中寻找
    -- limit_conf.lua 文件
    local limit = require "limit":new(conf)
    funciton some_who_1(limit) 
        return true, "some_limit_rule_1"
    end

    function some_who_2(limit)
        local redis = limit:get_redis()
        -- some_redis_operation
        -- target find 

        if is_target then
            return true, "some_limit_rule_2"
        else
            return false
        end 
    end

    function some_message(limit, data)
        -- 返回页面
        limit.send_redirect("limit.html")

        -- 返回json
        limit.send_redirect("xxx.html", data)
    end

    limit:who({some_who_1, some_who_2}):execute()
```

在 nginx 的 http 块中配置 `package.path` 是的 lua 解释器可以找到脚本文件，在需要限流的 location 部分增加 `access_by_lua_file` 指定 lua 脚本（当然也可以使用`content_by_lua`），如：

```
    http {
        lua_package_path "/some_place/limit/limit-common/?.lua;;";

        server {
            location /some_url {
                access_by_lua_file /some_place/some_business_limit.lua;
            }
        }
    } 

```
## 3.配置文件
配置文件用来配置 redis 和限流规则链，参考 `limit_conf.lua.sample` 文件，其中：

1. redis 部分是固定名称，不要修改名称和结构
2. `default_rule` 是默认的规则链，在没有给 `who` 函数时会默认使用这个规则链，如果给了 `who` 函数，那么可以不配置它。
3. `xxx_rule` 自定义规则链
4. 每个规则连链下的属性的 key 值是 `limiters/xxx.lua` 中的每个文件名（去掉.lua）。根据业务需要配置

### 3.1 bucket
文件 `limiters/bucket.lua` 使用令牌桶进行限流，配置项：
* 需要在 nginx 配置文件中配置共享 dict，如：
    ```
        http {
            lua_shared_dict my_limit_conn_store 100m;

            server {
                location / {
                    ...
                }
            }
        }
    ```
* `bucket_dict_name`

    共享 dict 名，字符串，需要与 nginx 配置文件中一致

* `bucket_rate`

    限制请求速率，数字，比如 200 表示 200个请求每秒

* `bucket_burst = 0,`
    
    允许的突发速率，数字，比如 100 表示 允许在 200 个请求每秒的基础上突发 100 个请求每秒的量

* `bucket_target = ”ip“`

    限制的目标，字符串，只能配置为：ip 或者 uri
    
    *ip：* 表示针对客户端IP地址
    
    *uri：* 表示针对被请求的地址

### 3.2 cookie
文件 `limiters/cookie.lua`，基于 cookie 限流，配置项：

* `cookie_domain` cookie 所属域名，字符串 如： "example.com"

* `cookie_path` 路径，字符串，如 "/"
            
* `cookie_key`  cookie 键名，字符串，如："example_limit",

* `cookie__value `写入的 cookie 值，字符串，如："1",

### 3.3 date_range
文件 `limiter/date_range.lua`，基于时间范围限流，配置项：

* `start_datetime`
    
    起始时间，固定格式 table
    
    如： {year=2018, month=03, day=30, hour=0, min=0, sec=0},

            
* `end_datetime` 

    截止时间，固定格式 table
    
    如：{year=2018, month=04, day=30, hour=0, min=0, sec=0},
            
* `week_day`
    
    具体星期几
    
    可以是 table，如： {3,4,5}
    
    可以是整数，如：1（代表周一）
    
    无论是 table 还是整数，配置的数值必须在 1-7 之间

### 3.4 limiter
文件 `limiters/limiter`，无条件限流，所有目标请求均被限制，无配置项，给个空 table 即可，如：
```
    default_rule = {
        limiter = {}
    }
```

### 3.5 probablity
文件 `limiters/probability.lua`，概率限流，配置项：

* `probability_rate` 

    限流概率，整数，如：80 代表 80% 流量将被限制掉


## 4. 关键函数
### 4.1 限流目标，who 函数
在 nginx 的 location 块配置中，限流是针对 URL 配置的。但是具体限流的目标由于应用的不同各不相同，需要针对参数确定限流对象，比如：

1. 有些业务限流是基本匹配同一个URL，但是会根据请求的参数来匹配限流目标。
2. 有些是根据 redis 中保存的目标用户，再匹配请求中传递的目标客户来确定限流目标
3. 有些是根据保存在 redis 中的黑白名单进行限流

因此，在限流脚本中，需要具体业务实现 who 函数，who 函数用来确定当前请求是否是限流的目标请求。

* 比如根据 url 参数（或者 cookie），从 redis 中查找是否是黑名单
* 比如根据 url 参数（或者 cookie），从 redis 中找到是否属于限流地址
* 比如根据 url 参数（或者 cookie），确定是否为某个具体业务

`who` 函数的原型是：

```
    function some_who_func(limit) 
```

返回值最多 2 个，返回 true 时至少返回两个返回值，返回 false 时则无需返回另一个返回值，返回值说明：

1. boolean，当前请求是否是限流目标
2. table 包含以下数据
    1. rule: 字符串类型，适用此目标的规则名

        比如："xxx_rule"，如果为 nil 那么使用默认规则名 "default_rule"

    2. message: `function` 类型，适用此目标的返回 message 函数

        如果为nil，则使用默认的 message 函数 `default_message`，参考 `limit.lua`

    3. data: `table` 类型，可选的，需要传递给 message 处理的数据

        可以为 nil ，说明无数据需要 message 处理

who 函数可以有多个，作为 table 传给 limit ，比如：

```
    limit:who({who_func1, who_func2, who_func3})
```

也可以只有一个，比如：

```
    limit:who(who_func_single)
```

who 函数匹配到目标后，脚本会停止调用后续 who 函数。匹配到目标的 who 函数必须返回 true 以及 目标适用的限流链、适用的 message 函数、额外需要传递的数据，如果 who 函数返回 false ，那么限流脚本会调用下一个 who 函数寻找。

如果不配置 who 函数，那么 limit 会使用默认的 who 函数，返回默认的 `defualt_rule` 以及默认的 `default_message`。

### 4.2 message 函数
message 函数用于在请求限流后，返回响应数据给浏览器，message 函数的原型是：

```
    function some_message(limit, data)
```

其中：

1. limit 是主控类，可以从 limit 类或者配置信息，以及请求参数信息（GET 和 POST 传递的参数），参考 `limit.lua`
2. data 是匹配的 who 函数返回的，根据需要使用。

在 message 函数中可以根据业务需要输出 mime 头以及其他 http 控制头。

可以根据需要返回 json 数据、xml 数据或者其他形式的数据

可以仅仅跳转到指定页面。

*可以针对每个限流目标，指定一个 message 函数，参考 `who` 函数说明*

## 5. 扩展
如果有新的限流规则，可以扩展此脚本，在 `limiters` 目录下新建规则文件 `some_new_rule.lua`，文件需要参考以下模板：

```
    local assert = assert
    local utils = require "utils"

    local _M = require("limiters.limiter"):new()

    function _M:process_config() 

    end

    function _M:execute()

        -- 如果不需要限流当前请求
        return false

        -- 如果限流当前请求，不需要参考下一条规则
        return true, false

        -- 如果限流当前请求，需要参考下一条规则
        return true, true

    end

    return _M
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)