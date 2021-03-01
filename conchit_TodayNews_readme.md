# Swift开源项目-模仿今日头条

![](http://obna9emby.bkt.clouddn.com/news/news.gif)

## 说明

首先声明，今日头条是我经常用的 app 之一，模仿今日头条也是因为感兴趣，代码仅用于学习交流。对于项目中的数据接口都是通过 Charles 抓包获得，基本每个界面都是有数据请求，不会抓包的朋友可以看我 [这一篇文章](http://www.jianshu.com/p/235bc6c3ca77)。

项目中有的地方代码写的不是很简洁，毕竟自己能力有限，对 Swift 使用不是很熟练，还请各位朋友不喜勿喷。下面有项目的完整源码，喜欢的朋友可以下载下来，如果您感觉我写的代码对您有所帮助，还请在 github 给个 star，非常感谢您的支持！~

#### 对于代码中出现的问题，可以及时联系我，我会继续修改。

### [github 地址](https://github.com/hrscy/TodayNews)

### [CodeData 地址](http://www.codedata.cn/cdetail/Swift/Demo/1471514673634279)

## 环境设置
- 项目环境
	- Xcode 7.3.1（低于这个版本会报错）。
	- Swift 2.2
	- iOS 8.0 +

- 使用 cocoaPods 管理第三方库， 如果电脑没有安装 cocoapods，请先安装 cocoapods。安装方式可参考：[最新版 CocoaPods 的安装流程](http://www.tuicool.com/articles/7VvuAr3)

- 项目中使用到的第三方库
	- SnapKit： 布局
	- Kingfisher： 缓存图片
	- SVProgressHUD：提示框
	- FDFullscreenPopGesture：侧滑
	- Alamofire ：网络请求
	- SwiftyJSON：解析 json
	- MJRefresh： 上拉刷新和下拉刷新
	
## 实现的功能

1. 获取今日头条的接口
2. 完成首页的布局和数据的显示
3. 实现首页顶部导航栏滚动
4. 新闻详情界面简单实现
5. 点击屏蔽按钮，弹出屏蔽视图（坐标有一些问题）
6. 完成视频界面顶部导航栏滚动
7. 完成视频界面布局和数据获取
8. 用户界面简单实现
9. 完成关注界面布局和数据的获取
10. 完成关注界面，添加关注功能
11. 完成搜索功能
12. 完成个人界面的布局
13. 完成设置界面的布局
14. 完成离线下载界面布局
15. 活动界面简单实现
16. 登录界面的简单实现
17. 启动界面的简单实现

## 数据请求

#### 今日头条的接口文件请看： [news.json](https://github.com/hrscy/TodayNews/blob/master/news.json)，需要提前安装 postman，然后把该文件导入到 postman 进行查看，可以打开谷歌浏览器，找到扩展程序，添加新的扩展，搜索 postman。

#### 下载地址请看 [postman](https://pan.baidu.com/s/1slxQIdv)，下载完成后，直接拖入到谷歌浏览器的扩展程序界面即可。

#### 数据请求的具体方式，请看 [YMNetworkTool.swift](https://github.com/hrscy/TodayNews/blob/master/TodayNews/Classes/Main(%E4%B8%BB%E8%A6%81)/Tools/YMNetworkTool.swift)。

# 首页

### [YMHomeViewController.md](https://github.com/hrscy/TodayNews/blob/master/documents/%E9%A6%96%E9%A1%B5/Controller/YMHomeViewController.md)

![首页-1](http://obna9emby.bkt.clouddn.com/news/%E9%A6%96%E9%A1%B5-1_spec.png)

#### 1.首先，首页的状态栏的颜色是白色，所以调用了下面的方法：

```
override func preferredStatusBarStyle() -> UIStatusBarStyle {
    return .LightContent
}
```

但是，经过测试，上面的代码不起作用，对于 `YMMineViewController.swift` 上面的代码是起作用的。

唯一的区别是就是在 `YMMineViewController.swift` 中隐藏了导航条。所以经过查阅资料，得到下面的结论：
> 1.不管是调用了系统的 `UINavigationController` 还是使用自己继承自 `UINavigationController`，如果 `navigationBar` 没有被隐藏的话，那么导航控制器的 `rootController` 以及它 `push` 的控制器的 `preferredStatusBarStyle()` 方法都不会被调用。
> 2.如果在当前控制器手动设置了 `navagationBar` 的 `barStyle` 为 `.Black` 或者 `.Default` 或者使用下面的代码手动设置：

```
// 方式1
navigationController?.setNavigationBarHidden(true, animated: false)
// 方式2
navigationController?.navigationBarHidden = true
```

那么 `preferredStatusBarStyle()` 就会被正常调用了。

还有一点关于隐藏导航栏的注意点请看 [YMMineViewController.swift](https://github.com/hrscy/TodayNews/blob/master/documents/%E6%88%91%E7%9A%84/Controller/YMMineViewController.md)。

#### 2.关于导航栏的 titleView

在首页首页顶部标题的时候，直接设置 titleView 的宽度为屏幕的宽，但是两边总是会留出 10 的间距，这个时候需要重写父类的 setFrame 方法，在 OC 里面可以使用下面的方法：

```

- (void)setFrame:(CGRect)frame  
{  
    CGRect newFrame = CGRectMake(0, 0, SCREENW, 44);
    [super setFrame:frame];  
} 
```

但是在 swift 中不能这样写，要使用下面的方式：

```
/// 重写 frame
override var frame: CGRect {
    didSet {
        let newFrame = CGRectMake(0, 0, SCREENW, 44)
        super.frame = newFrame
    }
}
```

这样设置，运行程序，发现 titleView 在屏幕两边不在留有间距。

#### 3.子控制器

`YMHomeTopicController.swift` 作为 `YMHomeViewController.swift`的子控制器，显示新闻数据。

### [YMHomeTopicController.md](https://github.com/hrscy/TodayNews/blob/master/documents/%E9%A6%96%E9%A1%B5/Controller/YMHomeTopicController.md)

该类注册了四种 cell，分别表示中间三张图片，右边一张图片，中间一张大图，中间一张视频大图，没有图片的情况。

以下是四种情况：

![](http://obna9emby.bkt.clouddn.com/home-cell-1.png)
![](http://obna9emby.bkt.clouddn.com/home-cell-2.png)
![](http://obna9emby.bkt.clouddn.com/home-cell-3.png)
![](http://obna9emby.bkt.clouddn.com/home-cell-4.png)
![](http://obna9emby.bkt.clouddn.com/home-cell-5.png)

在 `tableView(tableView: UITableView, cellForRowAtIndexPath indexPath: NSIndexPath) -> UITableViewCell` 中，根据不同情况对要显示的 cell 进行判断，显示对应的 cell。

具体判断情况请看 `Model` 里的 `YMNewsTopic.swift` 类。

### [YMHomeDetailController.swift](https://github.com/hrscy/TodayNews/blob/master/TodayNews/Classes/Home(%E9%A6%96%E9%A1%B5)/Controller/YMHomeDetailController.swift)

详情有下面几种方式：

![](http://obna9emby.bkt.clouddn.com/news/home-detail-1.jpg)
![](http://obna9emby.bkt.clouddn.com/news/home-detail-2.jpg)
![](http://obna9emby.bkt.clouddn.com/news/home-detail-3.jpg)
![](http://obna9emby.bkt.clouddn.com/news/home-detail-4.jpg)

为了实现简单，这里使用 `webView` 来实现

### [YMPopPresentationController.md](https://github.com/hrscy/TodayNews/blob/master/documents/%E9%A6%96%E9%A1%B5/Controller/YMPopPresentationController.md)

#### iOS 8 以后推出的专门负责转场动画的控制器。

在 Xcode 7 以上的版本中，`UIPresentationController` 有一个 bug，见下图：

![野指针](http://obna9emby.bkt.clouddn.com/news/home-pop-error.png)

`presentingViewController` 会报一个野指针的错误，这是 Xcode 的 bug。

#### `UIPresentationController` 中有两个方法可以布局子视图，分别是：

```
// 即将布局转场子视图时调用
public func containerViewWillLayoutSubviews()
// 布局完成转场子视图时调用
public func containerViewDidLayoutSubviews()
```
可以在两个方法里设置 `UIPresentationController` 的容器视图 `containerView` 和 被展现的视图 `presentedView()`。

![containerView-presentedView](http://obna9emby.bkt.clouddn.com/news/containerView-presentedView.png)

### [YMHomeTopicCell.md](https://github.com/hrscy/TodayNews/blob/master/documents/%E9%A6%96%E9%A1%B5/View/YMHomeTopicCell.md)

这个类主要作为四种类型 cell 的父类，主要定义了 标题、头像、昵称、评论、关闭按钮。

显示图片交给其子类各自实现。

当时考虑过使用一个类来实现四种类型的 cell，但是经过测试，由于 cell 的重用机制，始终不能达到想要的结果，所以才分别创建了四种不同的 cell，使用一个类的方式是 `YMTopicTableViewCell.swift` 这个类，大家可以参考一下。

由于首页的情况比较多，cell 的显示比较复杂，而且今日头条的接口也不是很规范，所以这几个类实现起来比较麻烦，而且代码写的不是很简洁，用了很多 `if` 判断，可能看起来不是很美观。

判断的情况与 `YMNewsTopic.swift` 类相同，具体请看 `YMNewsTopic.swift`。

我觉得使用不同 cell 的情况还比较简单理解。

如果各位朋友有什么更好的实现方法，欢迎给我留言或『Pull Request』，非常感谢您的留言和建议。

### [YMScrollTitleView.md](https://github.com/hrscy/TodayNews/blob/master/documents/%E9%A6%96%E9%A1%B5/View/YMScrollTitleView.md)

![](http://obna9emby.bkt.clouddn.com/news/home-title.png)

这个类和和视频顶部标题的类有些类似，对于数据和按钮点击的回调使用闭包的方式。而在视频的标题 `YMVideoTitleView.swift` 里使用代理来代替闭包，实现的功能是相同的，但是实现的方式不同，可以对比看一下。

对控件的布局方式还是使用的 `SnapKit` 来进行布局。

这个类里需要首先从服务器获取标题数据，服务器返回一个数组，根据这个数组循环创建标题的 `label`，然后设置好 `label` 的位置以及 `scrollView` 的 `contentSize`。

标题 label 的点击通过添加手势来实现监听点击操作，`titleLabelOnClick` 为标题点击的方法，当点击的时候，根据索引进行相应的偏移，调用 `adjustTitleOffSetToCurrentIndex` 来改变 label 的位置。

在 `adjustTitleOffSetToCurrentIndex(currentIndex: Int, oldIndex: Int)` 方法里，需要获取之前点击 label 的索引以及刚刚点击 label 的索引，改变形变，计算当前的偏移量。

重写 frame，来设置导航栏不再有两边的间距。请看具体代码 206 行。

### [YMNewsTopic.md](https://github.com/hrscy/TodayNews/blob/master/documents/%E9%A6%96%E9%A1%B5/Model/YMNewsTopic.md)

这个类是我觉得最麻烦的一个类了，有很多种情况，所以判断也比较多。

今日头条返回的数据中，有这四个字段，`image_list` ，`middle_image`，`large_image_list`，`video_detail_info`，在 cell 里面分别对应 `YMHomeSmallCell.swift`，`YMHomeMiddleCell.swift`，`YMHomeLargeCell.swift`。

`image_list` 这是一个**数组**，表示中间有三种图的情况；

![](http://obna9emby.bkt.clouddn.com/home-cell-3.png)

`middle_image` 这是一个**字典**，表示图片在右侧的情况；

![右边显示一张图片的情况](http://obna9emby.bkt.clouddn.com/home-cell-4.png)

`large_image_list` 这是一个**数组**，表示中间是一张大图；

![](http://obna9emby.bkt.clouddn.com/home-cell-2.png)

`video_detail_info` 这是一个**字典**，表示是视频，中间也用一张大图表示，这种情况和大图的情况基本相同，但是视频中间多了播放按钮。

![](http://obna9emby.bkt.clouddn.com/home-cell-5.png)

还有最后一种情况就是没有图片的情况，比如置顶的专题，但是置顶的专题和上面在**举报按钮**的地方也有所区别，置顶的新闻没有举报按钮，其他情况有举报按钮，需要根据 一个字段 `label` 来进行判断。

![](http://obna9emby.bkt.clouddn.com/home-cell-1.png)

上面五种情况出现的依赖关系，也需要进行判断，

下面说一下，具体的判断过程：

|image_list|middle_image|large_image_list|video_detail_info|
|----------|------------|----------------|-----------------|
|   nil    |    nil     |       nil      |       nil       |
|   nil    |   不为 nil  |    不为 nil     |       nil       |
|   nil    |   不为 nil  |      nil       |      nil        |
| 不为 nil  |   不为 nil  |    不为 nil     |    不为 nil     |
| 不为 nil  |   不为 nil  |    不为 nil     |       nil      |
| 不为 nil  |   不为 nil  |      nil       |    不为 nil     |
| 不为 nil  |   不为 nil  |      nil       |       nil      |

还有一些其他情况，比如有个数据里没有 `image_list` 这个字段，这种情况我没做判断，一般程序崩溃都是因为这个原因。但是实际上，我是先判断 `image_list` 是否有值，如果有值，则显示三张图片，如果为 `nil`，再判断 `middle_image` 的情况。

如果各位朋友有什么更好的实现方法，欢迎给我留言或『Pull Request』，非常感谢您的留言和建议。

### [YMPopViewAnimator.md](https://github.com/hrscy/TodayNews/blob/master/documents/%E9%A6%96%E9%A1%B5/Model/YMPopViewAnimator.md)

## 负责转场动画的代理

自定义转场动画需要集成两个代理协议，分别是 `UIViewControllerTransitioningDelegate` 和 `UIViewControllerAnimatedTransitioning`。

如果需要自定义转场动画，那么所有的操作需要自己完成，系统不再处理。

#### `UIViewControllerTransitioningDelegate` 

`UIViewControllerTransitioningDelegate` 共有五个代理方法，这里我用到了三个代理方法，分别是：

```
// MARK: - UIViewControllerTransitioningDelegate
    /**
     告诉系统由哪个控制器来实现代理
     - parameter presented:  被展现的视图
     - parameter presenting: 展现的视图
     - returns: YMPopPresentationController iOS 8 以后推出的专门负责转场动画的控制器
     */
    func presentationControllerForPresentedViewController(presented: UIViewController, presentingViewController presenting: UIViewController, sourceViewController source: UIViewController) -> UIPresentationController?
    /**
     告诉系统谁来负责 modal 的展现动画
     - parameter presented:  被展现的视图
     - parameter presenting: 展现的视图
     - returns: 由谁管理
     */
    func animationControllerForPresentedController(presented: UIViewController, presentingController presenting: UIViewController, sourceController source: UIViewController) -> UIViewControllerAnimatedTransitioning?
    /**
     告诉系统谁来负责 modal 的消失动画
     - parameter dismissed: 消失的控制器
     - returns: 由谁管理
     */
    func animationControllerForDismissedController(dismissed: UIViewController) -> UIViewControllerAnimatedTransitioning? 
```

#### `UIViewControllerAnimatedTransitioning`

用到了两个代理方法：

```
/** 动画时长*/
    func transitionDuration(transitionContext: UIViewControllerContextTransitioning?) -> NSTimeInterval 
    /** 负责转场动画的效果*/
    func animateTransition(transitionContext: UIViewControllerContextTransitioning) {
        if isPresent {
            // 展开
            let toView = transitionContext.viewForKey(UITransitionContextToViewKey)
            // 一定要将视图添加到容器上
            transitionContext.containerView()?.addSubview(toView!)
            // 锚点
            toView?.layer.anchorPoint = CGPoint(x: 1.0, y: 0.0)
            toView?.transform = CGAffineTransformMakeScale(0.0, 0.0)
            UIView.animateWithDuration(transitionDuration(transitionContext), delay: 0, usingSpringWithDamping: 0.8, initialSpringVelocity: 0.5, options: 
```

### YMHomeShareView.swift

分享界面：

![](http://obna9emby.bkt.clouddn.com/news/home-share.png)

## 视频


### [YMVideoViewController.md](https://github.com/hrscy/TodayNews/blob/master/documents/%E8%A7%86%E9%A2%91/Controller/YMVideoViewController.md)

![](http://obna9emby.bkt.clouddn.com/news/video_spec.png)

这个控制器主要显示顶部导航标题和帖子控制器的一个容器。

顶部导航标题请看 `YMVideoTitleView.swift`，帖子控制器请看 `YMVideoTopicController.swift`。

### [YMVideoTopicController.md](https://github.com/hrscy/TodayNews/blob/master/documents/%E8%A7%86%E9%A2%91/Controller/YMVideoTopicController.md)

![](http://obna9emby.bkt.clouddn.com/news/topicVC.png)

使用的一个 tableView 实现。集成上拉刷新和下拉刷新。实现起来不难。

但是视频播放麻烦一点。需要考虑 cell 的重用机制，由于今日头条返回的数据是一个网址，并不是视频的真实地址，试了一些方法，想把视频的真实地址搞出来，但是没有成功，也是我能力有限。搜易视频播放暂时写了一个地址，播放是这一个视频。

cell的图片是一个 button 的背景图片，通过 button 的点击事件，来判断此时是选中还是没有选中。当点击图片按钮或是播放按钮的时候，在这个按钮上再创建一个 playerView，来播放视频，具体类请看 `YMPlayerView.swift`。

首先提前定义一个 cell，来保存上一次点击的 cell，然后通过 `YMPlayerView.swift` 的回调， 首先把上一次 cell 的状态，恢复原状，然后再在当前选中的 cell 上，进行新的设置，并添加一个 `YMPlayerView`。

> 说明：视频播放还是存在问题，后面有时间会优化。

## 关注

### [YMNewCareViewController.md](https://github.com/hrscy/TodayNews/blob/master/documents/%E5%85%B3%E6%B3%A8/Controller/YMNewCareViewController.md)

这个类是第三个主控制器，显示关注界面。

![](http://obna9emby.bkt.clouddn.com/news/%E5%85%B3%E6%B3%A8-1.jpg)

这个界面创建了一个 tableView，并且注册了三种不同的 cell，分别是 `YMNewCareNoLoginCell.swift`，`YMNewCareTopCell.swift`，以及 `YMNewCareBottomCell.swift`，可分别打开各自的文件，进行查看。

首先设置 UI，然后 `setupRefresh()` 是添加上拉和下拉刷新，然后将 tableView 分成了上下两组，上边一组表示自己添加的关注内容，下边一组表示未添加的关注内容，下面一组可以上拉加载更多内容。

今日头条的接口里有一个 `concern_time` 字段，未添加关注之前，该值为 `0`，当添加某一关注内容之后，该值变为一个关注的时间，单位是秒。由于今日头条接口里返回的数据是一个数组，即已关注和未关注的内容同时包含在一个数组中，所以可以根据这个参数来区分是已关注还是未关注。具体方法可以参考 `setupRefresh` 方法里面调用的 `loadNewConcernList` 方法，以及 `loadMoreConcernList` 方法，这两个方法实现了对已关注和未关注的拆分。

接口里还有一个参数需要注意，就是 `newly` 这个字段，对于刚刚关注的内容或是已关注的内容并没有点击相应的 cell，跳转到下一控制器的关注内容，都会在右边显示一个 『NEW』，这个控件的显示与隐藏需要根据 `newly` 的值进行判断，`newly` 会返回两种情况，一种是 `1`， 另一种是 `0`，即对应显示和隐藏。

上面的参数定义请看 `YMConcern.swift`.

在下面一组每一个 cell 上都有一个『关注』 按钮，这里我使用代理来实现按钮点击的响应事件，让 `YMNewCareViewController` 来接收按钮的点击。

当添加关注的时候，会有一个动画效果，这个动画效果暂时还未实现，大家可以参考今日头条的效果。参考一下，有实现的朋友，也可以联系我，也可以给我 『pull request』。

这个界面的实现还算简单，就说明到这里吧~

### YMSearchContentViewController.swift

搜索界面

![](http://obna9emby.bkt.clouddn.com/news/search-care.png)

### [YMBlurImageView.md](https://github.com/hrscy/TodayNews/blob/master/documents/%E5%85%B3%E6%B3%A8/View/YMBlurImageView.md)


![](http://obna9emby.bkt.clouddn.com/care-title.png)

点击关注界面的某一个 cell 之后，跳转到下移控制器的顶部视图，有一个模糊效果。

界面实现不算太难，主要是对每个控件的布局，使用 `SnapKit`。点击按钮的回调使用委托实现。

代码中注释比较详细，这里不再说明。

### [YMCareheaderView.md](https://github.com/hrscy/TodayNews/blob/master/documents/%E5%85%B3%E6%B3%A8/View/YMCareheaderView.md)


![](http://obna9emby.bkt.clouddn.com/news/care-header.png)

具体代码请看 `YMCareheaderView.swift`。

## 我的

### [YMMineViewController.md](https://github.com/hrscy/TodayNews/blob/master/documents/%E6%88%91%E7%9A%84/Controller/YMMineViewController.md)


![](http://obna9emby.bkt.clouddn.com/news/%E6%88%91%E7%9A%84-%E6%9C%AA%E7%99%BB%E5%BD%95_spec.png)

![](http://obna9emby.bkt.clouddn.com/news/%E6%88%91%E7%9A%84.png)

隐藏导航栏的方法如下：

```
// 方式1
navigationController?.setNavigationBarHidden(true, animated: false)
// 方式2
navigationController?.navigationBarHidden = true
```

需要注意一点，隐藏导航栏的属性写到 `viewDidLoad()` 里不起作用。

### YMSettingViewController.swift

![](http://obna9emby.bkt.clouddn.com/news/%E8%AE%BE%E7%BD%AE.png)

从文件加载 cell 的数据，使用通知的方式，实现了清除缓存，以及改变字体大小，改变下载方式。

### YMOfflineTableViewController.swift
 
我的 -> 离线 -> 离线下载
 
![](http://obna9emby.bkt.clouddn.com/news/offline-download_spec.png)

对于标题的选中与未选中，使用归档的方式，`YMHomeTopTitle` 附加一个字段来判断选中与未选中，然后存储到沙盒中，具体实现可看代码。

### YMActivityController.swift

活动界面

为了实现简单，使用一个 `webView` 实现。

## 登录和启动界面

只是简单的搭了一个界面，具体逻辑没有实现：

![登录](http://obna9emby.bkt.clouddn.com/news/login_spec.png)

![启动](http://obna9emby.bkt.clouddn.com/news/%E5%90%AF%E5%8A%A8_spec.png)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)