#weather
读[www.weather.com.cn](http://www.weather.com.cn)数据的工具包

##使用简介
* 接口地址信息详见[weather.properties](http://git.oschina.net/kakotor/weather/blob/master/src/main/resources/weather.properties)
* 已生成的地址信息文件[locations.json](http://git.oschina.net/kakotor/weather/blob/master/src/main/resources/locations.json)

###读取天气信息 

```java
try {
    WeatherLastHour lastHour = WeatherReader.getLastHour("1010200");
    WeatherSixDay sixDay = WeatherReader.getSixDay("1010200");
    WeatherToday today = WeatherReader.getToday("1010200");
    
} catch (IOException e) {
    e.printStackTrace();
}
```
###生成地区信息文件

```java
LocationInfoBuilder builder = new LocationInfoBuilder();
builder.build();
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)