### java-optimization-and-debug-for-prod-env
### Java生产环境下性能监控与调优

开始时间 20180919  结束时间 20181003 耗时15天

**目录**

[1.0-技术栈总览](./1.0-技术栈总览.md)

[1.1-详细笔记-基于JDK命令行工具的监控](./1.1-详细笔记-基于JDK命令行工具的监控.md)

[1.2-详细笔记-基于JVisualVM的可视化监控](./1.2-详细笔记-基于JVisualVM的可视化监控.md)

[1.3-详细笔记-Btrace-Java动态、安全追踪（监控）工具](./1.3-详细笔记-Btrace-Java动态、安全追踪（监控）工具.md)

[1.4-详细笔记-Tomcat性能监控与调优](./1.4-详细笔记-Tomcat性能监控与调优.md)

[1.5-详细笔记-Nginx性能监控与调优](./1.5-详细笔记-Nginx性能监控与调优.md)

[1.6-详细笔记-JVM层GC调优](./1.6-详细笔记-JVM层GC调优.md)

[1.7-详细笔记-Java代码成优化(借助字节码分析问题)](./1.7-详细笔记-Java代码成优化(借助字节码分析问题).md)

[2-新的linux命令](./2-新的linux命令.txt)

[3-其他使用说明](./3-其他使用说明.txt)

#### 注：

1. 如果出现在windows上无法请求虚拟机中Linux中的不同网段的接口或者部署SpringBoot程序失败，
可以参考《[1.4-详细笔记-Tomcat性能监控与调优](./1.4-详细笔记-Tomcat性能监控与调优.md)》中 4.1.1.3 节。

2. 《[1.5-详细笔记-Nginx性能监控与调优](./1.5-详细笔记-Nginx性能监控与调优.md)》含有php安装和整合

3. 《[The Java® Virtual Machine Specification-Java SE 8 Edition](https://docs.oracle.com/javase/specs/jvms/se8/html/)》 

------------------------------------------ 

> 作者：[江节胜](https://www.baidu.com/s?wd=%E6%B1%9F%E8%8A%82%E8%83%9C%20%E8%83%9C%E8%A1%8C%E5%A4%A9%E4%B8%8B%E7%BD%91)

> 微信：**767000122  (欢迎添加好友)**

> Q Q ：596957738

> 个人网站：[tech.jiangjiesheng.cn](http://tech.jiangjiesheng.cn) 

> 联系邮箱：dev@jiangjiesheng.cn

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)