# echarts_line_dataZoom

#### 项目介绍
Echarts 平面直角坐标系趋势图（line-area），由于数据量很大，采用 xAxis-time 加 dataZoom 来实现，要求 dataZoom 的控制效果为百度指数那种，可以按照年、月、日的维度来进行展示。

### 思路以及实现
dataZoom 组件具有过滤数据的功能，但其不能控制 X 轴的字符展示，X 轴字符倒是可以通过 xAxis 的 formatter 来设置，如果按照这个思路来实现，即是这样的逻辑：改变 dataZoom 范围 => 得到渲染数据的范围 => 确定 X 轴字符现实的 formatter => 将图表 refresh,设置setOption => 图表重新渲染，那么问题就来了，这样通过手动 setOption 会让 dataZoom 也重新渲染，那拖动的dataZoom 将会被重置，这显然不行。

基于上面的思路，得知，图表是图表，dataZoom 是 dataZoom,两者是独立绘制的，只能 dataZoom 去控制 图表。

### 最后

搞这个好累，心累


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)