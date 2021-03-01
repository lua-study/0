# WeixinBot [![star this repo](http://github-svg-buttons.herokuapp.com/star.svg?user=Urinx&repo=WeixinBot&style=flat&background=1081C1)](http://github.com/Urinx/WeixinBot) [![fork this repo](http://github-svg-buttons.herokuapp.com/fork.svg?user=Urinx&repo=WeixinBot&style=flat&background=1081C1)](http://github.com/Urinx/WeixinBot/fork) ![python](https://img.shields.io/badge/python-2.7-ff69b4.svg)

网页版微信API，包含终端版微信及微信机器人

## Demo
为了运行 `weixin.py` 示例脚本，你需要有安装 `qrcode` 包，你可以通过 `pip install qrcode` 来安装。

![1](screenshot/1.png)

按照操作指示在手机微信上扫描二维码然后登录，你可以选择是否开启自动回复模式。

![2](screenshot/2.png)

开启自动回复模式后，如果接收到的是文字消息就会自动回复，包括群消息。

![3](screenshot/3.png)

现在，名片，链接，动画表情和地址位置消息都可以正常接收。

![4](screenshot/4.png)

![5](screenshot/5.png)

**目前支持的命令**：

`->[昵称或ID]:[内容]` 给好友发送消息

`m->[昵称或ID]:[文件路径]` 给好友发送文件中的内容

![6](screenshot/6.png)

`f->[昵称或ID]:[文件路径]` 给好友发送文件

`i->[昵称或ID]:[图片路径]` 给好友发送图片

`e->[昵称或ID]:[文件路径]` 给好友发送表情(jpg/gif)

`quit` 退出程序

![7](screenshot/7.png)

注意，以上命令均不包含方括号。

## Web Weixin Pipeline

```
       +--------------+     +---------------+   +---------------+
       |              |     |               |   |               |
       |   Get UUID   |     |  Get Contact  |   | Status Notify |
       |              |     |               |   |               |
       +-------+------+     +-------^-------+   +-------^-------+
               |                    |                   |
               |                    +-------+  +--------+
               |                            |  |
       +-------v------+               +-----+--+------+      +--------------+
       |              |               |               |      |              |
       |  Get QRCode  |               |  Weixin Init  +------>  Sync Check       Login     +---------------> New Login Page |     |  Weixin Sync  |
|      |              |               |                |     |               |
|      +------+-------+               +----------------+     +---------------+
|             |
|QRCode Scaned|
+-------------+
```

## Web Weixin API

### 登录

| API | 获取 UUID |
| --- | --------- |
| url | https://login.weixin.qq.com/jslogin |
| method | POST |
| data | URL Encode |
| params | **appid**: `应用ID`   **fun**: new `应用类型`   **lang**: zh\_CN `语言`   **_**: `时间戳` |

返回数据(String):
```
window.QRLogin.code = 200; window.QRLogin.uuid = "xxx"
```
> 注：这里的appid就是在微信开放平台注册的应用的AppID。网页版微信有两个AppID，早期的是`wx782c26e4c19acffb`，在微信客户端上显示为应用名称为`Web微信`；现在用的是`wxeb7ec651dd0aefa9`，显示名称为`微信网页版`。

![6](screenshot/8.jpg)
 

| API | 生成二维码 |
| --- | --------- |
| url | https://login.weixin.qq.com/l/ `uuid` |
 

| API | 二维码扫描登录 |
| --- | --------- |
| url | https://login.weixin.qq.com/cgi-bin/mmwebwx-bin/login |
| method | GET |
| params | **tip**: 1 `未扫描` 0 `已扫描`   **uuid**: xxx   **_**: `时间戳` |

返回数据(String):
```
window.code=xxx;

xxx:
	408 登陆超时
	201 扫描成功
	200 确认登录

当返回200时，还会有
window.redirect_uri="https://wx.qq.com/cgi-bin/mmwebwx-bin/webwxnewloginpage?ticket=xxx&uuid=xxx&lang=xxx&scan=xxx";
```
 

