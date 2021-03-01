 Quark Renderer 

A lightweight yet powerful canvas (&svg) render engine improved from [ZRender](https://github.com/ecomfe/zrender)

## Background

**Important: Quark Renderer is not built from scratch, but improved from ZRender, which is the render engine behind ECharts.**

I have used ECharts and ZRender for many years, both of them are extremly powerful tools for making some charting stuff.

To better understand the core ideas behind ZRender, I spent some days (2020-01) to read through its source code. In this process, I refactored a bunch of code and comments, because:

- I want a very customized version to implement some cool stuff in the future.
- I want a cleaner repo to teach my students how to understand and design a canvas engine for modern web and Wechat mini-programs.
- I want to make the code easier to read.
- There are two reasons why I have to pick up a new name for this project. Firstly, ZRender exported a global variable 'zrender', therefore a new name can avoid potential conflicts. Secondly, duplicated names are not allowed in npm.

Here are the key improvements compare to the original ZRender:

- Modified a bunch of classes and js files with ES6 syntax.
- Added keyboard event support.
- Added multi drag-drop feature.
- Refactored the structure of js files and directories for better understanding.
- Refactored some implementation details for better understanding.
- Fixed some bugs in /test directory, added a few test cases.
- Use [jsduck](https://github.com/senchalabs/jsduck) for better API document.
- Refactored all the comments for jsduck.
- Support Wechat mini-program directly, do not need any hack.
- Support node-canvas environment directly, do not need any hack.
- Removed VML engine, because the marketshare of IE is already very small now. 
- Add skew feature for transformation system.

## Usage

- Pull this repo to your local device.
- Run npm build.
- Check the examples inside /test directory.

Browser example:

```html
 
 
 
     
     Animation 
      
     
     
        html, body, #main {
            width: 100%;
            height: 100%;
        }
     
 
 
      
     
        let main = document.getElementById('main');
        let qr = QuarkRenderer.init(main);
        
        let gradient = new QuarkRenderer.LinearGradient();
        gradient.addColorStop(0, 'red');
        gradient.addColorStop(1, 'black');

        let circle = new QuarkRenderer.Circle({
            position: [0, 0],
            scale: [1, 1],
            shape: {
                cx: 50,
                cy: 50,
                r: 50
            },
            style: {
                fill: gradient,
                lineWidth: 5,
                text:'circle',
                textPosition:'inside'
            }
        });
        qr.add(circle);
        
        // first animation process
        circle.animate()
            .when(1000, {
                position: [200, 0],
                scale: [2, 1]
            })
            .when(2000, {
                position: [200, 200],
                scale: [1, 1]
            })
            .when(3000, {
                position: [0, 200],
                scale: [1, 2]
            })
            .when(4000, {
                position: [0, 0],
                scale: [1, 1]
            })
            .during(function(){
                console.log(circle.animationProcessList.length);
            })
            .done(function(){
                console.log(circle.animationProcessList.length);
            })
            .start();//.start(true)

        //second animation process
        circle.animate()
            .when(1000, {
                position: [500, 0],
                scale: [2, 1]
            })
            .when(2000, {
                position: [200, 200],
                scale: [1, 1]
            })
            .when(3000, {
                position: [0, 200],
                scale: [1, 2]
            })
            .when(4000, {
                position: [0, 0],
                scale: [1, 1]
            })
            .during(function(){
                console.log(circle.animationProcessList.length);
            })
            .done(function(){
                console.log(circle.animationProcessList.length);
            })
            .start();//.start(true)
     
 
 
```

Wechat mini-program example:

```html
 
     
         Quark Renderer 小程序示例1 
     
     
         
              
         
     
 
```

```javascript
onReady: function () {
    let ctx = wx.createCanvasContext('firstCanvas');
    //注意这里的初始化参数，因为微信小程序不允许操作 DOM，所以引擎不能自动获取到宽度高度，这里需要手动传进去
    let qr = QuarkRenderer.init(ctx,{width:300,height:500,renderer:'canvas'});
    let polygon = new QuarkRenderer.Polygon({
        position: [100, 100],
        scale: [1, 1],
        style: {
            fill: 'red'
        }
    });

    setInterval(function () {
        let len = Math.round(Math.random() * 100);
        let points = [];
        let r = (Math.random() * 100);
        for (let i = 0; i  
 
 
 
 
 
 
 
 

Wechat mini-program example:

 

## Resources

[https://cloud.tencent.com/edu/learning/live-1902?ADTAG=xyj ](https://cloud.tencent.com/edu/learning/live-1902?ADTAG=xyj )


## License

BSD 3-Clause License

[LICENSE](./LICENSE)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)