# 短链接生成器

## 前言
在这个营销的时代，短链接和二维码是企业进行营销中非常重要的工具，不仅仅是缩短了链接，而且还可以通过扩展获得更多的数据，诸如点击数、下载量、来源以及时间等等。

网上搜寻了一下比较有名有U.NU和0x3.me，但前者只能统计点击次数，而且不能修改链接，后者功能丰富，但确是收费商业网站。

## 环境搭建
本安装指南将帮助您安装Polr 2.0的最新版本Polr 2.0。Polr 是一个开源软件、世界上最好的语言，功能还算强大。
#### 功能包括
- 修改缩短的域名
- 统计功能(来源，时间)
- API支持
- 二维码生成

## 安装实例
[世界上最好的语言搭建短链接及统计功能](https://blog.52itstyle.com/archives/2563/)

## API代码案例
```
package com.itstyle.shorturl;

import java.util.HashMap;
import java.util.Map;
/**
 * 生成短链接 、自行配置后端服务 https://blog.52itstyle.com/archives/2563/
 * @author 小柒2012
 */
public class ShortUrlUtil {
	
	public static String urlToRequest = "https://polr.52itstyle.com/api/v2/action/shorten";
	
	public static String createShortUrl(String url){
		 Map  parameters = new HashMap ();
		 parameters.put("key", "0");
		 parameters.put("url", url);
		 return HttpClientHelper.requestBodyString(urlToRequest, parameters);
	}
    public static void main(String[] args) {
    	String url = "https://mp.weixin.qq.com/debug/wxadoc/dev/api/api-live-player.html";
    	url = createShortUrl(url);
    	System.out.println(url);
    	System.out.println("生成二维码地址:D:\\itstyle.png");
    	QrcodeUtil.createQrcode(200,200,url,"png","D:\\itstyles.png");
	}
}
```

## 二维码对比

#### 转换前
![转换前](https://gitee.com/uploads/images/2018/0320/183012_d20aa3c9_87650.png "itstyle.png")

#### 转换后
![转换后](https://gitee.com/uploads/images/2018/0320/183032_182ea8de_87650.png "itstyles.png")

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)