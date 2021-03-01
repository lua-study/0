### c2blog多人博客系统
采用围城多人博客开源框架，开源详情见围城多人博客
#### 服务器搭建
使用阿里云的centos7作为服务器进行搭建，搭建过程：首先搭建mysql+maven+tomcat+jdk8+nginx +git
的环境，然后通过git将代码pull到linux本地，然后编写自动化发布脚本，实现自动进行maven 的自动编译打包，以及将打好的war包
移到tomcat目录下，然后重启tomcat的功能。最后配置nginx进行反向代理，这样大大加快了静态资源的加载速度。大致过程就是如此，其中的
一些详细的配置由于内容过多就不在说明。


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)