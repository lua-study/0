### **请直接下载附件**
```
/** Created by postbird on 2016/4/1.  ...*/
/**
 *      @postbird
 *      1、本插件采用js编写，可直接将函数复制到个人js文件，减少get请求数
 *      2、author：powered by postbird
 *      3、email： ptbird@yeah.net
 *      4、site：http://www.ptbird.cn
 *      5、license : MIT
 * */
/**
 *  函数使用说明：
 *      1、直接调用函数  TimeDifference()
 *          返回说明： 返回距离当前的时间差
 * */
function timeDifference(tmpTime) {
    var mm=1000;//1000毫秒 代表1秒
    var minute = mm * 60;
    var hour = minute * 60;
    var day = hour * 24;
    var month = day * 30;
    var ansTimeDifference=0;//记录时间差
    var tmpTimeStamp = tmpTime ? Date.parse(tmpTime.replace(/-/gi, "/")) : new Date().getTime();//将 yyyy-mm-dd H:m:s 进行正则匹配
    var nowTime = new Date().getTime();//获取当前时间戳
    var tmpTimeDifference = nowTime - tmpTimeStamp;//计算当前与需要计算的时间的时间戳的差值
    if (tmpTimeDifference  = 1) {
        return tmpTime;                 //大于一个月 直接返回时间
    } else if (DifferebceWeek >= 1) {
        ansTimeDifference= parseInt(DifferebceWeek) + "个星期前";
    } else if (DifferebceDay >= 1) {
        ansTimeDifference = parseInt(DifferebceDay) + "天前";
    } else if (DifferebceHour >= 1) {
        ansTimeDifference = parseInt(DifferebceHour) + "个小时前";
    } else if (DifferebceMinute >= 1) {
        ansTimeDifference = parseInt(DifferebceMinute) + "分钟前";
    } else {
        ansTimeDifference = "刚刚";
    }
    return ansTimeDifference;
}

```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)