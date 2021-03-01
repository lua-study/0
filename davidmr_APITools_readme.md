# APITools

### 程序说明
* 一个HTTP请求工具，类似于Postman
* 可以记录接口信息，方便选择接口 支持常见的HTTP请求方法
* 拥有中文提示,方便填写接口参数
* 规范的Json格式文档定义，方便导出接口信息到其他格式
* 可拓展其他功能，使用Java编写，简单方便

### 构建说明
* 1:执行git clone https://git.oschina.net/zzunet/APITools.git
* 2:根据系统类别修改pom.xml(程序使用SWT开发，需要根据系统和jvm版本修改pom.xml)
* 3:执行build.bat构建程序，构建完成后程序包将生成在target目录，譬如APITools-1.8-jar-with-dependencies.jar
* 4:切换到target目录，执行java -Dfile.encoding=UTF-8 -jar APITools-1.8-jar-with-dependencies.jar启动程序（建议使用作为文件默认编码方式）

### 常见问题说明
* 1：控制台里打印日志乱码，需要修改config/log4j.properties,将log4j.appender.CONSOLE.Encoding值改成GB2312
* 2：启动程序失败，此问题可能是因为使用的SWT版本和jdk版本不一致导致的，比如32位jdk必须使用32位的SWTjar包，请在pom.xml里修改后重新构建程序

### 联系作者
* QQ:793554262
* Email:793554262@qq.com
* Blog:www.itlaborer.com
* 微信:liudeweichina

### 已构建程序包下载
* [点击去下载](https://git.oschina.net/zzunet/APITools/attach_files)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)