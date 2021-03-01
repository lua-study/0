# BlocklyPi beta

#### 项目介绍
本项目是一个基于Blockly的树莓派可视化编程软件,可以通过模块化编程操控树莓派的GPIO，基于Python和RPi.GPIO

#### 软件架构
基于HTML，Javascript的在线编辑器


#### 使用说明

见项目 `apps/blocklypi/index.html` 地址

更多说明详见Blockly


#### 实际使用
详见 [http://hgccloud.firadio.net/tools/blocklypi/apps/blocklypi/index.html](http://hgccloud.firadio.net/tools/blocklypi/apps/blocklypi/index.html)
![输入图片说明](https://gitee.com/uploads/images/2018/0617/192441_def2fff9_906045.png "index.png")

#### 特别说明
本版本为BlocklyPi beta版本，对第一代进行了重写，抛弃了Wiringpi而使用Python，功能相比于第一代更为强大，但是仍可能存在许多不足(可能在编写时没有发现)，如在使用过程中产生问题，请及时在issues中指出。

另外，原生Blocks编译为python_compressed.js(参见官方的Blockly源码)，树莓派的javascript在pt文件夹下。blocks和generators在同一文件中，以注释为定界符隔开。参考下图:

```
//xxx
Some code
包含Blockly.Blocks.xxx和Blockly.Python.xxx两个函数
//End.xxx
```
谢谢。


By 王逸伦&HGC

----
联系方式：
QQ：594352301

Mail：594352301@qq.com

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)