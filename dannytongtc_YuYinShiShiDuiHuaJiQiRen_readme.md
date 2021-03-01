# 语音实时对话机器人
 **简介：** 

结合百度语音识别，图灵机器人和百度语音合成实现的实时对话机器人，相较[第一版树莓派实时对话机器人](http://blog.csdn.net/lingdongtianxia/article/details/54799306)反应速度，使用体验有很大提升。现在这个机器人支持搜索图片、火车票、新闻和菜谱等，最主要的更新是加入了 **下载付费歌曲** 的功能，这个功能真的超级装逼，唤醒之后只需要说“下载稻香”，一首付费的  **稻香.mp3**  就在你电脑上了。具体功能详见图灵官网。

 **文件结构:** 
```
|——audio
|  |——_output_file.wav  #录音时的音频缓冲文件
|  |——man.wav  #录音文件，说话的声音信息在这里面
|  |——machine.mp3  #百度语音合成返回的MP3文件
|  |——machine.wav  #MP3文件转码后的WAV格式音频文件
|——LoginInfo.txt  #百度云语音识别登录信息，自己注册百度云账号得到自己的登录信息写在这个文件中
|——family.py  #语音对话功能集成库
|——example.py  #例程，运行这个文件以体验全部功能


```
 **链接：** 

[百度云登录](https://login.bce.baidu.com/)

[图灵机器人官网](http://www.tuling123.com/)

[pygame文档](http://pygame.org/docs/)

 **环境及安装方法：**
```
版本：
    windows10 、python3.6
相关库：
    pydub 安装方法 pip install pydub
    aip   安装方法 pip install baidu-aip
    别的库自己缺什么pip install什么吧，Linux别忘了权限问题 
```



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)