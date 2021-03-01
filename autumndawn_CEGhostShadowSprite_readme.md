#CEGhostShadowSprite

![效果图](screenshot.png)

### 用途 ###

CEGhostShadowSprite 是比较独立的一个小组件,用于播放很简单的残影效果。

可以配合我的另外一个类库 [贝塞尔移动](http://git.oschina.net/eran/BezierMathUtils) 一起使用 :)

### 局限性 ###

- 目前 CEGhostShadowSprite 比较简单 仅仅支持单纹理( Texture || Atlas's Texture )的Image

- 只提供了x,y坐标的更改 不可以改变alpha , roation 等 这些需要自己扩充

- 为了做性能优化 CEGhostShadowSprite 本身并不是显示对象,而是在初始化时候 需要传入两个Container

	> - realBodyParentContainer : 该Container内部放置残影Mc的本体
	> - shadowFragmentParentContainer : 放置所有的残影

这样做的效果是：

	所有本体都在残影的上层，可以自行排序 or 就按照最初addChild时候的顺序排列，移动时候不会有层级错乱

	所有的残影均在统一的一层 移动时候(两个Mc交叉时候)，会有轻微的层级错乱，如果速度快的话 肉眼很那看清

	采用这种方式后，可以将DRW控制在2


### 特性 ###

- CEGhostShadowSprite 本身不是显示对象 需要传入两个Container

- 方便TweenLite调用，详情参加DemoCode

- 内部有对象池,运行稳定后 不会老new出新的对象

### DemoCode ###

```
var ghostShadowSprite = new CEGhostShadowSprite();

ghostShadowSprite.initialize(_texture, _realBodyContainer, _shadowFramgmentContainer, 100, 100);

private function tweenToRandomPosition():void
{
	TweenLite.to(ghostShadowSprite, Random.range(0.5, 3, false),
				 {
					 x: Random.range(10, 780),
					 y: Random.range(10, 580),
					 magicTriggerValue: ghostShadowSprite.magicTriggerValue + 10,
					 onComplete: tweenToRandomPosition
				 });
}

//在Tween函数内部 每次都更改magicTriggerValue 即可触发残影效果
//单独更改 ghostShadowSprite 的 x,y 坐标不会触发残影
//如果需要 可以手动调用 ghostShadowSprite.markSubFragmentToCurrentPosition() 函数在当前位置添加残影

```

### Issue ###

iamzealotwang@126.com





 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)