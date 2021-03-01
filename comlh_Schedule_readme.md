# quartz是单例模式
请看AddServlet和DeleteServlet两个servlet为两个不同的线程。然而获得的scheduler为同一个对象。
# 程序运行逻辑
访问http://localhost:8080/schedule/add?addjob=job1,job2，产生两个任务，会显示当前获得的scheduler对象。

访问http://localhost:8080/Schedule/delete?deletejob=job1，删掉一个任务，会显示当前获得的scheduler对象。

访问http://localhost:8080/Schedule/delete?deletejob=job2，删掉一个任务，会显示当前获得的scheduler对象。

此时不同线程中创建的任务，都被清空了，可以再次访问http://localhost:8080/schedule/add?addjob=job1,job2，产生两个任务，会显示当前获得的scheduler对象。此例说明schedule为单例模式。


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)