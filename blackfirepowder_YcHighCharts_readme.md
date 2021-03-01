Highcharts是一个制作图表的纯Javascript类库，主要特性如下：

兼容性：兼容当今所有的浏览器，包括iPhone、IE和火狐等等；
对个人用户完全免费；
纯JS，无BS；
支持大部分的图表类型：直线图，曲线图、区域图、区域曲线图、柱状图、饼装图、散布图；
跨语言：不管是PHP、Asp.net还是Java都可以使用，它只需要三个文件：一个是Highcharts的核心文件highcharts.js，还有a canvas emulator for IE和Jquery类库或者MooTools类库；
提示功能：鼠标移动到图表的某一点上有提示信息；
放大功能：选中图表部分放大，近距离观察图表；
易用性：无需要特殊的开发技能，只需要设置一下选项就可以制作适合自己的图表；
时间轴：可以精确到毫秒
下载插件

Highcharts下载地址

http://www.highcharts.com/download

jquery下载地址

http://jquery.com/

1、需要引入的脚本
```
  
  
  
  
```
2、前端显示片段
```
$('#canvasDiv').highcharts({
            chart: {
                type: '@Model[0].Type'
            },
            title: {
                text:  '@Model[0].Title'
            },
            subtitle: {
                text: '@Model[0].Subtitle'
            },
            xAxis: {
                categories: @Html.Raw(Model[0].XAxis.CategoriesJson)
            },
            yAxis: {
                title: {
                    text: '@Model[0].YAxis.Title'
                },
                labels: {
                    formatter: function () {
                        return this.value + '次'
                    }
                }
            },
            tooltip: {
                crosshairs: true,
                shared: true
            },
            plotOptions: {
                spline: {
                    marker: {
                        radius: 4,
                        lineColor: '#666666',
                        lineWidth: 1
                    }
                }
            },
            series: @Html.Raw(Model[0].SeriesJson)
        });
```
3、控制器数据绑定片段
![](http://git.oschina.net/uploads/images/2015/0811/110236_561a282c_91726.png "控制器数据绑定片段")

演示效果如下：
![](http://git.oschina.net/uploads/images/2015/0811/110438_328319a7_91726.png "")
![](http://git.oschina.net/uploads/images/2015/0811/110458_8807917e_91726.png "")
![](http://git.oschina.net/uploads/images/2015/0811/110511_45c03b46_91726.png "")
----------------------------------------------------------------------------------
# YcHighCharts
Highcharts是一个制作图表的纯Javascript类库，自主封装.net图表框架，支持webform和mvc3以上

由元创商业科技（深圳）提供

官网：http://www.obo2o.cn/
blog：http://www.cnblogs.com/cheng5x

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)