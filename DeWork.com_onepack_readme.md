## onepack v1.0.2
onepack是一个加固+多渠道一键打包的工具, 避免再次手动操作. 在后续的版本会增加gradle plugin的方式一键打包

## use onepack
1. 需要配置: APK_SIGNER_JAR_DIR环境变量, 路径为: Your_SDK_PATH\build-tools\27.0.3\lib\apksigner.jar
2. 在path中配置 Your_SDK_PATH\build-tools\27.0.3\
3. 命令说明:
   
命令 | 说明
---|---
-s | 签名配置文件
-c | 渠道配置文件, 只加固签名
-onlyPackChannel | 对已有加固包写渠道
-onlySign | 只签名apk,不加固


> 命令行方式使用可以不指定outdir, 默认会使用apk所在目录; jar引用的方式,需要指定outdir
1. 你可以以jar包的方式引入到你的工程
```
        OnePack onePack = new OnePack();
        onePack.setChannelConfig(channelConfig); //设置channel config
        onePack.setSignConfig(signConfig);   //设置sign config
        onePack.setOutDir(new File(outDir));  //设置输出目录
        onePack.setOriginApkFile(new File(apkName)); //设置原始apk文件
        onePack.start();
```
2. 你也可以在命令行使用(签名和渠道配置的文件名不限制, [onepack.jar](https://github.com/xiexiang89/onepack/blob/master/jar/onepack/onepack.jar))
```
java -jar onepack.jar my.apk -s sign.config -c channel.config -o outdir
```
- channel.config配置如下
```
keyName=channel_id
channel=baidu;huawei
```
- sign.config配置如下
```
storeFile=
storePassword=
keyAlias=
keyPassword=
```
- 批处理方式([onepack.7zip](https://github.com/xiexiang89/onepack/blob/master/bat/onepack.7z))

请在sign.config 和 channel.config配置好信息
```
onepack.bat my.apk
```
## third party libraries
1. 解包和打包 apktool_2.4.0
2. 加固ms-shield-1.0.3.jar [查看](https://cloud.tencent.com/developer/article/1193406)
3. AndroidSdk zipalign and apksigner


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)