| API | webwxnewloginpage |
| --- | --------- |
| url | https://wx.qq.com/cgi-bin/mmwebwx-bin/webwxnewloginpage |
| method | GET |
| params | **ticket**: xxx   **uuid**: xxx   **lang**: zh_CN `语言`   **scan**: xxx   **fun**: new |

返回数据(XML):
```
 
	 0 
	 OK 
	 xxx 
	 xxx 
	 xxx 
	 xxx 
	 1 
 
```
 

### 微信初始化

| API | webwxinit |
| --- | --------- |
| url | https://wx.qq.com/cgi-bin/mmwebwx-bin/webwxinit?pass_ticket=xxx&skey=xxx&r=xxx |
| method | POST |
| data | JSON |
| header | ContentType: application/json; charset=UTF-8 |
| params | {   &nbsp;&nbsp;&nbsp;&nbsp; BaseRequest: {   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;	Uin: xxx,  	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Sid: xxx,   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;	Skey: xxx,   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; DeviceID: xxx,   &nbsp;&nbsp;&nbsp;&nbsp; }   } |

返回数据(JSON):
```
{
	"BaseResponse": {
		"Ret": 0,
		"ErrMsg": ""
	},
	"Count": 11,
	"ContactList": [...],
	"SyncKey": {
		"Count": 4,
		"List": [
			{
				"Key": 1,
				"Val": 635705559
			},
			...
		]
	},
	"User": {
		"Uin": xxx,
		"UserName": xxx,
		"NickName": xxx,
		"HeadImgUrl": xxx,
		"RemarkName": "",
		"PYInitial": "",
		"PYQuanPin": "",
		"RemarkPYInitial": "",
		"RemarkPYQuanPin": "",
		"HideInputBarFlag": 0,
		"StarFriend": 0,
		"Sex": 1,
		"Signature": "Apt-get install B",
		"AppAccountFlag": 0,
		"VerifyFlag": 0,
		"ContactFlag": 0,
		"WebWxPluginSwitch": 0,
		"HeadImgFlag": 1,
		"SnsFlag": 17
	},
	"ChatSet": xxx,
	"SKey": xxx,
	"ClientVersion": 369297683,
	"SystemTime": 1453124908,
	"GrayScale": 1,
	"InviteStartCount": 40,
	"MPSubscribeMsgCount": 2,
	"MPSubscribeMsgList": [...],
	"ClickReportInterval": 600000
}
```
 

| API | webwxstatusnotify |
| --- | --------- |
| url | https://wx.qq.com/cgi-bin/mmwebwx-bin/webwxstatusnotify?lang=zh_CN&pass_ticket=xxx |
| method | POST |
| data | JSON |
| header | ContentType: application/json; charset=UTF-8 |
| params | {   &nbsp;&nbsp;&nbsp;&nbsp; BaseRequest: { Uin: xxx, Sid: xxx, Skey: xxx, DeviceID: xxx },   &nbsp;&nbsp;&nbsp;&nbsp; Code: 3,   &nbsp;&nbsp;&nbsp;&nbsp; FromUserName: `自己ID`,   &nbsp;&nbsp;&nbsp;&nbsp; ToUserName: `自己ID`,   &nbsp;&nbsp;&nbsp;&nbsp; ClientMsgId: `时间戳`   } |

返回数据(JSON):
```
{
	"BaseResponse": {
		"Ret": 0,
		"ErrMsg": ""
	},
	...
}
```
 

### 获取联系人信息

| API | webwxgetcontact |
| --- | --------- |
| url | https://wx.qq.com/cgi-bin/mmwebwx-bin//webwxgetcontact?pass_ticket=xxx&skey=xxx&r=xxx |
| method | POST |
| data | JSON |
| header | ContentType: application/json; charset=UTF-8 |

