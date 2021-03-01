#Boost4Android

##boost_1_55_0
1. sh booststrap.sh
2. cd tools/build/v2
3. edit user-config.jam
   

    import os ;  
       
    if [ os.name ] = CYGWIN || [ os.name ] = NT {  
    androidPlatform = windows-x86_64 ;  
    }  
    else if [ os.name ] = LINUX {  
    androidPlatform = linux-x86_64 ;  
    }  
    else if [ os.name ] = MACOSX {  
    androidPlatform = darwin-x86 ;  
    }  
       
    modules.poke : NO_BZIP2 : 1 ;  
    ANDROID_NDK = /home/lzl/android_sdk/android-ndk-r13b ;  
    using gcc : android4.9 : $(ANDROID_NDK)/toolchains/arm-linux-androideabi-4.9/prebuilt/$(androidPlatform)/bin/arm-linux-androideabi-g++ :  
     $(ANDROID_NDK)/toolchains/arm-linux-androideabi-4.9/prebuilt/$(androidPlatform)/bin/arm-linux-androideabi-ar  
     $(ANDROID_NDK)/toolchains/arm-linux-androideabi-4.9/prebuilt/$(androidPlatform)/bin/arm-linux-androideabi-ranlib  
     --sysroot=$(ANDROID_NDK)/platforms/android-9/arch-arm  
     -I$(ANDROID_NDK)/sources/cxx-stl/gnu-libstdc++/4.9/include  
     -I$(ANDROID_NDK)/sources/cxx-stl/gnu-libstdc++/4.9/libs/armeabi/include  
     -DNDEBUG  
     -D__GLIBC__  
     -DBOOST_FILESYSTEM_VERSION=3  
     -lstdc++  
     -lgnustl_shared  
     -mthumb  
     -fno-strict-aliasing  
     -std=gnu++11  
     -O2  ;   
4. cd ../../../ 
5.  ./b2 --without-mpi --without-serialization toolset=gcc-android4.9 link=shared runtime-link=shared target-os=linux --stagedir=android/shared

this will compile shared of boost libaray.

6. ./b2 --without-mpi --without-serialization toolset=gcc-android4.9 link=static runtime-link=static target-os=linux --stagedir=android/static

this will compile static of boost libaray.

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)