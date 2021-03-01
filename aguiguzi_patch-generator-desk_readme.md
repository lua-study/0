#  **patch-generator-desk** 【技术QQ群：456742016】

项目增量补丁包神器：全自动web增量打包发版，支持git/svn，支持多模块项目。
- author : aaron
- [项目地址：https://gitee.com/hackempire/patch-generator-desk](https://gitee.com/hackempire/patch-generator-desk)
- [empire团队地址：https://gitee.com/organizations/hackempire/](https://gitee.com/organizations/hackempire/)
### empire宣言
- ###          打造帝国最强无敌武士套装！来吧！加入帝国军团，一起征服这个世界！ 

### 软件下载

- 	可执行.exe文件以及使用的相关教程请到附件中下载！
### 软件介绍

- 	本软件是empire团队打造的一款用于application/web项目增量打包的全自动发版部署工具。
### 功能介绍：

	1.GIT服务器增量打包;
	2.GIT日志增量打包;
	3.SVN服务器增量打包;
	4.SVN日志增打包;

### 历史轨迹
-     1.修复控制台无法显示操作日志的bug-----2018-05-01 18:48

### 使用教程：

	通用配置部分
		 1.项目名称：必须填写本地项目的文件名；
		 2.项目路径：必须填写项目的本地路径；
		 3.输出目录：必须填写增量包的输出路径；
		 4.项目类型：必须选择项目类型是单模块项目还是多模块项目；
		 5.sourceMapper表：sourceDir：源码目录,targetDir：.class目录、源文件目录；patchDir：打包后放置的目录
		 6.配置按钮：点击导入项目打包的配置（配置必须以.xml结尾）
		 7.保存按钮：点击保存当前项目打包的配置（配置必须以.xml结尾）

	GIT服务器增量私有配置部分
		 1.GIT本地URL路径：对应项目在本地的.git目录；例如D:\Users\Administrato\patch\git\.git
		 2.GIT范围版本：要打包的GIT提交版本范围；例如：757212d，544515f

	SVN服务器增量私有配置部分
		 1.SVN URL路径：对应项目在SVN服务器的地址；例如https://xxxxx/svn/scrm/tags/ump20170420_chery_pc
		 2.SVN范围版本：要打包的SVN提交版本范围；例如：14431，14439
		 3.修正路径：从svn服务器获取的增量路径中可能包含多余的在本地不存在的目录；例
                   如：/tags/ump20170420_chery_pc/src/main/webapp/WEB-INF/views/cherrywcc/wccchrescue/list.jspx
		   可以设置该值为 /tags:将其替换为空,/tags为需要替换的路径,:后面的空表示将/tags去掉;还可以将其设
                   置/tags/ump20170420_chery_pc:ump ,表示本地项目文件名为ump
		 4.SVN账户：svn服务器的账户
		 5.SVN密码：svn服务器的密码
		 6.排除版本：svn版本范围内需要排除掉的不用发版的版本号,多个版本以逗号分隔；

	GIT日志增量私有配置部分
		 1.GIT日志路径：对应的git提交日志存放的本地路径；
		   该路径或得方式可以通过右键点击项目-Team-show in history-视图中会显示提交的版本，选择需要发布的某个版本拷贝
                   右下角的本次版本的提交路径存入GIT提交日志即可。
		   例如 patch-generator/src/main/java/com/empire/patch/generator/GeneratePatchExecutor.java
		        patch-generator/src/main/java/com/empire/patch/generator/GitPatchGenerator.java

	SVN日志增量私有配置部分	  
		 1.SVN日志路径：对应SVN提交日志存放的本地路径；
		   日志记录方式，提交SVN后控制台会输出提交日志，将其拷贝到.txt结尾的日志文件中保存起来，用于发版
		   内容实例：(注意日志需顶格记录)

commit -m "1.服务点评bug修复2.道路救援bug修复3.全屏报表(二阶)bug修复"      
    Sending        D:/SpringRooWorkSpace/ump20170420_chery_pc/src/main/webapp/WEB-INF/views/cheryreport/RegAndAuthResult.jsp
    Transmitting file data ...
    Committed revision 14471.
### **相关项目** 

1.  [emsite分布式开源系统生态圈](https://gitee.com/hackempire/emsite-parent)
1.  [分布式服务框架Dubbo](https://github.com/apache/incubator-dubbo)
1.  [Emsite-patch-generator](https://gitee.com/hackempire/patch-generator-parent)
1.  [Emsite-patch-desk](https://gitee.com/hackempire/patch-generator-desk)
### **软件效果图** 
![增量打包神器桌面版](https://gitee.com/uploads/images/2018/0501/203654_cbe498db_302505.png "_BJ8NS6R@(3MWDPSPJ6MQ5U.png")


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)