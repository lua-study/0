#  LevelDB-win编译方案

#![输入图片说明](https://gitee.com/uploads/images/2017/1213/211714_5aad0487_3843.png "ocquant.png")

>1，git checkout origin/windows

>2，打开db/c.cc文件，将第八行位置修改如下
>>    #ifndef WIN32

>>    #include  

>>    #endif

>3，修改port/port.h文件
>>    #elif defined(LEVELDB_PLATFORM_WINDOWS)  

>>    #  include "port/port_win.h"  
>>    

>4，修改port/port_win.h文件；将第四行的宏定义给注释掉
>>    #define snprintf _snprintf  // 注释掉此句    
    
>5，CMakeLists.txt放入levebdb目录下；修改其中boost路径；使用cmake工具；
>



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)