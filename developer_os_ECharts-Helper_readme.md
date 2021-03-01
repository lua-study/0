# ECharts-Helper

#### 项目介绍
# echart-helper是什么？
echart-helper是一款辅助echarts开发的jQuery插件，能够帮助开发者快速构建echart图表。


#### 安装教程

引入jquery、echarts及echarts.helper三个文件即可
~~~
  
  
  
~~~


#### 实现原理

* 将 echarts 各类通用配置预先放入插件中，减少后续相关配置信息的写入，同时，任意内容均可通过配置进行覆盖（可完全复制使用echarts原生格式）。
* 将后端数据自动格式化成 echarts 所需格式，减少数据再次整理的过程。


#### 实现功能

* html标签绑定数据，渲染图表
* js调用生成图表
* 异步请求url渲染图表
* 配置使用主题
* 可自定义基础配置模版


#### 使用说明

> 完整使用说明请前往看云：https://www.kancloud.cn/qw_xingzhe/echart-helper/668005

> 以下为部分使用说明

html
~~~
  
~~~
js（后续js部分标签绑定与此处相同，皆省略）
~~~
$('body').EChartHelper();
~~~
![](images/screenshot_1529676402976.png)

2. js调用渲染

html
~~~
  
~~~
js
~~~
var drawData = {
    echart_data     : [{"title":"基础知识","get_score":11},{"title":"加分知识","get_score":12},{"title":"未分组","get_score":8}],
    echart_config   : {title:"分组得分占比图",type:"pie",name_key:"title",value_key:"get_score"}
};
$('.canvas-box echart-canvas-01').drawEChart(drawData);
~~~

3. js 简单定义数据

html
~~~
  
~~~
js
~~~
// data_simple.js 在 demo中返回数据为：[{"title":"基础知识","get_score":11},{"title":"加分知识","get_score":12},{"title":"未分组","get_score":8}]
$('.echart-canvas-02').getDrawEChart({
    'url'       : './data_simple.js',       
    'drow_data' : {
        echart_config   : {title:"分组得分占比图",type:"pie",name_key:"title",value_key:"get_score"}
    }           
});
~~~


4. js 完整定义数据，自定义请求类型

html
~~~
  
~~~
js
~~~
// data_profession.js 在 demo中返回数据为：{"code":1,"dataset":[{"title":"基础知识","get_score":5},{"title":"加分知识","get_score":10},{"title":"未分组","get_score":5}]}
$('.echart-canvas-04').getDrawEChart({
    'url'           : './data_profession.js',   
    'type'          : 'POST',
    'data'          : {p:1},
    'success_key'   : 'code',           // 数据请求成功标识字段名
    'success_val'   : '1',              // 数据请求成功标识字段值
    'data_key'      : 'dataset',        // 数据使用字段
    'drow_data'     : {                 
        echart_config   : {title:"分组得分占比图",type:"pie",name_key:"title",value_key:"get_score"}
    }           
});
~~~


5. 异步请求，url标签绑定

简单数据格式请求
~~~
           
~~~

完整数据格式请求
~~~
              
~~~


6. 配置主题

> 需要引入样式文件（此处以 wonderland 为例），可配置自定义样式：http://echarts.baidu.com/theme-builder/ 下载引入后即可配置使用。

js
~~~
  
  
  
  
 
    $('body').EChartHelper({
        'theme':'wonderland',
    });
 
~~~
![](images/screenshot_1529729300149.png)

7. 配置模版

> 在 chartOption 内以图表类型为 key 传入需要自定义的配置内容即可。
> 具体配置内容请参考 echarts 官方文档。

~~~
$('body').EChartHelper({
    'chartOption':{
        'pie':{
            title : {
                subtext: '纯属虚构123',
            },
        }
    }
});
~~~


8. 其他配置展示

a) 雷达图 radar
> 相对于饼图增加了一个总数字段

html
~~~
  
~~~
![](images/screenshot_1529680779892.png)

b) 柱状图 bar
html
~~~
  
~~~
![](images/screenshot_1529677203004.png)

c) 折线图 line
> 此处仅需要将柱状图 echart-config 中 type 属性改为 line 即可

html
~~~
  
~~~
![](images/screenshot_1529678382353.png)

d) 组合折线图 line
> 会自动将x轴无数据的字段填充0

html
~~~
  
~~~
![](images/screenshot_1529679137879.png)

e) 组合柱状图 bar
> 同理，修改组合折线图 echart-config 中的 type 值为 bar 即可

html
~~~
  
~~~
![](images/screenshot_1529679448053.png)

f) 组合柱状图+折线图 bar+line
> 将 echart-config 中相关字段使用数组配置

html
~~~
  
~~~
![](images/screenshot_1529683074966.png)

g) 仪表盘 gauge
html
~~~
  
~~~
![](images/screenshot_1529679800775.png)





 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)