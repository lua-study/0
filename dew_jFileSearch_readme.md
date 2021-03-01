# jFileSearch

#### 项目介绍
该项目是基于java的文档检索系统，支持office,txt,pdf等文件的主流办公文件的全文检索，以及在线展示，一处维护处处查看。应对的是某些企业文档较多，查找文档困难以及文档共享内容延迟的情况，解决个人文档版本内容不一致等问题；
#### 系统有三级过滤
1. 第一级文件夹过滤：只查找想查找的目录 
2. 第二级文档库全文检索过滤： 通过检索文档内容对内容进行一次过滤 
3. 第三级前端二次过滤： 检索结果太多，前端二次过滤 
通过以上三级过滤精准命中目标文档，前后端精心优化，一次性加载10万个节点可稳定检索，经测试文件名过滤速度比windows快很多倍；
#### 系统截图
检索页面
![](https://gitee.com/cangjingge/jFileSearch/raw/master/doc/search.jpg)
文件查看页面
![](https://gitee.com/cangjingge/jFileSearch/raw/master/doc/viewFile.png)
#### windows一键部署包
写了个一键部署包地址为https://share.weiyun.com/5X8ZjTB
使用时，安装好liboffice配置好config下面的jfsSetting.json中的文档资源路径fileSourceDir和视图资源路径fileViewDir；点击start.bat即可启动。通过浏览器直接访问127.0.0.1:8080即可，用户名admin密码000000
#### 软件架构
系统功能模块主要分1.数据分析，2.数据检索，3.数据展示
parent为父模块，为了扩展性，数据分析模块（file2text）,数据展示模块(file2view),数据检索(fileSearch)均为独立模块开发，
其他模块为常规业务模块
![](https://gitee.com/cangjingge/jFileSearch/raw/master/doc/JFileSystem.png)
#### 安装教程

1. 安装jdk8路径不要有中文也不要有括号
2. elasticsearch5或者以上版本，配置使用默认端口即可
3. 安装redis使用默认端口即可
4. 安装LibreOffice 6 记得配置文件中要配置libreoffice的安装路径，否则启动会报错
5. 在realmDB.json中的文档库中，配置文档库模式，并配置源文件路径和视图文件存路径即可开始启动项目了
#### 使用说明
1. 配置文档库目录，和视图库目录（jfsSetting.json中的searchLibs，每个用户可以指定一个文档库）remoteRepositoryMode指的远程文档库模式，目前支持svn和none(本地管理)
2. web下面Application#main是启动入口
3. 启动后直接访问127.0.0.1即可访问
4. 使用用户名密码:admin/000000登陆系统
5. 初次使用如果是svn模式先检出文件，然后点击格式化系统；如果是本地模式之间格式化系统即可。
#### 项目规划
1. 增加文档库维护功能，目前是基于svn进行文档库维护的（已经完成）
2. 增加文档内容权限控制，这一项可能会影响性能，需要有合理的方案
3. 增加更多类型的文件支持
#### 注意事项
1. 文件查看如果出现乱码问题，应该是缺少字体库导致的，可以自己往系统中导入响应的字体即可解决
2. 格式化系统权限比较高。默认配置种只给了超级管理员。请注意权限配置
3. 还有问题可以查看wiki或者联系我
#### 联系我

1. 网站  www.qqxh.net
2. email zhangsen@protonmail.com
3. qq 9528326

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)