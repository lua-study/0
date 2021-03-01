# 基于Cesium的体渲染使用说明

## 简介

![](mk-images/2020-02-20-14-00-17.png)

在Cesium的基础上实现体渲染功能

## 源码使用方法

0. 安装
npm install

1. 调试
npm run dev

2. 打包
npm run build

## 示例说明

![](mk-images/2020-02-20-14-10-19.png)

## 示例代码使用讲解

示例代码请参考scripts/index.js文件。

#### js文件引入

引入parseCsv.js/VolumeRendering.js以后，VolumeRendering/parseCsv为全局变量，
VolumeRendering是一个Cesium的图元，可以直接加入到scene当中去使用
parseCsv是一个函数，用来解析csv数据

html代码：
```html
      
      
```

js代码：
```javascript
const VolumeRendering = window.VolumeRendering;
const parseCsv = window.parseCsv;
```

#### csv数据解析

加载完成后对csv数据进行解析, csv文件必须符合结构必须是：前三个字段表示x/y/z即位置，后面的字段各自表示某个时刻的数值

buffers为buffer的数组，每个元素都代表着某个时刻的所有体渲染数据

stpProperty 这是创建体渲染需要用到的参数，用来表示x/y/z轴的使用顺序，shader中使用，不用理解，后面直接赋值就好

minCartesian, maxCartesian 分别代表csv中数据的最小位置，最大位置，创建的体渲染需要这两个参数决定体渲染的大小

```
const { buffers, stpProperty, minCartesian, maxCartesian } = parseCsv(text);
```

### 体渲染图元的创建

VolumeRendering是一个Cesium的图元类。使用方法如下：

```
// 创建体渲染模型，其中的属性minCartesain/maxCartesian/stpProperty是从parseCsv获取到的
var vr = viewer.scene.primitives.add(new VolumeRendering(viewer.scene));
vr.modelMatrix = enuMatrix; // 设置渲染体在地球上的什么位置，如何摆放
vr.minCartesain = minCartesian; // 确定渲染体的最小位置点
vr.maxCartesian = maxCartesian; // 确定渲染体的最大位置点
vr.stpProperty = stpProperty; // 确定shader中xyz的顺序，一般情况下不要修改，直接使用parseCsv获取得就好
vr.show = true; // 是否可见
vr.stepSize = 0.1; // 迭代步长，单位米，如果太小，会影响性能，如果太大，显示效果会不好
vr.maxSteps = 10000; // 迭代总次数，一般情况下不要修改，越小，性能越好，但是显示效果会变差

vr.gradientCanvas.colorStops = [ // 修改色带，范围在0到1之间
    [0.0, "rgba(0, 255, 0, 0.1)"],
    [0.5, "rgba(0, 0, 255, 0.5)"],
    [0.7, "rgba(255, 255, 0, 1.0)"],
    [1.0, "rgba(255, 0, 0, 1.0)"],
];

// 对应csv中所描述属性的最小值，注意minIntensity的位置，会用色带中位置0处的颜色，如果csv中有数值小于minIntensity，则会强制设置为minIntensity
vr.minIntensity = 0.0;

// 对应csv中所描述属性的最大值，maxIntensity对应色带中位置为1.0的颜色，如果csv中有数值超过maxIntensity，则会强制设置为maxIntensity
vr.maxIntensity = 100.0;

vr.blendAlpha = 0.8;

// vr.blendAlpha(buffer) // buffer为Uint8Array类型数组，长度是固定的：1024*1024*4，请使用parseCsv中获取到得进行赋值
window.vr = vr;

```



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)