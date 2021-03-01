# red5-rtmp-push

#### 介绍

 获取视频流 进行人脸识别后推送到red5服务器（人脸识别技术由虹软®提供） 

 整个系统共有两个项目组成  
- [red5_hls 流媒体服务器是对red5服务器进行springboot构建，同时支持hls,rtsp等流的播放支持](https://gitee.com/endlesshh/red5_hls)
- [red5-rtmp-push 接受视频流并推送到服务器](https://gitee.com/endlesshh/red5-rtmp-push) 
#### 启用说明

1.主要是借用ifast框架,主要的服务类就一个,其他的都是多余的。

2.首先修改 resources/application-dev.yml 中的 red5.url : rtmp://red5ip/oflaDemo/ 改为你的red5服务器。

3.如果是打包成jar 要将 libarcsoft_face_engine_jni.dll,libarcsoft_face_engine.dll,libarcsoft_face.dll三个文件放到jar的同级目录下，然后在包路径下的命令窗口收入 java -jar 包名.jar

4.本项目已经全部集成到后台管理所以直接登录后台进行操作  

5.使用mysql数据库，用户名 admin 密码   1

6.问题：连接中断，需要有重启机制。需停止当前线程重新一个新的线程

7.人脸图片单独验证

8.因为Flash浏览器要不支持了，所以使用B站的技术方案livego和flv.js

9.配合[red5_hls 流媒体服务器](https://gitee.com/endlesshh/red5_hls)进行hls展示脱离flash,样例： templates/video/manage/view_push_http.html


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)