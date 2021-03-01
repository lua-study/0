#AnimationLoadingImage
#使用SDWebImage实现的图片下载动画显示效果(只有从网络上新下载的才添加动画 本地已经缓存的不添加)
### 动画效果
![输入图片说明](http://git.oschina.net/uploads/images/2016/0901/170942_2bc7ad01_727503.gif "在这里输入图片标题")

#使用方法
```
#import "UIImageView+AnimationLoading.h"
```


```
/**
 *  下载图片 并且动画显示
 *  @param strUrl 图片地址(字符串哦)
 *  @param pImage 占位图片
 */
-(void)setImageWithAnimationOfUrl:(NSString *)strUrl placeHolder:(UIImage *)pImage;
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)