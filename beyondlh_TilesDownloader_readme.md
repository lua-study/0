#TilesDownloader

# QQ交流群: 106802648

> 百度地图用这个: GMapProviders.BaiduMap
> 谷歌地图无偏移: GMapProviders.GoogleSatelliteMap
> 谷歌地图有偏移: GMapProviders.GoogleChinaSatelliteMap

## 百度地图核心代码就3个

> BaiduMapProvider.cs
> BaiduProjection.cs
> BaiduSateliteMapProvider.cs

# [打开看看](http://git.oschina.net/adodo1/TilesDownloader/tree/master/scr/GMap.Net/GMap.NET.Core/GMap.NET.MapProviders/Baidu?dir=1&filepath=scr%2FGMap.Net%2FGMap.NET.Core%2FGMap.NET.MapProviders%2FBaidu)

# 谷歌地图无偏移有2个有效的URL分别是(无偏移)

> URL1. http://mt1.google.cn/vt/lyrs=s&hl=en&x={0}&y={1}&z={2}
> URL2. http://khm1.google.com/kh/v={version}&hl=en&x={0}&y={1}&z={2}
>
> 例如1: http://mt1.google.cn/vt/lyrs=s&hl=en&x=105378&y=56408&z=17     例如2: http://khm1.google.com/kh/v=699&hl=en&x=105378&y=56408&z=17    PS: 地址1 自动获取最新的谷歌影像(无偏移)
> PS: 地址2 首先要通过 http://ditu.google.cn/maps/api/js?sensor=false&language=zh-cn 这个网址获取最新的地图版本
>     例如获取的json字符串里的https://khms1.google.com/kh?v=699\u0026hl=zh-CN\u0026gl=CN\u0026
>     最新的地图版本就是699 再把版本填写到URL2的v=后面就可以了
>     地址2 比 地址1 的优势在于可以获取历史版本的谷歌影像 被墙的几率少一点

# [谷歌地图下载脚本](https://github.com/adodo1/tilemaker)
> 1. 谷歌地图下载脚本可以批量快速下载谷歌地图
> 2. 并且可以直接导入ArcMAP里浏览
> 3. 可以将零散的瓦片封装成ArcServer的紧凑型bundle文件
> 4. 想了解更多使用方法在QQ群里讨论






 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)