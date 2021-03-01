babylon
=======

巴比伦流媒体服务器，目前只支持rtmp协议
#如何使用#
```
package main

import (
    "babylon/rtmp"
	log "github.com/cihub/seelog"
	"runtime"
)


func main() {
  runtime.GOMAXPROCS(runtime.NumCPU())
  l := ":1935"
  err := rtmp.ListenAndServe(l)
  if err != nil {	
     panic(err)		
  }
  select {}
}
```
#用ffmpeg发布流媒体和播放示例#
* ffmpeg -i xxxx.mp4 -c:a aac -ar 44100 -ab 128k -ac 2 -strict -2 -c:v libx264 -vb 500k -r 30 -s 640x480 -ss 00.000 -f flv rtmp://127.0.0.1/live/xxxx
* ffplay -i rtmp://127.0.0.1/live/xxxx

#路线图#
* 2013.10.20 支持rtmp协议反向代理和转发功能          
* 2013.12.20 支持rtsp(h264/aac),hls(h264/aac)协议，也就是rtmp输入，rtmp、rtsp、hls同时输出 
* 2014.3.20 支持rtsp(h264/aac) 转发

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)