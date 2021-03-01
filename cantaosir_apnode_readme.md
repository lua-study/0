# apnode 
#### 项目介绍
Windows （或包括Linux MacOS）通过 NodeJS 管理服务的管理工具集 
Nginx，PHP，MySQL， 扩展，
Apache，Redis，MongoDB，FTP，Git，SVN

#### 软件目录架构 
使用 Winsw 将一些程序转为服务运行，  
\apnode\ahost 放默认网站文件 ，  
\apnode\.tool 放常用工具和一些配置文件 NotePad2  MiniThunder 已经内置
\apnode\apmanger 为C#管理工具，目前未开发，生产管理文件 apmanger.exe 当前仅为示例占坑  
运行库 vcredist 需要自行安装，PHP程序目录下有VisualStudio2012_vcredist_x64.exe  

#### 常用工具 
1. Git，
    > https://www.git-scm.com/download/win 官方下载首页  
    > https://github.com/git-for-windows/git/releases/download/v2.18.0.windows.1/Git-2.18.0-64-bit.exe 
2. TortoiseGit， 
    > https://tortoisegit.org/download/  官方下载首页 
    > https://download.tortoisegit.org/tgit/2.7.0.0/TortoiseGit-2.7.0.0-64bit.msi   
    > https://download.tortoisegit.org/tgit/2.7.0.0/TortoiseGit-LanguagePack-2.7.0.0-64bit-zh_CN.msi 中文包  
3. TortoiseSVN, 
	> https://tortoisesvn.net/downloads.html
3. 7Zip, 开源的解压缩工具， 没广告也不用破解，似乎这个热了后国内就出来好些压缩软件，
    > https://www.7-zip.org/download.html  
4. NotePad2-Mod, 记事本的替代软件, 
	> https://xhmikosr.github.io/notepad2-mod/  
	> https://github.com/XhmikosR/notepad2-mod/releases
5. MiniThunder， 迅雷小巧的下载工具， 
    > http://t.cn/zOY7u6X  
    > https://weibo.com/minithunder  
6. SysinternalsSuite,微软官方提供的管理工具 Process Explorer 和  Autoruns 比较常用
	> https://docs.microsoft.com/zh-cn/sysinternals/downloads/sysinternals-suite  
	
#### 补充环境 
1. JAVA ,   
    > http://www.oracle.com/technetwork/java/javase/archive-139210.html 建议 8u201 看说明尾号是奇数版的比偶数版的稳定
2. NODEJS，
	> https://nodejs.org/zh-cn/download/  
    > https://nodejs.org/dist/v12.13.0/node-v12.13.0-win-x64.zip  
    > https://nodejs.org/dist/v8.11.4/node-v8.11.4-x64.msi 旧版  
3. MySQL, 推荐5.7
    > https://cdn.mysql.com/archives/mysql-5.7/mysql-5.7.22-winx64.zip
4. Tomcat , 运行JSP，
    > https://tomcat.apache.org/download-80.cgi
5. Python, anaconda 集成 conda 包管理工具的Python的环境
	> https://www.anaconda.com/distribution/ 
#### 使用说明 
1. apnode, 为了方便开发环境搭建而准备的套件，默认放到 C: 下即可
2. 安装必备工具，下载的 MiniThunder， TortoiseGit，
3. NODEJS MySQL Java 按需到官方下载 
4. FileZillaClient 中包含了WinSCP 和 Putty ，FileZillaServer 为FTP服务
5. Redis Server 和 Memcache 版本是从网络上收集的
6. Apache 含 PHP54TS 和 subversion 
7. Nginx 配套使用 WinswPHP56x64NTS，含有较多插件 events,mongodb,redis,sphinx,wincache,xdebug,yaf,win32ps,
8. FRP Ngrok 集成方便一些测试
9. .tool 目录下有NODE 和 MySQL 的配置文件
10. start_nginx.cmd，start_apache.cmd，start_PHP56.cmd，是启动快捷方式
11. MysqlRoute 做测试读写分离用
12. apmanger 准备用C#写的管理工具，说不定也可以成为一个Apache Friends 工具套件

#### 在线工具推荐 
1. 菜鸟工具,
	> https://c.runoob.com/ 

#### 相关引用  
1. Winsw，方便的应用转服务工具
2. phpfpm 虽然有官方的fastcgi，但是看起来似乎这个更和谐
	
#### 参与贡献
1. Fork 本项目
2. 新建 Feat_xxx 分支
3. 提交代码
4. 新建 Pull Request
 

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)