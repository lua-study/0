#VGraphicEngine
用软件实现方式模拟OpenGL可编程管线;
设备层分离在:vg::fw中,目前提供window平台支持;
渲染层分离在vg::sr;可编程部分在vg::sl中;
数学工具由两部分vg::core以及外部库glm;
vg::core中还包含几个内存分配器;
目前进度为:可以完成一个纹理模型的渲染(光照也可--有BUG,无明暗变化)VS,FS基本功能实现.GS暂时固定.
后续方向:重构sl,vr部分.修复BUG;
光栅化部分及FS部分采用更高效的实现方式.....

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)