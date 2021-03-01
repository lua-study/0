# GCWSDK_IOS
# 第一步 将demo工程目录下的 Debug-iphoneos 目录拖到自己的工程目录下
# 第二步 初始化摄像机
##    self.cameraRecorder=[[CameraRecorder alloc] initWithParams:self.preView delegate:self

## userDeniedAuthorizationBlock:^{
##        NSLog(@"请允许访问相机");
##   }];
# 第三步:准备好伴奏音乐
## [[AudioManager manager] createAudioPlayerFromUrl:self.mp3Url delegate:self];
# 第四步:开始拍摄
##   [self.cameraRecorder startRecord];
##   [[AudioManager manager] play];
##   [sender setTitle:@"停止拍摄" forState:UIControlStateNormal];
# 第五步 音乐放完了或者按了停止拍摄键，就停止拍摄 
## [self.cameraRecorder stopRecord];
# 第六步 在 -(void)RecordFinshed:(NSURL *)outPutVideoUrl error:(NSError*)error 这个方法里面 可以进行设置片头或直接转换视频
## 设置片头  
## self.titlesModel.view=view; 为设置片头界面片头所对应的容器view，片头背景图片的UIImageView 和 片头字幕 的UILabel 都必须是这个容器view 的子view
##  self.titlesModel.duration=3.0f; 设置片头的持续时间，单位为秒
##
##  转换视频:
## 生成含特效的视频
##  [[VideoEffectUtil sharedInstance] addEffect:self.outPutVideoUrl bgMusicUrl:self.mp3Url lyricData:nil borderModel:self.cameraRecorder.borderModel cammeraTranfromModel:self.cameraRecorder.tranformModel titlesModel:self.titlesModel progressBlock:^(float prog) {
##        NSLog(@"progress: %f",prog);
##       dispatch_async(dispatch_get_main_queue(), ^{
##            //注意在主线程更新UI
            
##      });
##   } completeBlock:^(ALAsset *asset) {
##      weakSelf.captureButton.enabled=YES;
##       NSLog(@"url: %@",asset.defaultRepresentation.url);
##  } failureBlock:^(NSError *error) {
##       //没有相册写入权限、磁盘空间不足等会在这里报错
##      weakSelf.captureButton.enabled=YES;
        
##       NSLog(@"error: %@",error);
##   }];



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)