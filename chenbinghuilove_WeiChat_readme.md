### 该项目Demo是模仿微信的好友聊天列表[Demo](https://git.oschina.net/chenbinghuilove/WeiChat)。
首先看一下当前的demo实现的功能以及效果图：

![WeiChat.gif](http://upload-images.jianshu.io/upload_images/1397676-47ce06b637f00107.gif?imageMogr2/auto-orient/strip)

从功能效果上面来看，实现的功能点主要有一下几点：

1 启动页轮播图

2 登陆页面数据信息验证以及点击事件

3 好友列表展示页

4 聊天页面
  4.1 消息页面的布局展示效果，

  4.2 消息气泡的拉伸效果，

  4.3 输入框的自动化布局效果，

  4.4 键盘弹出后的动态效果，

  4.5 消息发出后消息页面的动态效果。

###针对上面不能的功能点进行分析和开发
1 首页启动轮播图思想就是检查当前系统是否为第一次安装该软件或者当前的版本号与系统存得版本号是否一致。
```Swift
// Override point for customization after application launch.
        // 得到当前应用的版本号
        let infoDictionary = NSBundle.mainBundle().infoDictionary
        let currentAppVersion = infoDictionary!["CFBundleShortVersionString"] as! String
        //取出之前保存的版本号
        let userDefaults = NSUserDefaults.standardUserDefaults()
        let appVersion = userDefaults.stringForKey("appVersion")
        let storyboard = UIStoryboard(name: "Main", bundle: nil)
        
        // 如果appVersion为nil说明是第一次启动；如果appVersion不等于currentAppVersion说明是更新的图片
  if appVersion == nil || appVersion != currentAppVersion {
            //将用户阅读引导信息存储下来
            userDefaults.setValue(currentAppVersion, forKey: "appVersion")
            
            let guideViewController = storyboard.instantiateViewControllerWithIdentifier("GuideViewController") as! GuideViewController
            self.window?.rootViewController = guideViewController
        }
```
轮播图的实现方式就更加简单了，设计思想在当前的View上层平铺一个scrollView视图(该视图只能左右滑动)，视图的长是View的N倍，这里的N表示我们轮播图个数，并且加入pageController进行位置定位控制。
```Swift
        let frame = self.view.bounds     
        scrollView = UIScrollView(frame: frame)
        // default NO. if YES, stop on multiples of view bounds
        scrollView.pagingEnabled = true
        // default YES. show indicator while we are tracking. fades out after tracking
        //Horizontal水平方向上的平移标尺
        //Vertical垂直方向上的平移标尺
        scrollView.showsHorizontalScrollIndicator = false
        scrollView.showsVerticalScrollIndicator = false
        // 跟上面的标示一致的，点击放回顶部
        scrollView.scrollsToTop = false
        //A Boolean value that controls whether the scroll view bounces past the edge of content and back again
        //回弹的动态效果
        scrollView.bounces = false
        //The point at which the origin of the content view is offset from the origin of the scroll view.
        //The default value is CGPointZero.
        //相当于偏移量
        scrollView.contentOffset = CGPointZero
        //将scrollview的contentSize设为屏幕宽度的3倍
        scrollView.contentSize = CGSize(width: frame.size.width * CGFloat(numOfPages), height: frame.size.height)
        scrollView.delegate = self
        for index in 0 ..  CGFloat {
        let screanRect = UIScreen.mainScreen().bounds
        //获取该文字在限定宽的情况下，高度是多少，然后与我们当前的cell高度进行对比，并且更新avatarSize.height值。
        let labelSize: CGSize = UILabel.sizeOfString(message.message, font: UIFont.systemFontOfSize(16), maxWidth: screanRect.width - 10 - 20 - avatarSize.width * 2)
        if labelSize.height   textHeigth{
            UIView.animateWithDuration(0.3, animations: { () -> Void in
                let textFieldFrame = self.inputToolbar.frame
                print(textFieldFrame.origin.y)
                self.inputToolbar.frame = CGRectMake(0, textFieldFrame.origin.y - 10 , UIScreen.mainScreen().bounds.width, textFieldFrame.height + 10)
                self.inputToolbar.backgroundImageView.frame = CGRectMake(0, 0, self.inputToolbar.frame.width, self.inputToolbar.frame.height + 10)
                self.inputToolbar.textFieldBackground.frame = CGRectMake(44, 0, UIScreen.mainScreen().bounds.width - 34 - 10 - 34 - 10, self.inputToolbar.frame.height + 5)
                self.inputToolbar.textField.frame = CGRectMake(44, 0, self.inputToolbar.textFieldBackground.frame.width, self.inputToolbar.frame.height + 5)
                }) { (Bool) -> Void in
                    print(true)
            }
```
3 还有就是之前用的TextField输入框，然后点击return后会返回提交状态，但是如果使用了TextView作为输入框时，就需要使用这个方法`func textView(textView: UITextView, shouldChangeTextInRange range: NSRange, replacementText text: String) -> Bool`进行实时监控，他是针对输入框中的每一个单词进行对比的。
```Swift
func textView(textView: UITextView, shouldChangeTextInRange range: NSRange, replacementText text: String) -> Bool {
        if text == "\n" {
            self.onLeftBtnTapped(self.rightBtn)
            return false
        }else{
            return true
        }       
    }
```
4 这里设计一个工具类主要作用是为了辅助调整布局的。
boundingRectWithSize根据当前一段输入的文字的特征来获取到它的size属性。从而能够判断出这个文字的在限定长度的情况下，它的高度是多少。
```Swift  
extension UIImage{
    //拉伸图片的方法
    class func resizableImage(name: String) -> UIImage {
        let image = UIImage(named: name)!        
        let top: CGFloat = image.size.height * 0.6
        let bottom: CGFloat = image.size.height * 0.5
        let lAndr: CGFloat = image.size.height * 0.5
        return image.resizableImageWithCapInsets(UIEdgeInsets(top: top, left: lAndr, bottom: bottom, right: lAndr))
    }
}
extension UILabel{
    //主要是获取输入信息的高度
    class func sizeOfString(string: NSString,font: UIFont,maxWidth:CGFloat) ->CGSize {
        //boundingRectWithSize()方法
        //需要自己去了解，了解
        let size: CGSize = string.boundingRectWithSize(CGSize(width: maxWidth, height: 999), options: .UsesLineFragmentOrigin, attributes: [NSFontAttributeName: font], context: nil).size
        return CGSize(width: size.width + 15, height: size.height + 20)
    }
}
```
5 键盘弹出的动画效果设计思想：添加键盘监听方法，获取到键盘的运动时间，曲线，间隔等数据，再将输入框按照这种方式来做同样的动作即可。如果你的键盘上面的组件不是Autolayer自动布局的（依赖关系）的，那么就需要你取调整每一个组建的动作会很复杂和麻烦，当然我就是后者，这里没有用到SnapKit，所以很麻烦啊，这里就不贴出来丢人了。
```Swift  
//keyboard notitication
        NSNotificationCenter.defaultCenter().addObserver(self, selector: "keyboardFrameWillChange:", name: UIKeyboardWillShowNotification, object: nil)
        NSNotificationCenter.defaultCenter().addObserver(self, selector: "keyboardFrameWillHide:", name: UIKeyboardWillHideNotification, object: nil)
        NSNotificationCenter.defaultCenter().addObserver(self, selector: "textViewFrameWillChange:", name: UITextViewTextDidChangeNotification, object: nil)
        //keyboard收回加入点击事件。
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)