返回数据(JSON):
```
{
	"BaseResponse": {
		"Ret": 0,
		"ErrMsg": ""
	},
	"MemberCount": 334,
	"MemberList": [
		{
			"Uin": 0,
			"UserName": xxx,
			"NickName": "Urinx",
			"HeadImgUrl": xxx,
			"ContactFlag": 3,
			"MemberCount": 0,
			"MemberList": [],
			"RemarkName": "",
			"HideInputBarFlag": 0,
			"Sex": 0,
			"Signature": "你好，我们是地球三体组织。在这里，你将感受到不一样的思维模式，以及颠覆常规的世界观。而我们的目标，就是以三体人的智慧，引领人类未来科学技术500年。",
			"VerifyFlag": 8,
			"OwnerUin": 0,
			"PYInitial": "URINX",
			"PYQuanPin": "Urinx",
			"RemarkPYInitial": "",
			"RemarkPYQuanPin": "",
			"StarFriend": 0,
			"AppAccountFlag": 0,
			"Statues": 0,
			"AttrStatus": 0,
			"Province": "",
			"City": "",
			"Alias": "Urinxs",
			"SnsFlag": 0,
			"UniFriend": 0,
			"DisplayName": "",
			"ChatRoomId": 0,
			"KeyWord": "gh_",
			"EncryChatRoomId": ""
		},
		...
	],
	"Seq": 0
}
```
 

| API | webwxbatchgetcontact |
| --- | --------- |
| url | https://wx.qq.com/cgi-bin/mmwebwx-bin/webwxbatchgetcontact?type=ex&r=xxx&pass_ticket=xxx |
| method | POST |
| data | JSON |
| header | ContentType: application/json; charset=UTF-8 |
| params | {   &nbsp;&nbsp;&nbsp;&nbsp; BaseRequest: { Uin: xxx, Sid: xxx, Skey: xxx, DeviceID: xxx },   &nbsp;&nbsp;&nbsp;&nbsp; Count: `群数量`,   &nbsp;&nbsp;&nbsp;&nbsp; List: [   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; { UserName: `群ID`, EncryChatRoomId: "" },   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ...   &nbsp;&nbsp;&nbsp;&nbsp; ],   } |

返回数据(JSON)同上
  

### 同步刷新

| API | synccheck |
| --- | --------- |
| protocol | https |
| host | webpush.weixin.qq.com   webpush2.weixin.qq.com   webpush.wechat.com   webpush1.wechat.com   webpush2.wechat.com   webpush.wechatapp.com   webpush1.wechatapp.com |
| path | /cgi-bin/mmwebwx-bin/synccheck |
| method | GET |
| data | URL Encode |
| params | **r**: `时间戳`   **sid**: xxx   **uin**: xxx   **skey**: xxx   **deviceid**: xxx   **synckey**: xxx   **_**: `时间戳` |

返回数据(String):
```
window.synccheck={retcode:"xxx",selector:"xxx"}

retcode:
	0 正常
	1100 失败/登出微信
selector:
	0 正常
	2 新的消息
	7 进入/离开聊天界面
```
 

| API | webwxsync |
| --- | --------- |
| url | https://wx.qq.com/cgi-bin/mmwebwx-bin/webwxsync?sid=xxx&skey=xxx&pass_ticket=xxx |
| method | POST |
| data | JSON |
| header | ContentType: application/json; charset=UTF-8 |
| params | {   &nbsp;&nbsp;&nbsp;&nbsp; BaseRequest: { Uin: xxx, Sid: xxx, Skey: xxx, DeviceID: xxx },   &nbsp;&nbsp;&nbsp;&nbsp; SyncKey: xxx,   &nbsp;&nbsp;&nbsp;&nbsp; rr: `时间戳取反`   } |

