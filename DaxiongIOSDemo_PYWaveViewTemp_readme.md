# PYWaveViewTemp
关于自定义波浪效果视图，可以当进度展示器用。（默认举行和圆形两种，可自定义形状
![冲浪.gif](http://upload-images.jianshu.io/upload_images/4185621-a92c752ac94658f0.gif?imageMogr2/auto-orient/strip)

前言：
工作中遇到冲浪需求，于是找了很多资料做参考，最后集成了一个工具类

---
**一、实现思路**
>1. 用正弦函数，计算波浪上的点用`UIBezierPath`的`moveToPoint`和`addLineToPoint`连接成线，
2. 用定时器DisplayLink作为动力源
3. 停止波浪： 停止定时器并赋值为nil
4. 开启波浪： 新建定时器，并`setNeedsDisplay`

---
**二、详细代码**
**1. 创建**
>1. 提供的构造方法**`构造方法 构造方法将自动开启冲浪不需要手动调用开启`**
```
/**
 * 冲浪视图的类构造方法
 * @param colorMutableArray 颜色数组
 * @param progress 高度或进度，占self.frame.size.height得百分比
 */
+(instancetype)waveViewWithFrame:(CGRect)frame andColorSet: (NSMutableArray  *)colorMutableArray andProgress: (CGFloat)progress;
/**
 * 冲浪视图的类构造方法
 * @param colorMutableArray 颜色数组
 * @param progress 高度或进度，占self.frame.size.height得百分比
 */
-(instancetype)initWithFrame:(CGRect)frame andColorSet: (NSMutableArray  *)colorMutableArray andProgress: (CGFloat)progress;
```
2. 默认的构方法要手动打开冲浪模式



**2.开启 & 停止冲浪**
>是否冲浪(设置成YES开始冲浪，设置成NO停止冲浪。 默认为NO)
```
@property (nonatomic,assign) BOOL isWaveStart;
```

**3.炫酷的扩展性**
1. 颜色
>///需要画出的颜色数组,可以随时添加，内部在绘图的时候对数组进行了遍历
```
@property (nonatomic,strong) NSMutableArray  *colorMutableArray;
```

2. 海水的高度  (可以作为下载进度)
>高度或进度，占self.frame.size.height得百分比
```
@property (nonatomic,assign) CGFloat progress;
```

3. 水波的参数
>1.振幅 (水波的振幅)
```
@property (nonatomic, assign) CGFloat amplitude;
```
2.水波的周期
```
@property (nonatomic, assign) CGFloat cycle;
```
3.两个波水平之间偏移的距离
```
@property (nonatomic, assign) CGFloat distanceH;
```
4.两个波竖直之间偏移 
```
@property (nonatomic, assign) CGFloat distanceV;
```
5.水波的速率(默认0.1)
```
@property (nonatomic, assign) CGFloat waveScale;
```

4. 形状的扩展
>1.自定义形状
```
@property (nonatomic, strong) UIBezierPath *bazierPath;
```
2.形状类型，默认是圆形（分为矩形和圆形两种，如果设置了bazierPath属性，则优先按照bazierPath路径获取形状）
```
@property (nonatomic,assign) PYWaveViewPathType pathType;
```
3.关于形状的枚举
```
typedef enum : NSUInteger {
    PYWaveViewPathType_CIRCULAR = 0,//圆形
    PYWaveViewPathType_RECT = 1,//矩形
} PYWaveViewPathType;
```

**话不多说，[源码代码请看这里](http://git.oschina.net/LYPLiYaoPeng/PYWaveViewTemp)**

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)