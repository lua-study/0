* 默认配置名称：config.yml
* log配置格式
```
log:
  #can set output to file, others will be outputed to std
  output: std
  name: log.txt
  #level can be: all, debug, info,, warn, error, fatal
  level: all
  enable_line: true
```
* 启动需调用service.Start()方法

* fs配置格式
```
storage:
  #can be: local, aliyun
  kind: local 
  addr: ./storage
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)