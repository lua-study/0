##背景
我有一台VPS,每天会产生数据库备份.本着异地备份的原则,希望本地电脑同样有一份备份文件 
所以用C#写了这个控制台的备份程序. 
因为需求简单,所以这个程序就没有写递归来查看各个文件夹 
Ftp的操作类是网上找的.稍微修改了一点点bug

##配置文件说明
FtpServerIP:服务器地址  
FtpRemotePath:FTP文件夹路径(根目录就空着) 
FtpUserID:FTP账号 
FtpPassword:FTP密码 
BackupPath:本地同步的路径 
 
最后用windows的计划任务定时执行

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)