    simpleImageTool又一个简单、好用的图片格式转换、缩放水印叠加等功能的纯Java图片工具库。
    simpleImageTool的由来，近期需要用到图片处理，通过网上的图片流直接进行缩放水印叠加等，需要一个纯java的处理库，在网上找一下没有符合我的库，要么是太老很多还是jdk1.6以前的，要么是功能不够好。找到阿里的simpleimage功能还算完善，1.7环境下想使用很麻烦，还要搞JAI的包，在改simpleimage（JPG图片处理相关的用新的ImageIO方式处理已经改好)时发现我不需要那么多功能而且有的功能还不完善，改好估计比造个小轮子还麻烦，所以就造了一个小轮子，抄了些simpleimage的代码 :laughing:  :laughing: 1. 1. 1. 这里是列表文本。
    特点：1、使用超级简单，链方式，图片缩放，旋转、水印一次性搞定
          2、支持格式目前算比较全面的
          3、gif支持算开源中算好的，完善待续（gif4J算很不错的，就是闭源收费）。
          4、支持读取的格式：jpeg、tif、icns、WBMP、targa、ico、TARGA、psd、JPG、wbmp、PNG、JPEG、tga、tiff、CUR、BMP、SGI、GIF、TIF、TIFF、bmp、jpg、TGA、PSD、png、ICNS、ICO、cur、gif、sgi
          5、支持写入式：BMP、tif、jpeg、WBMP、GIF、TIF、TIFF、jpg、bmp、JPG、wbmp、png、PNG、JPEG、gif、tiff、

使用说明：
1、图片格式转换： 
   SimpleImageTool.of(图片地址或者InputStream流)
                  .toFile(new File("c:/img/test/t2.gif"));
  格式转根据输出文件的后缀来确定， 比如psd图片转成 .png   toFile(new File("*****.png")）
2、缩放：a、同时指定宽高缩放，可以通过lockScale(true) //锁定比例，差的部分用bgcolor的颜色来填充,不设置透明,不锁定就拉伸图片，图片会变形
        b、定宽 高度自动
        c、定高 宽度自动
        d、按给定scale比例缩放 
   
       SimpleImageTool.of(is)
		      .size(600, 600)  //指定固定的宽高
		      .width(480)      //定宽
		      .height(380)     //定高
                      .rotate(30)      //旋转						
                      .lockScale(true) //锁定比例，差的部分用bgcolor的颜色来填充 不设置透明
		      .scale(0.2d)     //缩放比例
		      .bgcolor(Color.blue)
		      .gray(true)      //转换成黑白图片
		      .toFile(new File("c:/img/test/t2.gif"));   
    这些参数最后的优先级越高。 比如设了size(600,600) 再设置width(480)  那么起初size()不起作用，之所以有这需求，文章中经常需要定宽的图片按比例自动。       
3、裁切：比如.cut(800, 1300)先把图片尺寸根据比例最短缩放到800宽 或者 1300宽 再裁切中间的800，1300区域

4、水印叠加 
 a、文字水印
 WatermarkParameter watermark = new WatermarkParameter().addWaterText("测试测试测试")
				.postion(Positions.CENTER) 内置位置
				.rotate(20f) 旋转
				.color(Color.blue) 字体颜色
				.opacity(0.2f);    透明度
 通过上面的参数设置  postion内置了几个位置，也可以直径通过.point(x,y)指定坐标位置 
 b、图片水印 水印图片超过目标图片就缩小到四分之一
 BufferedImage watermarkImage = ImageIO.read(new FileInputStream("/images/1.gif"));
		WatermarkParameter watermark = new WatermarkParameter().addWaterMarkImage(watermarkImage)
				.postion(Positions.CENTER)
				.rotate(20f)
				.opacity(0.2f);
c.多个水印加入
  .watermark(watermark)
  .watermark(watermark2) 
5、图片质量控制 主要用于jpg、gif
.writeParam(new WriteParameter().dpi(200)  //图片精度
                       .quality(0.9F)      //图片质量越大质量越好文件就越大
            )



使用介绍文章：https://my.oschina.net/u/157306/blog/1477320


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)