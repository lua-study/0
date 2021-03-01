#gmfs

golang 基于 gridFs 的分布式文件服务

http://www.oschina.net/p/gmfs

[ gmfs 捐赠记录,感谢你们的支持！ ](http://git.oschina.net/juapk/gmfs/wikis/%E6%8D%90%E8%B5%A0%E8%AE%B0%E5%BD%95)

# Window 启动 mongodb 命令：

mongod.exe --dbpath "C:\Program Files\MongoDB\data"

# giraffe 启动：

go run giraffe start


# api 说明
--

code 		响应编码

1000		正常消息

1001		异常消息

1002		保存失败

1003		读取失败

1004		超过限制大小，默认小于80M

1005		图片涉黄

1006		不支持文件

--
message 	响应内容

1、code 为 1000 正常消息，时 message 为响应结果

2、其他情况为错误描述

--
rdm 		随机数（重置图片使用）

--
mime	文件展类型，例如 "image/jpeg" , "application/pdf" 等

--
suffix 		上传文件后缀



演示 demo 地址：http://localhost:1323/demo.html
----------------------------------------------
（1）、POST 上传
----------------------------------------------
地址：/upload.html

参数：file		文件属性名

参数：nude		可选（检查是否涉黄 true 是， false 否）

参数：online		可选（全局允许上线 online 为 false 不允许上线才生效，true 是， false 否）

参数：resetId 	可选（resetId 与 resetRdm 同时存在,替换指定图片）

参数：resetRdm 	可选（resetId 与 resetRdm 同时存在,替换指定图片）

演示地址：http://localhost:1323/upload.html

返回 JSON 例如：

```
{
    "code": "1000",
    "message": "55c83f2a07986a0838000003",
    "mime": "image/jpeg",
    "rdm": "L5Ap4",
    "suffix": ".jpg"
}
```

#（2）、GET 上传

地址：/proxy.html

参数：uri		文件地址

参数：nude		可选（检查是否涉黄 true 是， false 否）

参数：online		可选（全局允许上线 online 为 false 不允许上线才生效，true 是， false 否）

参数：resetId 	可选（resetId 与 resetRdm 同时存在,替换指定图片）

参数：resetRdm 	可选（resetId 与 resetRdm 同时存在,替换指定图片）

演示地址：http://localhost:1323/proxy.html?uri=http://p5.qhimg.com/dmt/490_350_/t01d49b7191cbc97c11.jpg

返回 JSON 例如：

```
{
    "code": "1000",
    "message": "55c83f2a07986a0838000003",
    "mime": "image/jpeg",
    "rdm": "L5Ap4",
    "suffix": ".jpg"
}
```

#（3）、显示（原样输出 byte 流）

地址：dispaly/:id.html?watermark=true

参数：id			唯一ID（上传成功 message 返回的字符串）

参数：watermark	可选（只对图片有效，全局设置不开启水印，请求可通过该参数打开水印 true 是， false 否）

演示地址：http://localhost:1323/dispaly/55c83f2a07986a0838000003.html

# 图片缩放处理 #

1、等比缩放 100 像素

http://localhost:1323/dispaly/55c83f2a07986a0838000003_100.html

2、缩放为 100x100 像素

http://localhost:1323/dispaly/55c83f2a07986a0838000003_100x100.html

注意！限制宽高大于 50 像素, 宽高小于2倍的实际像素。

#（4）、文件下载

地址：/download/:id.html?name=xx

参数：id			唯一ID（上传成功 message 返回的字符串）

参数：name		可选（文件名称，默认使用 id 命名）

演示地址：http://localhost:1323/download/55c83f2a07986a0838000003.html

		http://localhost:1323/download/55c83f2a07986a0838000003.html?name=20150806

#（5）、秒传（查询是否存在）

地址：/search/:md5/:size.html

参数：md5	文件 md5 值

参数：size	文件大小（单位 B 字节）

演示地址：http://localhost:1323/search/3fbef3c587cf53c88b282b614cad105f/34562.html

```
{
    "code": "1000",
    "message": "55c83f2a07986a0838000003",
    "mime": "image/jpeg",
    "rdm": "L5Ap4",
    "suffix": ".jpg"
}
```

#（6）、文件转正（开启文件失效功能，才需要转正）

地址：/online/:id/:rdm.html

参数：id		唯一ID

参数：rdm	随机数

演示地址：http://localhost:1323/online/55c83f2a07986a0838000003/L5Ap4.html

```
{
    "code": "1001",
    "message": true
}
```


Futures
====================
1、欢迎提出更好的意见，帮助完善 gmfs


开源赞助我(支付宝)
====================
![GitHub](https://raw.githubusercontent.com/leqwang/kisso/master/images/donate.png "开源赞助我(支付宝)")

copyright
====================
Apache License, Version 2.0


关注我
====================
![程序员日记](http://git.oschina.net/uploads/images/2016/0121/093728_1bc1658f_12260.png "程序员日记")



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)