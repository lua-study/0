###讯飞语音识别功能开发
####效果图
![输入图片说明](http://git.oschina.net/uploads/images/2017/0122/111947_7c777258_370055.gif "在这里输入图片标题")
####开发详情
1.引用讯飞的SDK
这里就不赘述了，讯飞的开发者文档中写的很清楚，这里就不赘述了。
2.合理利用SDK包中的demo程序
在官网下载sdk时，其实讯飞已经帮你把appid嵌入到你的demo例子中去了，你可以参照这个例子编写自己的代码；
例子代码中实现了一个带有界面的实现方式，用的是`IFlyRecognizerView`这个相对简单一点，看一下代码实现立刻就能明白；
如果要想自己设计界面单纯的调用讯飞的api，那么需要使用`IFlySpeechRecognizer`类方法，好在开发文档中有关于无界面api的使用帮助。
步骤1.我们的app的启动项中初始化我们的api接口如下：
```objc
/**
     *讯飞语音初始化
     **/
    [IFlySetting setLogFile:LVL_ALL];
    [IFlySetting showLogcat:YES];
    
    NSArray *paths = NSSearchPathForDirectoriesInDomains(NSCachesDirectory, NSUserDomainMask, YES);
    NSString *cachePath = [paths objectAtIndex:0];
    [IFlySetting setLogFilePath:cachePath];
    
    NSString *initString = [[NSString alloc] initWithFormat:@"appid=%@",@"*****"];
    [IFlySpeechUtility createUtility:initString];
```
步骤2.实现IFlySpeechRecognizerDelegate代理方法
```objc
@interface VoiceViewController : UIViewController 
//语音识别对象
@property (nonatomic, strong) IFlySpeechRecognizer *iFlySpeechRecognizer;

@property (strong, nonatomic) IBOutlet UITextField *vioceNumber;
@property (strong, nonatomic) IBOutlet UIButton *Vbutton;
@property (strong,nonatomic) NSMutableString *song;

@end


#pragma mark - IFlySpeechRecognizerDelegate
- (void)onVolumeChanged:(int)volume{
    NSLog(@"音频的声音------------------%d",volume);
    //录音的音量，音量范围1~100
    if (volume>=0 &&volume 2 && volume<=3){
        speechImage.image = [UIImage imageNamed:@"yuyin_02.png"];
    }else{
        speechImage.image = [UIImage imageNamed:@"yuyin_03.png"];
    }
}

- (void)onResults:(NSArray *)results isLast:(BOOL)isLast{
    NSMutableString *result = [[NSMutableString alloc] init];
    NSDictionary *dic = [results objectAtIndex:0];
    NSLog(@"-----ls------%@",[dic objectForKey:@"ls"]);
    for (NSString *key in dic) {
        [result appendFormat:@"%@",key];
    }
    NSLog(@"转写结果--------------------------：%@--results:%@",result,results);
    
    NSString * resultFromJson =  [ISRDataHelper stringFromJson:result];
    if (resultFromJson.length <= 1) {
        return;
    }
    _vioceNumber.text = resultFromJson;
    NSLog(@"result---%@",resultFromJson);
    
    //返回结果
}


```
步骤3.就是通过点击button按钮来开启录音方法
```objc
- (void)viewDidLoad {
    //初始化讯飞语音识别
    _iFlySpeechRecognizer = [IFlySpeechRecognizer sharedInstance];
    //开始识别
    [_iFlySpeechRecognizer setParameter:@"asr_ptt" forKey:0];
    [_iFlySpeechRecognizer setParameter:@"language" forKey:@"en_us"];
    
    _iFlySpeechRecognizer.delegate = self;
    
    [_Vbutton addTarget:self action:@selector(startVoice:) forControlEvents:UIControlEventTouchDown];
    [_Vbutton addTarget:self action:@selector(finishVoice:) forControlEvents:UIControlEventTouchUpInside];
    
    [super viewDidLoad];
}
````
####易错点
第一、当鼠标弹起是就停止录音注销录音方法，导致了根本就没有走Onresult的方法，也就没有返回结果了。
    解决办法：之暂停服务即可，虽然这种方法可能导致内存溢出，但是ios本身有自己的一套垃圾清除机制。
```objc
- (void)finishVoice:(UIButton *)button{
    NSLog(@"finishVoice---finish-------------结束录制");
    [_iFlySpeechRecognizer stopListening];
    
//    [_iFlySpeechRecognizer cancel];
//    [_iFlySpeechRecognizer setDelegate:nil];
//    _iFlySpeechRecognizer = nil;
    _vioceNumber.text = _song;
    NSLog(@"-----song-------%@",_song);   
}
```
第二、讯飞的bug导致的，原因不详。在网上了找了一些解决办法这种方式算是效果最好的吧。
在我录音结束后，系统还会自动收集声音进行解析，所以这里必须把后面的那个声音给踢出出去，可以设置一个boolean变量，第一次为true第二次为false这样来分支，还可以判断解析出来的字符长度。这里一般是有一个“。”在里面的。
`转写结果--------------------------：{"sn":2,"ls":true,"bg":0,"ed":0,"ws":[{"bg":0,"cw":[{"sc":0.00,"w":"。"}]}]`
```obj-c
if (resultFromJson.length <= 1) {
        return;
    }
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)