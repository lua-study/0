boofw/raf-timer
=============

setTimeout and setInterval based on requestAnimationFrame api

Usage
--------------

* not ES2015

```
  
 
RafTimer.setTimeout(function(t) {
  console.log('setTimeout', JSON.stringify(t));
});
RafTimer.setInterval(function(t) {
  console.log('setInterval', JSON.stringify(t));
  if (t.count > 3) t.quit();
}, 500);
 
```

* ES2015

```
 
  import RafTimer from '#path#/src/index.js';
  RafTimer.setTimeout(function(t) {
    console.log('setTimeout', JSON.stringify(t));
  });
  RafTimer.setInterval(function(t) {
    console.log('setInterval', JSON.stringify(t));
    if (t.count > 3) t.quit();
  }, 500);
 
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)