#wordfilter

配置文件
-----------------------------------------------------------------------------------
- 默认位置：`config/wordfilter.properties`
- 服务端口：默认`9119`，可通修改property参数`sardine.port=9110` 指定其他端口
- 应用授权：默认全部，修改property参数`security.apps`指定，多个app之间逗号分隔
- 注意：修改该文件需要重启服务器

敏感词字典
-----------------------------------------------------------------------------------
- 默认位置：`config/dics/*.dic`，该目录下所有`*.dic`文件都会被加载，默认utf-8编码，每一行是一个敏感词
- 修改配置：当对该目录下的文件作任意修改时，包括增删改任意文件或目录，都会自动重新加载。
- 过滤级别：`config/wordfilter.properties/wordfilter.level.*=dic1.dic,dic2.dic`指定级别，以及级别所对应的字典，多个字典逗号分隔。

日志格式
-----------------------------------------------------------------------------------
- 日志配置文件：`config/logback.xml`
- 日志文件目录：`logs/*.log`


服务接口
-----------------------------------------------------------------------------------

###1、内容过滤

**Path：**


```
    POST /security?appId=sardine&subject=word_filter
```

**Request:**

application/json

```
    {
        action:"动作类型", # verify | replace
        level:"过滤级别", # sms，通过properties文件中的过滤级别设置
        data:"待过滤内容"
    }
```

**Response:**
application/json
```json
    {
        "success": true,
        "result": {
            具体的返回值包装，请求类型不一样返回值包装不一样
        }
    }
```

**说明：**

wordfilter 分为 检查与替换两种模式：
- verify模式：非常严格，但可能造成误判，卖a国b  |  卖 * 国  | 卖   国 | 卖%#%*)()**#$$#$%%$%国  均可以解析出敏感词 卖国
- replace模式：较宽泛，只有卖国能匹配出

*verify会与用户交互，即使误判也可以人工编辑；replace模式如果误判后就是错误了。如果对上述规则有不同意见，请提出。*

**示例：**
```
    POST http://172.20.10.222:9110/security?appId=sardine&subject=word_filter
```
Request：
```
    {
        action:"verify",
        level:"all",
        data:"PcP气枪ll&/网&；卖；。。13423__205670。。国的世界  职65645业报;;;;仇下载体验"
    }
```
Response:
```
	{
	   "success": true,
	    "result": {
	        "illegalWords": [
	            "职业报仇",
	            "pcp气枪网",
	            "枪",
	            "气枪",
	            "卖国",
	            "13423205670"
	        ],
	        "legal": false
	    }
	}
```

使用建议
-----------------------------------------------------------------------------------

- 1、任何系统都不能保证100%可用，请调用方自行降级处理服务挂掉情况下的业务逻辑
- 2、经测试，上述接口主要耗时在建立网络连接，因此调用方务必保持http 长连接，即`connection: keep-alive`（http1.1默认）
- 3、建议使用`httpclient4.3+`的连接池来调用接口，不建议使用java 原生的HttpURLConnection ，示例代码片段如下：

```
	private void singleton() {

		final PoolingHttpClientConnectionManager connectionManager = new PoolingHttpClientConnectionManager();
		connectionManager.setMaxTotal(300);// 最大连接数
		connectionManager.setDefaultMaxPerRoute(30);// 每个host最大连接数

		final RequestConfig requestConfig = RequestConfig.custom()//
				.setConnectTimeout(2 * 1000)// 设置最大连接时间2s
				.setSocketTimeout(2 * 1000)// 设置最大数据传输时间2s
				.build();// 设置请求和传输超时时间

		closeableHttpClient = HttpClientBuilder.create()
				.setDefaultRequestConfig(requestConfig)
				.setConnectionManager(connectionManager)
				.setKeepAliveStrategy(new DefaultConnectionKeepAliveStrategy())//默认keep-alive
				.build();
	}
```

压力测试
-----------------------------------------------------------------------------------

- 硬件：8核 8G

- 字典大小：4144
- 测试文本大小：3.13KB


**10并发:** ab -k -n 1000 -c 10 -p swfjson "http://172.20.10.222:9110/security?appId=sardine&subject=word_filter"

```
    Concurrency Level:      10
    Time taken for tests:   0.575 seconds
    Complete requests:      1000
    Failed requests:        0
    Write errors:           0
    Keep-Alive requests:    1000
    Total transferred:      264000 bytes
    Total POSTed:           3451170
    HTML transferred:       168000 bytes
    Requests per second:    1738.78 [#/sec] (mean)
    Time per request:       5.751 [ms] (mean)
    Time per request:       0.575 [ms] (mean, across all concurrent requests)
    Transfer rate:          448.28 [Kbytes/sec] received
                            5860.19 kb/s sent
                            6308.47 kb/s total

    Connection Times (ms)
                  min  mean[+/-sd] median   max
    Connect:        0    0   0.1      0       2
    Processing:     2    6   2.7      5      27
    Waiting:        2    5   2.7      5      26
    Total:          2    6   2.7      5      27

    Percentage of the requests served within a certain time (ms)
      50%      5
      66%      6
      75%      7
      80%      7
      90%      8
      95%     10
      98%     15
      99%     17
     100%     27 (longest request)
```


**100并发:** ab -k -n 100000 -c 100 -p swfjson "http://172.20.10.222:9110/security?appId=sardine&subject=word_filter"

```
    Concurrency Level:      100
    Time taken for tests:   51.012 seconds
    Complete requests:      100000
    Failed requests:        0
    Write errors:           0
    Keep-Alive requests:    100000
    Total transferred:      26400000 bytes
    Total POSTed:           342041700
    HTML transferred:       16800000 bytes
    Requests per second:    1960.32 [#/sec] (mean)
    Time per request:       51.012 [ms] (mean)
    Time per request:       0.510 [ms] (mean, across all concurrent requests)
    Transfer rate:          505.39 [Kbytes/sec] received
                            6547.96 kb/s sent
                            7053.35 kb/s total

    Connection Times (ms)
                  min  mean[+/-sd] median   max
    Connect:        0    0   0.0      0       2
    Processing:     6   51  96.4     38    1357
    Waiting:        5   51  96.4     38    1356
    Total:          6   51  96.4     38    1357

    Percentage of the requests served within a certain time (ms)
      50%     38
      66%     43
      75%     49
      80%     54
      90%     71
      95%     82
      98%     94
      99%    108
     100%   1357 (longest request)
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)