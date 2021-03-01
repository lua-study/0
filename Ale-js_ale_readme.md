 
    
 
 
    
    
    
    
      
 
 关于 Ale.js 

## 介绍

**(在star码云上的 ale.js 时，不要忘记也去 [github](https://github.com/Ale-js/ale) 上给我们一个star！非常感谢！)**

Ale (中文：啤酒) 是一套用于以组件的形式构建用户界面的渐进式框架。它信奉，万物皆组件。与其它大型框架不同的是，Ale 只需要你将关注点放在数据上，并不需要关心任何与视图有关的内容。当你更新数据时，视图中任何使用到它的地方都会得到更新。

我们将 Vue 和 React 的一些特性融合在 Ale 中，使之更加便捷、轻量。同时，diff 算法在 Ale 中也有应用（得益于 Ale 自研的 diff 算法，只有大约50行，极其轻量）。

同时，在 Ale 中，你也根本无需操心任何有关于 性能 方面的事情，因为 Ale 经过压缩后（非g-zip）只有大约7kb大小，执行速度也分别接近 Vue 和 React 的 3 倍！

如果你已经是有经验的前端开发者，想知道 Ale 与其它库 / 框架有哪些具体区别，请查看 [对比其它框架](https://cn.alejs.org/guide/v1/Comparison/)。

#### 简单实例
```javascript
//一个简单的HelloWorld实例
Ale("helloworld", {
    template: "Hello World"
})

Ale.render("helloworld", {
    el: "#app"
})
```

### 浏览器兼容
Ale 不支持 IE8 及以下版本，因为 Ale 使用了 IE8 无法模拟的 ECMAScript 5 特性。但它支持所有兼容 ECMAScript 5 的浏览器。

### 生态系统
QQ群：

 

### 文档
想查看文档和在线实例，请访问 [cn.alejs.org](https://cn.alejs.org).

### 许可证

[MIT](http://opensource.org/licenses/MIT)

Copyright (c) 2018-present, Yingxuan (Bill) Dong


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)