返回数据(JSON):
```
{
	'BaseResponse': {'ErrMsg': '', 'Ret': 0},
	'SyncKey': {
		'Count': 7,
		'List': [
			{'Val': 636214192, 'Key': 1},
			...
		]
	},
	'ContinueFlag': 0,
	'AddMsgCount': 1,
	'AddMsgList': [
		{
			'FromUserName': '',
			'PlayLength': 0,
			'RecommendInfo': {...},
			'Content': "", 
			'StatusNotifyUserName': '',
			'StatusNotifyCode': 5,
			'Status': 3,
			'VoiceLength': 0,
			'ToUserName': '',
			'ForwardFlag': 0,
			'AppMsgType': 0,
			'AppInfo': {'Type': 0, 'AppID': ''},
			'Url': '',
			'ImgStatus': 1,
			'MsgType': 51,
			'ImgHeight': 0,
			'MediaId': '', 
			'FileName': '',
			'FileSize': '',
			...
		},
		...
	],
	'ModChatRoomMemberCount': 0,
	'ModContactList': [],
	'DelContactList': [],
	'ModChatRoomMemberList': [],
	'DelContactCount': 0,
	...
}
```
 

### 消息接口

| API | webwxsendmsg |
| --- | ------------ |
| url | https://wx.qq.com/cgi-bin/mmwebwx-bin/webwxsendmsg?pass_ticket=xxx |
| method | POST |
| data | JSON |
| header | ContentType: application/json; charset=UTF-8 |
| params | {   &nbsp;&nbsp;&nbsp;&nbsp; BaseRequest: { Uin: xxx, Sid: xxx, Skey: xxx, DeviceID: xxx },   &nbsp;&nbsp;&nbsp;&nbsp; Msg: {   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Type: 1 `文字消息`,   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Content: `要发送的消息`,   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; FromUserName: `自己ID`,   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ToUserName: `好友ID`,   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; LocalID: `与clientMsgId相同`,   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ClientMsgId: `时间戳左移4位随后补上4位随机数`   &nbsp;&nbsp;&nbsp;&nbsp; }   } |

返回数据(JSON):
```
{
	"BaseResponse": {
		"Ret": 0,
		"ErrMsg": ""
	},
	...
}
```

#### 发送表情

| API | webwxsendmsgemotion |
| --- | ------------ |
| url | https://wx2.qq.com/cgi-bin/mmwebwx-bin/webwxsendemoticon?fun=sys&f=json&pass_ticket=xxx |
| method | POST |
| data | JSON |
| header | ContentType: application/json; charset=UTF-8 |
| params | {   &nbsp;&nbsp;&nbsp;&nbsp; BaseRequest: { Uin: xxx, Sid: xxx, Skey: xxx, DeviceID: xxx },   &nbsp;&nbsp;&nbsp;&nbsp; Msg: {   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Type: 47 `emoji消息`,   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; EmojiFlag: 2,   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; MediaId: `表情上传后的媒体ID`,   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; FromUserName: `自己ID`,   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ToUserName: `好友ID`,   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; LocalID: `与clientMsgId相同`,   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ClientMsgId: `时间戳左移4位随后补上4位随机数`   &nbsp;&nbsp;&nbsp;&nbsp; }   } |

 

### 图片接口

| API | webwxgeticon |
| --- | ------------ |
| url | https://wx.qq.com/cgi-bin/mmwebwx-bin/webwxgeticon |
| method | GET |
| params | **seq**: `数字，可为空`   **username**: `ID`   **skey**: xxx |
 

| API | webwxgetheadimg |
| --- | --------------- |
| url | https://wx.qq.com/cgi-bin/mmwebwx-bin/webwxgetheadimg |
| method | GET |
| params | **seq**: `数字，可为空`   **username**: `群ID`   **skey**: xxx |
 

| API | webwxgetmsgimg |
| --- | --------------- |
| url | https://wx.qq.com/cgi-bin/mmwebwx-bin/webwxgetmsgimg |
| method | GET |
| params | **MsgID**: `消息ID`   **type**: slave `略缩图` or `为空时加载原图`   **skey**: xxx |
 

### 多媒体接口

| API | webwxgetvideo |
| --- | --------------- |
| url | https://wx.qq.com/cgi-bin/mmwebwx-bin/webwxgetvideo |
| method | GET |
| params | **msgid**: `消息ID`   **skey**: xxx |
 

