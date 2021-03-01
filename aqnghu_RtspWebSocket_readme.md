

# RtspWebSocket
这是一个在h5播放摄像头的项目，解决无插件的情况下播放的问题
可以参看我的博客介绍:https://my.oschina.net/chengpengvb/blog/1832469


## Usage

1.项目目录下执行: 
     node websocket.js supersecret 8081 8082 
2.打开cmd执行(播放第一个摄像头): 
    ffmpeg -i "你的rtsp" -q 0 -f mpegts -codec:v mpeg1video -s 800x600 http://127.0.0.1:8081/supersecret/live1 
3.打开cmd执行(播放第二个摄像头): 
    ffmpeg -i "你的rtsp" -q 0 -f mpegts -codec:v mpeg1video -s 800x600 http://127.0.0.1:8081/supersecret/live2 
4.打开view-stream.html看效果 
 
## Developing



### Tools

Created with [Nodeclipse](https://github.com/Nodeclipse/nodeclipse-1)
 ([Eclipse Marketplace](http://marketplace.eclipse.org/content/nodeclipse), [site](http://www.nodeclipse.org))   

Nodeclipse is free open-source project that grows with your contributions.


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)