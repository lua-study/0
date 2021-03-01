mysql 5.5.3

表1：vod_project
	id		int				//项目ID
	title		varchat		utf8		//标题
	banner		varchat		utf8		//头图，用图片链接
	number		int				//访问人数
	vod_class	int				//视频类型，直播or点播
	channel_id	varchar		utf8		//1为直播，2为点播

表2：vod_chat
	vod_id		int				//项目ID
	user_name	varchar		utf8mb4		//用户名
	user_head	varchar		utf8		//用户头像
	user_talk	varchar		utf8mb4		//用户发言内容
	openid		varchar		utf8		//用户基于微信服务号的OPENID

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)