# highcharts2javatag
通过自定义标签实现highcharts 3D图表展示，借鉴了Android适配器的思想，通过固定的数据源，展现相关图表，无需考虑图表内部实现。

**演示地址:**
http://dtmonitor.tunnel.qydev.com/highcharts2javatag/

官网地址：
https://projectlombok.org/

官网使用说明：
http://jnb.ociweb.com/jnb/jnbJan2010.html

java -jar lombok.jar

**Maven:**
```xml
 
     com.google.code.gson 
     gson 
     [2.6.2,) 
 
```

**3D条形(柱状)图Bar的Tag:**
```xml
	 
```

**3D条形(柱状)图Bar的数据格式:**		

	private List  xlist;
	
	private Map > ylist;
	
	
**3D饼状图Pie的Tag:**
```xml
	 
```

**3D饼状图Pie的数据格式:**		

	private Map  legendMap;
	
**折线图line的Tag:**
```xml
	 
```

**折线图line的数据格式:**		

	private List  xlist;
	
	private Map > ylist;

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)