#WuXianAir
仅供大家学习交流，可以加QQ群"cocos2d-x手游-倾国倾城"共同学习
群号：211249919

配置和下载说明参照“GameCore说明.doc”

感谢BWOLF提供改过的核心库libGameCore，不过还有些问题，大家帮忙改改，提交到群里，谢谢
改之前的libGameCore，命名为“libGameCore原.rar”

增加win32大包工具packager.cmd

新版添加dfont
改了如下文件
1.WXGrid.cpp
std::string fileName = filename;
2.WXSimpleButton.cpp
m_label = NULL;
3.WXUIDefine.h
#if (CC_TARGET_PLATFORM == CC_PLATFORM_WIN32)
#define FONT_NAME_DEFAULT	"msyh"
#elif (CC_TARGET_PLATFORM == CC_PLATFORM_IOS)
#define FONT_NAME_DEFAULT	"_H_Helvetica"
#elif (CC_TARGET_PLATFORM == CC_PLATFORM_MAC)
#define FONT_NAME_DEFAULT	"Helvetica"
#elif (CC_TARGET_PLATFORM == CC_PLATFORM_ANDROID)
#define FONT_NAME_DEFAULT	"DroidSansFallback"
#elif (CC_TARGET_PLATFORM == CC_PLATFORM_LINUX)
#define FONT_NAME_DEFAULT	"FreeSerif"
#else
#define FONT_NAME_DEFAULT	""
#endif
4.gamecore.h
#include "dfont/dfont_manager.h"
#include "dfont/dfont_utility.h"


PerformancePanel.cpp 
PerformanceMgr.h low_performance_reason_app_memory_high


WXBaseNode 点击面板崩溃 m_pListener = NULL; m_pfnSelector = NULL;
BGMap.cpp addBackgroundBg();//地图无法加载，改后加

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)