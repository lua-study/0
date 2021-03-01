### 项目动态修改Properties（运行时）
 
 
 
 **把agent通过jps出来的进程id用命令把jar包注入到jvm里（Attaching Java Agent）** 

```java -jar dynamic-agent-1.0.2-SNAPSHOT-jar-with-dependencies.jar 79056 /Users/steven/temp/dynamic-agent-1.0.2-SNAPSHOT-jar-with-dependencies.jar ```
 
 
 

1. 默认会占用本地9999端口 目前还未加入配置端口项
2. 这里需要指定服务器的tools.jar 因为VirtualMachine类的工具在这个jar里
3. dynamic-agent-1.0.2-SNAPSHOT-jar-with-dependencies.jar是项目打完包后的(已经加入tools.jar 如果想用自己本地tools.jar请用1.0.1版本)
4. LoadAgent 46623 /Users/steven/temp/dynamic-agent-1.0.2-SNAPSHOT-jar-with-dependencies.jar
	- LoadAgent 是指定要调用的类 这里参数默认配置它即可
	- 46623 是进程号
	- /Users/steven/temp/dynamic-agent-1.0.2-SNAPSHOT-jar-with-dependencies.jar 指定项目打包后的jar包路径和上面的jar包一样


 
 
 

### 注意：
- 如果你的生产jdk是小于当前agent的jdk一定要降到比生产小，不要问为什么。你懂得。

- 此项目只能修改系统的properties配置。

- 默认通过两种方式修改支持jconsole通过操作修改和telnet方式修改。



 **将agent attach进入到你到项目进程** 
![输入图片说明](https://gitee.com/coderunning/dynamic-property/raw/master/pic/2.png "在这里输入图片标题")

 **查看成功标示** 
![输入图片说明](https://gitee.com/coderunning/dynamic-property/raw/master/pic/3.png "在这里输入图片标题")

 **jsonsole控制台（链接到你启动到项目）** 
![输入图片说明](https://gitee.com/coderunning/dynamic-property/raw/master/pic/4.png "在这里输入图片标题")

 **这是项目中写死到MBean（com.steven:type=NewBiAgentManagement）找到并配置动态属性值** 
![输入图片说明](https://gitee.com/coderunning/dynamic-property/raw/master/pic/5.png "在这里输入图片标题")

 **设置详细：** 
- 第一步：
![输入图片说明](https://gitee.com/coderunning/dynamic-property/raw/master/pic/6.png "在这里输入图片标题")
- 第二步：
![输入图片说明](https://gitee.com/coderunning/dynamic-property/raw/master/pic/7.png "在这里输入图片标题")

 **通过telnet的方式：** 
![输入图片说明](https://gitee.com/coderunning/dynamic-property/raw/master/pic/8.png "在这里输入图片标题")

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)