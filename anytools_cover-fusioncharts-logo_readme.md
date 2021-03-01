# cover-fusioncharts-logo
We Know,the free version of fusioncharts is always dsplay with a logo.
Ifound an easy method to cover the logo,just use a div to cover the logo's position.
It's just for study,don not suggest use it in an business project.
#dependency
use jquery.jsfusionchart.jsfusioncharts.theme.fint.js
  
  
  
#how to use
var html = '  ';
$("body").append(html);
var chartSpan = $("#chartContainer > span");
var chartPos = chartSpan.position();
//alert(chartPos.left+","+chartPos.top+","+chartSpan.height());
$("#overrideLogoDiv").css("left",chartPos.left+5)
$("#overrideLogoDiv").css("top",(chartPos.top+chartSpan.height()-20))

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)