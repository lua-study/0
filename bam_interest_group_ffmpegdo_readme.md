# ffmpegdo  windows环境直播推流拉流项目

- 1.项目组成为nginx，ffmpeg,web三部分。
- 2.nginx推流服务器，项目中为nginx-1.7.11.3-Gryphon，已经配置好。
- 2.1CommandOption类下
NGINX_RTMP("cmd /k D: && cd D:\\DockerVSBoot\\ffmpegdo\\nginx-1.7.11.3-Gryphon && nginx.exe -c conf\\nginx-win-rtmp.conf")
这个地址需改成你nginx推流服务器所放的地址，这个不包括在yml配置项中。
- 3.ffmpeg已经放入gitee附件中上传了，需配置环境变量。
- 4.页面模板使用的MDUI,项目中为自行组件组合搭建。
- 5.交互使用的fetch 2.0.4[https://cdn.bootcss.com/fetch/2.0.4/fetch.js]首页关闭直播你可以当成一个例子。
- 6.部分配置代码相关放入doc目录下。


# 启动步骤

1. nginx和FFmpeg配置好后【路径、ip、环境变量、测试视频等等】。
2. 右键启动FfmpegdoApplication
3. 右键启动NginxRtmpService
4. 访问http://localhost:9090
5. http://localhost:9090/rpush?roomid=zhuhaobamr
6. http://localhost:9090/hpush?roomid=zhuhaobamh
7. 5和6就是live与hls的例子了，直接地址栏回车
8. 刷新首页点击直播列表第一列的直播间
9. 或者点击首页“直播菜单页”，超链接事件在图片上，点击文字遮罩层无效
10. 经测试hls和live均ok，推流不是很稳定，请f12多刷新几次
11. 另：本人使用的是QQ浏览器版本10.2.1，依赖的内核为chrominum63\IE11.285

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)