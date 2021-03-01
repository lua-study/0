#kuailexs_IDE

实现方式为将那些代码导入android 工程中，差什么类就补什么，没什么技术含量，单纯拼装。
若直接用编译了的jar包，会出现能编译不能运行的情况。

kuailexs_IDE/assets/classes.zip 文件需要构建   
dx --dex --output=classes.dex dx.jar ecj.jar sdklib.jar zipsigner2.jar spongycastle.jar javax.jar guava.jar
zip -r classes.zip classes.dex

包含以下项目代码：如有遗漏，还请谅解

sdklib.jar 22.1.3
ecj.jar 4.6
dx.jar 1.7
guava.jar  14.0.1

https://github.com/rtyley/spongycastle

https://code.google.com/archive/p/zip-signer

https://github.com/jackpal/Android-Terminal-Emulator

https://github.com/Trinea/android-common

aide_ndk

Android OpenSource android-utils （adb/acp/aidl/aapt/zipalign）

https://github.com/jecelyin/920-Text-Editor-old tag 12.11.23

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)