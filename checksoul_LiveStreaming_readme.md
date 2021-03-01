一个Java实现的基于Red5的直播服务器！

- 支持直播数据的实时保存
- 支持视频数据的转码
- 支持视频文件水印的添加

 **操作说明（Java环境是必要的）：** 
1. 在附件列表中下载Red5服务容器：
![输入图片说明](https://git.oschina.net/uploads/images/2017/0421/110253_c40f96b1_440636.jpeg "在这里输入图片标题")
2. 解压前面下载的压缩文件， 会得到一个名叫red5-server-1.0.6-RELEASE的文件夹；
3. 打开此文件夹，里面的目录结构如下图：
![输入图片说明](https://git.oschina.net/uploads/images/2017/0421/110621_bf3ed31c_440636.jpeg "在这里输入图片标题")
4. 如果是Windows操作系统，双击red5.bat文件；如果是Linux类操作系统，则在终端中运行red5.sh；
5. 如果前面四个步骤没问题，red5服务就已经开启了，里面有些demo可以用作测试，像什么直播功能用里面的demo就可以完成；
6. LiveStreaming只是添加了部分功能，如果你想运行这个项目的话，直接将这个项目下载到本地，导入到eclipse中，然后用eclipse打成war包，放入webapps目录下，重启red5服务即可；
7. 如果此项目运行成功后，浏览器访问地址为： **http://ip地址:端口号（默认5080）/项目名/live** ；
   rtmp推流地址为： **rtmp://ip地址:端口号(默认1935)/项目名/随便给串字符** ；
   端口号可在conf目录下的 **red5.properties** 文件中查找修改；

备注： **导出的war包，需用解压软件解药到webapps目录下，然后启动red5容器！** 

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)