| API | webwxgetvoice |
| --- | --------------- |
| url | https://wx.qq.com/cgi-bin/mmwebwx-bin/webwxgetvoice |
| method | GET |
| params | **msgid**: `消息ID`   **skey**: xxx |
 

### 账号类型

| 类型 | 说明 |
| :--: | --- |
| 个人账号 | 以`@`开头，例如：`@xxx` |
| 群聊 | 以`@@`开头，例如：`@@xxx` |
| 公众号/服务号 | 以`@`开头，但其`VerifyFlag` & 8 != 0    `VerifyFlag`:   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 一般公众号/服务号：8   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 微信自家的服务号：24   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 微信官方账号`微信团队`：56 |
| 特殊账号 | 像文件传输助手之类的账号，有特殊的ID，目前已知的有：  `filehelper`, `newsapp`, `fmessage`, `weibo`, `qqmail`, `fmessage`, `tmessage`, `qmessage`, `qqsync`, `floatbottle`, `lbsapp`, `shakeapp`, `medianote`, `qqfriend`, `readerapp`, `blogapp`, `facebookapp`, `masssendapp`, `meishiapp`, `feedsapp`, `voip`, `blogappweixin`, `weixin`, `brandsessionholder`, `weixinreminder`, `officialaccounts`, `notification_messages`, `wxitil`, `userexperience_alarm`, `notification_messages` |
 

### 消息类型

消息一般格式：
```
{
	"FromUserName": "",
	"ToUserName": "",
	"Content": "",
	"StatusNotifyUserName": "",
	"ImgWidth": 0,
	"PlayLength": 0,
	"RecommendInfo": {...},
	"StatusNotifyCode": 4,
	"NewMsgId": "",
	"Status": 3,
	"VoiceLength": 0,
	"ForwardFlag": 0,
	"AppMsgType": 0,
	"Ticket": "",
	"AppInfo": {...},
	"Url": "",
	"ImgStatus": 1,
	"MsgType": 1,
	"ImgHeight": 0,
	"MediaId": "",
	"MsgId": "",
	"FileName": "",
	"HasProductId": 0,
	"FileSize": "",
	"CreateTime": 1454602196,
	"SubMsgType": 0
}
```
 

| MsgType | 说明 |
| ------- | --- |
| 1  | 文本消息 |
| 3  | 图片消息 |
| 34 | 语音消息 |
| 37 | VERIFYMSG |
| 40 | POSSIBLEFRIEND_MSG |
| 42 | 共享名片 |
| 43 | 视频通话消息 |
| 47 | 动画表情 |
| 48 | 位置消息 |
| 49 | 分享链接 |
| 50 | VOIPMSG |
| 51 | 微信初始化消息 |
| 52 | VOIPNOTIFY |
| 53 | VOIPINVITE |
| 62 | 小视频 |
| 9999 | SYSNOTICE |
| 10000 | 系统消息 |
| 10002 | 撤回消息 |
 

**微信初始化消息**
```html
MsgType: 51
FromUserName: 自己ID
ToUserName: 自己ID
StatusNotifyUserName: 最近联系的联系人ID
Content:
	 
	     
	         
	        	// 最近联系的联系人
	            filehelper,xxx@chatroom,wxid_xxx,xxx,...
	         
	         
	             
	                 
	                	// 朋友圈
	                    MomentsUnreadMsgStatus
	                 
	                 
	                    1454502365
	                 
	             
	         
	         
	        	// 未读的功能账号消息，群发助手，漂流瓶等
	         
	     
	 
```

**文本消息**
```
MsgType: 1
FromUserName: 发送方ID
ToUserName: 接收方ID
Content: 消息内容
```

**图片消息**
```html
MsgType: 3
FromUserName: 发送方ID
ToUserName: 接收方ID
MsgId: 用于获取图片
Content:
	 
		 
		  
	 
```

**小视频消息**
```html
MsgType: 62
FromUserName: 发送方ID
ToUserName: 接收方ID
MsgId: 用于获取小视频
Content:
	 
		 
		  
	 
```

