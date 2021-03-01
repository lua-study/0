android-app
===========

项目中引用的第三方库比较多，首先是HoloEverywhere项目，其中包括HoloEverywhere Library和HoloEverywhere Addon Preferences，其次是ActionBarPullToRefresh项目，用到了ActionBar-PullToRefresh / extras / actionbarcompat，编译时先要引用HoloEverywhere Library和ActionBarPullToRefresh Library，还有SlidingMenu项目，编译时需引用HoloEverywhere Library，然后修改SlidingMenu/app中的Activity为对应HoloEverywhere Library的Activity(SlidingActivity、SlidingFragmentActivity继承holo中的activity,SlidingListActivity继承holo中的ListActivity,SlidingPreferenceActivity继承holo中的PreferenceActivity)，最后还引用了ViewPagerIndicator 和AppMsg，编译时注意保持support-v4的统一。

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)