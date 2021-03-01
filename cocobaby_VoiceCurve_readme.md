# 声音大小显示演示项目

---

##预览

![预览][1]

##描述

这是一个多个模块API的使用演示项目，包括声音的大小采集、自定义曲线图、感光API的使用等

##使用说明

####XML布局文件
```
 
```

####页面中使用
```
        mCurveView = (CurveView) this.findViewById(R.id.curve);
        mButton = (Button) this.findViewById(R.id.button1);
        mButton.setOnClickListener(new OnClickListener() {

            @Override
            public void onClick(View arg0) {
                if (mIsStop) {
                    recordThread = new RecordThread(mHandler);
                    recordThread.startRecord();
                    mCurveView.clearScreen();
                    mButton.setText("停止");
                    mIsStop = false;
                } else {
                    recordThread.stopRecord();
                    mButton.setText("开始");
                    mIsStop = true;
                }
            }
        });
```

##更多

- [我的个人博客](http://www.hikyson.cn)

- [我的开源项目](http://git.oschina.net/cocobaby)

- [我的新浪微博](http://weibo.com/1980495343/profile?rightmod=1&wvr=6&mod=personinfo)

##License

Copyright (c) 2014 Kyson

Licensed under the [Apache License, Version 2.0](http://www.apache.org/licenses/LICENSE-2.0)

[1]:http://kkwordpress-wordpress.stor.sinaapp.com/uploads/2014/12/tt_voice_curve_showcase.gif

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)