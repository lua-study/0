# EasyRTSPServer（原EasyIPCamera） #

EasyRTSPServer（原EasyIPCamera）是由[**TSINGSEE青犀开放平台**](http://open.tsingsee.com "TSINGSEE")开发的一套非常稳定、易用、支持多种平台（包括Windows/Linux 32&64，Android，ARM hisiv100/hisiv200/hisiv300/hisiv400/hisiv500/hisiv600等平台）的RTSP Server组件，适用于IPCamera、NVR、编码器、安卓监控设备等软硬件产品，接口调用非常简单成熟，调用者无需关注RTSP Server中关于客户端监听接入、音视频多路复用、RTSP具体流程、RTP打包与发送等相关问题，支持多种音视频格式，再也不用像调用live555 RTSPServer那样处理整个RTSP OPTIONS/DESCRIBE/SETUP/PLAY/RTP/RTCP的复杂流程和担心内存释放的问题了！EasyIPCamera非常适合于安防领域、教育领域、互联网直播等领域；

BTW：EasyRTSPServer非常适合在海思系列芯片上运行，性能以及稳定性都非常优秀，并发方面，稳定保持在20路1080P并发：

 - TCP/UDP 方式分别连接20路下，1080P 4M 定码率，音频格式G711（64K）G726（16K 24K 32K 40K）AAC(64K 96K 128K)都没问题；
 
 - 支持Basic、Digest两种鉴权模式；


## 功能支持 ##

- [x] 标准、稳定运行的RTSP/RTP服务；
- [x] 支持RTP over UDP/RTP over TCP；
- [x] 视频编码格式支持：H.264、H.265；
- [x] 音频编码格式支持：G.711A、G.711U、G.726、AAC；
- [x] 支持标准RTSP鉴权认证;
- [x] 灵活的SDK调用接口支持;
- [x] 丰富的SDK接口调用示例;

## 调用示例 ##

- **EasyRTSPServer**：在不同的调用平台上，我们实现了不同的调用示例；
	1. Android：采集Android摄像头（支持前/后摄像头切换）和麦克风声音作为数据源的安卓RTSPServer；
	2. EasyIPCamera_Win：Windows采集摄像头/屏幕桌面/麦克风的音视频作为数据源的RTSPServer；
	3. EasyIPCamera_RTSP：以其他IPC硬件（海康、大华、雄迈）提供的RTSP流作为EasyIPCamera的数据源，对外提供RTSPServer功能；
	4. EasyIPCameraSimulator：我们基于EasyIPCamera做的一个IPC的模拟器，一个EasyIPCameraSimulator可以模拟器很多IPC，详细介绍参考：[http://blog.csdn.net/xiejiashu/article/details/64924006](http://blog.csdn.net/xiejiashu/article/details/64924006 "EasyIPCamera")
	5. EasyScreenCapture：Windows屏幕采集与直播同屏服务，详细介绍参考：[http://blog.csdn.net/xiejiashu/article/details/61211382](http://blog.csdn.net/xiejiashu/article/details/61211382)；
	6. ARM上我们提供基于海思v100/v200/v300/v400以及其他ARM芯片的摄像机芯片编码后的音视频做为数据源的RTSPServer，具体芯片调用demo示例代码请邮件至support@easydarwin.org申请；
	
	Windows编译方法，

    	Visual Studio 2010 编译：./EasyIPCamera-master/EasyIPCamera.sln

	Linux编译方法，

		chmod +x ./Buildit
		./Buildit


	 
	   支持平台    芯片    目录位置   
	  Windows  x86  ./Lib/  
	  Windows  x64  ./Lib/x64/  
	  Linux  x86  ./Lib/  
	  Linux  x64  ./Lib/x64/  
	  Android  Android  ./Android/  
	  海思  arm-hisiv100-linux  ./Lib/hisiv100/  
	  海思  arm-hisiv200-linux  ./Lib/hisiv200/  
	  海思  arm-hisiv300-linux  ./Lib/hisiv300/  
	  海思  arm-hisiv400-linux  ./Lib/hisiv400/  
	  海思  arm-hisiv500-linux  ./Lib/hisiv500/  
	  海思  arm-hisiv600-linux  ./Lib/hisiv600/  
	   邮件获取更多平台版本   
	 


## 调用全流程 ##

![](http://www.easydarwin.org/github/images/easyipcamera/easyipcamera20160805.gif)


## 设计方法 ##

EasyIPCamera参考live555 testProg中的testOnDemandRTSPServer示例程序，将一个live555 testOnDemandRTSPServer封装在一个类中，例如，我们称为Class EasyIPCamera，在EasyIPCamera_Create接口调用时，我们新建一个EasyIPCamera对象，再通过调用EasyIPCamera_Startup接口，将EasyIPCamera RTSPServer所需要的监听端口、认证信息、通道信息等参数输入到EasyIPCamera中后，EasyIPCamera就正式开始建立监听对外服务了，在服务的过程中，当有客户端的连接或断开，都会以回调事件的形式，通知给Controller调用者，调用者再具体来处理相关的回调任务，返回给EasyIPCamera，在EasyIPCamera服务的过程当中，如果回调要求需要Controller调用者提供音视频数据帧，Controller调用者可以通过EasyIPCamera_PushFrame接口，向EasyIPCamera输送具体的音视频帧数据，当调用者需要结束RTSPServer服务，只需要调用EasyIPCamera_Shutdown停止服务，再调用EasyIPCamera_Release释放EasyIPCamera就可以了，这样整个服务过程就完整了！

## Android同屏直播效果 ##

上方的手机运行EasyIPCamera的屏幕推送功能，下面的手机使用EasyPlayer Android版本进行播放的 同屏直播效果。网络良好的时候延迟只有200多毫秒。

 
 
 

[点击观看视频](http://www.easydarwin.org/images/20170223081816450.gif "EasyIPCamera")

## 版本下载 ##

Android-EasyIPCamera： [https://fir.im/EasyIPCamera](https://fir.im/EasyIPCamera "https://fir.im/EasyIPCamera")

[![EasyIPCamera](http://www.easydarwin.org/github/images/easyipcamera/EasyIPCamera_Android.png)](https://fir.im/EasyIPCamera "EasyIPCamera")

### EasyIPCamera支持数据格式说明 ###

EASY\_SDK\_VIDEO\_FRAME\_FLAG数据可支持多种视频格式：
		
	#define EASY_SDK_VIDEO_CODEC_H265			/* H265  */
	#define EASY_SDK_VIDEO_CODEC_H264			/* H264  */
	#define	EASY_SDK_VIDEO_CODEC_MJPEG			/* MJPEG */
	#define	EASY_SDK_VIDEO_CODEC_MPEG4			/* MPEG4 */

视频帧标识支持

	#define EASY_SDK_VIDEO_FRAME_I				/* I帧 */
	#define EASY_SDK_VIDEO_FRAME_P				/* P帧 */
	#define EASY_SDK_VIDEO_FRAME_B				/* B帧 */
	#define EASY_SDK_VIDEO_FRAME_J				/* JPEG */

EASY\_SDK\_AUDIO\_FRAME\_FLAG数据可支持多种音频格式：
	
	#define EASY_SDK_AUDIO_CODEC_AAC			/* AAC */
	#define EASY_SDK_AUDIO_CODEC_G711A			/* G711 alaw*/
	#define EASY_SDK_AUDIO_CODEC_G711U			/* G711 ulaw*/
	#define EASY_SDK_AUDIO_CODEC_G726			/* G726 */


## 技术支持 ##

- 邮件：[support@easydarwin.org](mailto:support@easydarwin.org) 

- QQ交流群：**692496281**


## 更多流媒体音视频资源

EasyDarwin开源流媒体服务器： www.EasyDarwin.org 

EasyDSS高性能互联网直播服务： www.EasyDSS.com 

EasyNVR安防视频可视化服务： www.EasyNVR.com 

EasyNVS视频综合管理平台： www.EasyNVS.com 

EasyNTS云组网： www.EasyNTS.com 

EasyGBS国标GB/T28181服务器： www.EasyGBS.com 

EasyRTS应急指挥平台： www.EasyRTS.com 

TSINGSEE青犀开放平台： open.TSINGSEE.com 

Copyright ©  www.TSINGSEE.com  Team 2012-2019

![青犀TSINGSEE](http://www.easydarwin.org/public/images/tsingsee_qrcode_160.jpg)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)