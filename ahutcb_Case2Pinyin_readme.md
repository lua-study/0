## Case2Pinyin是一个可以将中文字符转换成为拼音的开源工具

这解决了我们很多填充内容时可以自动填写的操作.

例如, 根据城市拼音搜索, 根据姓名拼音搜索等等.

### 运行前应该首先进入lib目录将Maven仓库中没有的sparta库加入Maven中央仓库

`
    mvn install:install-file -Dfile=sparta.jar -Dpackaging=jar -DgroupId=com.hp.hpl -DartifactId=sparta -Dversion=1.0

    mvn install:install-file -Dfile=sparta-sax.jar -Dpackaging=jar -DgroupId=com.hp.hpl -DartifactId=sparta-sax -Dversion=1.0

`

接下来我们就可以进入Main方法进行测试

`
String cnStr = "单元测试";
System.out.println(CN2SpellUtils.cn2FirstSpell(cnStr));
System.out.println(CN2SpellUtils.cn2Spell(cnStr));
System.out.print(CN2SpellUtils.cn2ASCII(cnStr));

=========Print==========

DYCS
danyuanceshi
e58d95e58583e6b58be8af95


`



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)