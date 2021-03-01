# OSAdsFramework

#### 介绍
插屏广告和激励视频

## 安装说明
打开 SDK 所在的文件夹，将文件夹 AdFrameworks(包含OSAttributionStatisticsFramework AppsFlyerFramework Google-Mobile-Ads-SDK GoogleAppMeasurement FBSDKCoreKit FBAudienceNetwork OSAdsFramework) 拖到 Xcode 中的应用目录。选择“Copy Items if needed”（需要时复制项目），然后点击“Finish”（完成）

![SDK手动集成](https://images.gitee.com/uploads/images/2019/1202/182030_dcb89ef2_446174.png "15163978_374691812877227_109371011480158208_n.png")

## Google SDK安装说明
info.plist 添加 google id
```xml
 GADApplicationIdentifier 
 YOUR_GOOGLE_ID 
```
## FaceBook SDK安装说明
Unity 需要在项目的“构建设置”页面中将“-lxml2”添加到“其他关联工具标记”，如下所示
![](https://images.gitee.com/uploads/images/2019/1016/164753_863ba679_446174.png "FB设置.png")


## 初始化
1. 需要加密过的配置表adInfo.dat 另行提供
2. 初始化代码


```ObjC
#import  
#import  
@interface AppDelegate : UIResponder  

@property (strong, nonatomic) UIWindow *window;

@end 

@implementation AppDelegate
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    // Override point for customization after application launch.
    //初始化 统计和买量SDK。
	/// @param key AppsFlyer 账号提供的key
	/// @param appId App Store 上app上架地址的 appId
	/// @param gameName AppsFlyer使用的统计前缀。
	/// @param delegate id
    [AppsFlyerProxy instanceInitWithKey:@"SFmpoiTG8y4MzCSPePPpsP" appId:@"123456" gameName:@"test" delegate:self];
    //初始化 广告SDK
    [AdManager instanceInitWithTestMode:YES delegate:self];
    //打开SDK输出log
    CLogShowLog(true);
    return YES;
}
@end

```
## AppsFlyer 设置
```ObjC
//AppDelegate中需要额外添加
- (void)applicationDidBecomeActive:(UIApplication *)application
{
    [AppsFlyerProxy applicationDidBecomeActive];
}
```
## 使用说明
#### 展示插屏广告
```ObjC
/**
	//游戏启动位置
    InterstitialEnumSplashEnd = 0,
    //游戏结束时位置
    InterstitialEnumNextLevel,
    //游戏恢复位置
    InterstitialEnumResume,
**/
[AdManager showInterstitialWithType:InterstitialEnumSplashEnd];
```
#### 展示InterstitialEnumSplashEnd 时需特殊处理
1. 展示Loading，由CP设计，一般为游戏加载动画，动画时长5'S- 10's(要求CP制作)
2. 广告展示条件 Loading页面展示时长5's后调用showInterstitialWithType:。
3. 插屏相关回调函数- (void)splashAdWillOpen; - (void)splashAdDidClose;做Loading页面的处理。
4. Loading页面设置展示时长上限，最长10's，10's后没有广告展示去除Loading，进入游戏。

#### 激励视频展示
```ObjC
// isReady block中返回激励视频是否缓冲完成。如果此时 isReady = true 只会在isReady block中回调。 未完成状态，缓冲完成后 只会在readyCallBack block 中 进行回调
[AdManager isRewardVideoReady:^(BOOL isReady) {
            if (isReady) {
                //[self hideLoading];
            }else {
                //[self showLoading];
            }
        } rewardVideoReady:^{
                //[self hideLoading];

        }];
 
//展示激励视频广告   调用show之前需调用isRewardVideoReady:rewardVideoReady:方法，等待rewardVideoReady block回调
//AdManager 类方法
+ (void)showRewardVideo;
//展示激励视频广告  携带参数版本, 一般传入点击位置标记，NSString 类型
//AdManager 类方法
+ (void)showRewardVideoParam:(id)param;
```
#### 广告展示相关的回调，AppDelegate中实现函数 optional 
```ObjC
#pragma -------------AdManagerDelegate-------
//激励视频关闭时回调，同时回调激励是否成功参数
- (void)rewardVideoReward:(NSNumber*)obj {
    CLog(@"接收到成功奖励的通知, obj is %d", [(NSNumber *)obj boolValue]);
}
- (void)rewardVideoWillShow {
    CLog(@"激励视频将要显示");
}
//所有插屏广告类型都会回调。
- (void)splashAdWillOpen{
    CLog(@"全屏广告 展示 ");
}
- (void)splashAdDidClose {
    CLog(@"全屏广告 关闭");
}
```
#### AppsFlyer识别成功后相关的回调 AppDelegate中实现函数 optional
```ObjC
#pragma ------------AppsFlyerConversionListener--------
//是否为Fb买量
- (void)onAppsFlayerReturnIsBuyFb:(BOOL)isBuyFb
{
    CLog(@"isBuyFb is %d", isBuyFb);
}
//买量识别数据返回
-(void)onAppsFlyerReturnAdSet:(NSString *)adSet
{
    CLog(@"adSet is %@", adSet);
}
//买量识别标志返回 status 自然0 非自然 1
- (void)onAppsFlyerReturnStatus:(int)status
{
    CLog(@"status is %d", status);
}
//买量识别失败返回
- (void)onAppsFlyerReturnFailure:(NSString *)failure
{
    CLog(@"failure is %@", failure);
}
//买量识别数据返回 以map形式返回
- (void)onAppsFlyerReturnSuccess:(NSDictionary  *)map
{
    CLog(@"map is %@", map);
}
```




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)