# mail

### 功能目前已经完好

~~给树莓派用的,定时查询ip, 目前存在的问题: idea运行正常,maven打包后运行报错:~~
```
Exception in thread "Timer-0" java.lang.NoClassDefFoundError: javax/mail/Address
        at com.yyq.App.begin(App.java:66)
        at com.yyq.App.access$000(App.java:16)
        at com.yyq.App$Task.run(App.java:33)
        at java.util.TimerThread.mainLoop(Timer.java:555)
        at java.util.TimerThread.run(Timer.java:505)
Caused by: java.lang.ClassNotFoundException: javax.mail.Address
        at java.net.URLClassLoader.findClass(URLClassLoader.java:382)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:418)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:355)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:351)
        ... 5 more
```

~~暂时无解,再看吧 :(~~

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)