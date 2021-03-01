该仓库为阅读Redis 5.0.3源码并添加注释用以云备份。

## 基础数据结构
- sds C样式的动态字符串封装
- adlist 双向链表
- dict 字典（由hash表实现）
    - dictScan操作中的反转二进制算法，可以提供一种`极为均衡`的遍历方式
- intset 整数集合
- ziplist 由数组封装的抽象数据结构，一个压缩list
- listpack [详细说明](https://github.com/antirez/listpack/blob/master/listpack.md) 由数组封装的抽象数据结构，ziplist的改良版
- quicklist 由双向链表与ziplist组合抽象出的数据结构，ziplist做为节点中存储数据的区域
- zipmap 由数组封装的抽象数据结构，内部采用key-value的形式存储
- zskiplist 跳表，由单向链表封装的抽象数据结构，对每个节点均加入一个`跳跃表（数组）`的内存空间进而使得所有操作表现良好；以空间换时间的经典实现，良好的处理节点上限一般为2^64个
- raxTree 由数据封装的抽象数据结构，一个基数树；与普通基数树不同的是合并不具有值的节点
---
## 数据结构示意图
![srs C样式的动态字符串封装 1](https://images.gitee.com/uploads/images/2019/0915/135622_f3044bf7_692806.jpeg "幻灯片2.jpeg")
![srs C样式的动态字符串封装 2](https://images.gitee.com/uploads/images/2019/0915/135656_27f903e0_692806.jpeg "幻灯片3.jpeg")
![srs C样式的动态字符串封装 3](https://images.gitee.com/uploads/images/2019/0915/135722_16fdcad1_692806.jpeg "幻灯片4.jpeg")
![srs C样式的动态字符串封装 4](https://images.gitee.com/uploads/images/2019/0915/135745_375da9d2_692806.jpeg "幻灯片5.jpeg")
![adlist 双向链表](https://images.gitee.com/uploads/images/2019/0915/135806_d123adb2_692806.jpeg "幻灯片6.jpeg")
![intset 整数集合 1](https://images.gitee.com/uploads/images/2019/0915/135901_a9b6160c_692806.jpeg "幻灯片9.jpeg")
![intset 整数集合 2](https://images.gitee.com/uploads/images/2019/0915/135923_45124302_692806.jpeg "幻灯片10.jpeg")
![ziplist 一个压缩list 1](https://images.gitee.com/uploads/images/2019/0915/135941_ef3bd5a5_692806.jpeg "幻灯片11.jpeg")
![ziplist 一个压缩list 2](https://images.gitee.com/uploads/images/2019/0915/140002_379a1738_692806.jpeg "幻灯片12.jpeg")
![ziplist 一个压缩list 3](https://images.gitee.com/uploads/images/2019/0915/140022_0c08fd1c_692806.jpeg "幻灯片13.jpeg")
![listpack ziplist的改良版](https://images.gitee.com/uploads/images/2019/0915/140034_4726a4d6_692806.jpeg "幻灯片14.jpeg")
![quicklist 双向链表与ziplist组合](https://images.gitee.com/uploads/images/2019/0915/140123_135e610b_692806.jpeg "幻灯片15.jpeg")
![zipmap 数组key-value的形式存储](https://images.gitee.com/uploads/images/2019/0915/140200_522ef436_692806.jpeg "幻灯片16.jpeg")
![zskiplist 跳表](https://images.gitee.com/uploads/images/2019/0915/140230_1885cd06_692806.jpeg "幻灯片17.jpeg")
![raxTree 基数树 1](https://images.gitee.com/uploads/images/2019/0915/140254_f1a528ec_692806.jpeg "幻灯片18.jpeg")
![raxTree 基数树 2](https://images.gitee.com/uploads/images/2019/0915/140338_d6c0aaf3_692806.jpeg "幻灯片19.jpeg")
![raxTree 基数树 3](https://images.gitee.com/uploads/images/2019/0915/140359_f5d62d2d_692806.jpeg "幻灯片20.jpeg")
![raxTree 基数树 4](https://images.gitee.com/uploads/images/2019/0915/140416_8a7f258d_692806.jpeg "幻灯片21.jpeg")

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)