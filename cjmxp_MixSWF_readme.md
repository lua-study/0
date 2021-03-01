#MixSWF

swf混淆工具，用于混淆FD/FB工程打包的swf文件，可智能提取项目中的包名、类名和类成员名等，并可以减少swf文件体积。bin目录下的MixSWF.swf已经进行了混淆处理，可以使用JPEXS Free Flash Decompiler等反编译工具查看混淆效果。修改bat/SetupSDK.bat里的FLEX_SDK字段指向你自己的flexSDK，运行Run.bat即可使用。或者运行FD工程重新编译。

##使用方法

- 打开FD工程并编译运行MixSWF，会出现绿色和蓝色的两个圆角矩形
- 把装有项目源码的src文件夹拖到右边的圆角矩形里，MixSWF会提取源码中的包名、类名及类成员名覆盖到mixs.txt文件
- 把使用release发布的swf文件拖到左边的圆角矩形里，swf同级目录上多出的*_mix.swf文件即是经过混淆的文件

##文件说明

- mixs.txt 配置需要混淆的字符，使用英文字符","分隔字段，由MixSWF自动生成
- nomixs.txt 配置不需要混淆的字符，使mixs.txt失效，格式跟mixs.txt一致
- *_table.txt 混淆后出现在swf同级目录，列出混淆前后的字段，用于对照
- *_min.swf 这个你懂的

##实现原理

swf把所有使用到的类名、方法名和字符串等都存储到一个叫常量池的区域，MixSWF的工作就是根据swf的文件格式找到这个区域，并把里面的字符串都替换成简短的字符组合，然后重新包装成一个新的swf

##注意事项

- 不能混淆主文档类名，例如Main，因为MixSWF没有处理标明swf入口的Tag
- 不能混淆主文档的包名，如果主文档包含在其他包内，请把包名填入nomixs.txt，例如plat.Main，则需要把plat填入nomixs.txt
- 不能混淆使用debug发布的swf，因为debug版里有多个doABCTag，而MixSWF只处理第一个
- 不能混淆关键字以及和flash内置类一致的类名、方法名和变量名等，例如is,Sprite,x,y,width,height,parent等，如果你的项目中存在这样的自定义类或方法，请配置nomixs.txt不对其进行混淆
- 如果你的项目混淆后不能正常运行，请修改MixData类里的CHAR_SET为`_abcde`等编译器能识别的字符集，重新混淆后使用JPEXS Free Flash Decompiler或其他反编译工具提取源码，使用混淆过的代码搭建新的工程，然后进行调试。一般都是混淆了内置关键词造成的，使用*_table.txt定位。

##参考

- `avm2overview.pdf`
- `swf_file_format_spec_v10.pdf`
- [SWFWireDecompiler](https://github.com/magicalhobo/SWFWire/tree/master/SWFWireDecompiler)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)