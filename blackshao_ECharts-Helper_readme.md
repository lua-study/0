# ECharts-Helper

#### 项目介绍
# echart-helper是什么？
echart-helper是一款echarts辅助开发插件，能够帮助开发者快速构建echart图表。


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
![](images/screenshot_1529676402975.png)

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
$('.echart-canvas-01').getDrawEChart({
    'url':'http://api_01',			// 此处假定返回数据为：[{"title":"基础知识","get_score":11},{"title":"加分知识","get_score":12},{"title":"未分组","get_score":8}]
    'drow_data':{
        echart_config   : {title:"分组得分占比图",type:"pie",name_key:"title",value_key:"get_score"}
    }           
});
~~~

4. 配置主题

> 需要引入样式文件（此处以 wonderland 为例），可配置自定义样式：http://echarts.baidu.com/theme-builder/ 下载引入后即可配置使用。

js
~~~
  
  
  
  
 
    $('body').EChartHelper({
        'theme':'wonderland',
    });
 
~~~
![](images/screenshot_1529729300149.png)

5. 配置模版

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










 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)