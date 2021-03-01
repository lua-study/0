#smart-config
基于smart-boot构建的配置中心系统，以Redis作为数据持久化

##系统依赖
1. Redis
2. NodeJs(本人的node版本为5)
3. Java8

##项目部署
1. 修改application-dev.properties,配置(redis地址`spring.redis.host`)、(redis密码`spring.redis.password`)、(缓存名`redis.cacheName`)
2. 运行Bootstrap.java启动服务端
3. 目录切换至htdocs,并执行readme.md文件内的命令
4. 在htdocs目录下执行gulp start,打开浏览器访问http://localhost:3000/build/tenant.html
![键值对](kv.png)

![租户](tenant.png)
##推荐项目
- [smart-socket](https://git.oschina.net/smartdms/smart-socket)
- [smart-sosa](https://git.oschina.net/smartdms/smart-sosa)
- [maven-mybatisdalgen-plugin](https://git.oschina.net/smartdms/maven-mybatisdalgen-plugin)
- [smart-boot](https://git.oschina.net/smartdms/smart-boot)

##关于作者
Edit By [Seer](http://zhengjunweimail.blog.163.com/)  
E-mail:zhengjunweimail@163.com  
QQ:504166636 
Update Date: 2016-06-03

##捐赠
![微信捐赠](wx.png)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)