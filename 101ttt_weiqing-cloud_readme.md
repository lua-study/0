# thanos-cloud

端口：
    nacos : 8848
    sentinel : 8181
    redis: 6379
    thans-cloud-auth-server : 9090
    thanos-gateway: 8890
    thanos-message-service:9091
    thanos-message-login-log:9092
    
     





启动sentinel
cd E:\sofeware\Sentinel\sentinel-dashboard\target
java -Dserver.port=8181 -Dcsp.sentinel.dashboard.server=localhost:8181 -Dproject.name=sentinel-dashboard -jar sentinel-dashboard.jar


启动rocketmq
cd E:\sofeware\rocketmq-all-4.2.0-bin-release\bin
mqnamesrv.cmd -n 127.0.0.1:9876

cd E:\sofeware\rocketmq-all-4.2.0-bin-release\bin
mqbroker -n 127.0.0.1:9876




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)