**地理位置消息**
```
MsgType: 1
FromUserName: 发送方ID
ToUserName: 接收方ID
Content: http://weixin.qq.com/cgi-bin/redirectforward?args=xxx
// 属于文本消息，只不过内容是一个跳转到地图的链接
```

**名片消息**
```js
MsgType: 42
FromUserName: 发送方ID
ToUserName: 接收方ID
Content:
	 
	 

RecommendInfo:
	{
		"UserName": "xxx", // ID
		"Province": "xxx", 
		"City": "xxx", 
		"Scene": 17, 
		"QQNum": 0, 
		"Content": "", 
		"Alias": "xxx", // 微信号
		"OpCode": 0, 
		"Signature": "", 
		"Ticket": "", 
		"Sex": 0, // 1:男, 2:女
		"NickName": "xxx", // 昵称
		"AttrStatus": 4293221, 
		"VerifyFlag": 0
	}
```

**语音消息**
```html
MsgType: 34
FromUserName: 发送方ID
ToUserName: 接收方ID
MsgId: 用于获取语音
Content:
	 
		 
	 
```

**动画表情**
```html
MsgType: 47
FromUserName: 发送方ID
ToUserName: 接收方ID
Content:
	 
		   
		  
	 
```

**普通链接或应用分享消息**
```html
MsgType: 49
AppMsgType: 5
FromUserName: 发送方ID
ToUserName: 接收方ID
Url: 链接地址
FileName: 链接标题
Content:
	 
		 
			  
			  
			 5 
			  
			  
			  
			...
		 
		 
			  
			  
		 
	 
```

**音乐链接消息**
```html
MsgType: 49
AppMsgType: 3
FromUserName: 发送方ID
ToUserName: 接收方ID
Url: 链接地址
FileName: 音乐名

AppInfo: // 分享链接的应用
	{
		Type: 0, 
		AppID: wx485a97c844086dc9
	}

Content:
	 
		 
			  
			  
			  
			 3 
			 0 
			  
			  
			  
			  
			 0 
			  
			  
			 
				http://ws.stream.qqmusic.qq.com/C100003i9hMt1bgui0.m4a?vkey=6867EF99F3684&amp;guid=ffffffffc104ea2964a111cf3ff3edaf&amp;fromtag=46
			 
			 
				http://ws.stream.qqmusic.qq.com/C100003i9hMt1bgui0.m4a?vkey=6867EF99F3684&amp;guid=ffffffffc104ea2964a111cf3ff3edaf&amp;fromtag=46
			 
			 
				 0 
				  
				  
				  
			 
			  
			  
			  
			  
			 
				http://imgcache.qq.com/music/photo/album/63/180_albumpic_143163_0.jpg
			 
			  
		 
		  
		 0 
		 
			 29 
			 摇一摇搜歌 
		 
		  
	 
```

**群消息**
```
MsgType: 1
FromUserName: @@xxx
ToUserName: @xxx
Content:
	@xxx: xxx
```

**红包消息**
```
MsgType: 49
AppMsgType: 2001
FromUserName: 发送方ID
ToUserName: 接收方ID
Content: 未知
```
注：根据网页版的代码可以看到未来可能支持查看红包消息，但目前走的是系统消息，见下。

**系统消息**
```
MsgType: 10000
FromUserName: 发送方ID
ToUserName: 自己ID
Content:
	"你已添加了 xxx ，现在可以开始聊天了。"
	"如果陌生人主动添加你为朋友，请谨慎核实对方身份。"
	"收到红包，请在手机上查看"
```

持续更新中 ...

## Todo
- [x] 发送图片或者文件功能
- [ ] 主动给群聊发送消息
- [ ] 建立群聊
- [x] 群发消息
- [ ] 补充更多的接口及完善文档

P.S. 还有啥要补充的也可以在[issue #8](https://github.com/Urinx/WeixinBot/issues/8)下留言


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)