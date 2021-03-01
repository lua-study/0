# xmem
一个C语言的轻量级动态内存管理组件，提高了RAM的使用效率。xmem支持动态内存分配与回收，内存碎片整理功能。xmem的设计支持Debug模式与Release模式；开发阶段使用Debug模式可以对内存写越界进行检测，通过将越界处内存信息dump告知开发人员何处内存写越界；在Release模式内存块管理头与内存块采用相向生长模式，避免因内存写越界，内存块管理头信息出错而导致整个程序崩溃的问题。xmem只需要很小的代码开销，极少的配置，就能轻松实现动态内存管理的功能，使用极其方便。

Ultralightweight dynamic memory allocation in C.

## License

Apache License

1.xmem support 2 growing method.
	a.)header and memory block are grow by opposite direction.
	-------------------------------------------------------------------------------
	| Header List|  xMemHdrEnd--->|  ...   |  |
	|       |header|  mem  |header|  mem  |header|  mem  |       |
	--------------------------------------------------------------
2. The super block is a block that include some smaller memory blocks, to reduce memory spend on header.	
3. Set the Macro CPU_64_BIT to 1 if your CPU is 64bits. 
4. Implement the macro SYS_ENTER_CRITICAL_SECTION and SYS_SYS_CRITICAL_SECTION according to you system, to asure xmalloc and xfree are safe. 
   Make sure no interruptions occur during xmalloc or xfree are executing, otherise might cause the header link be broke.

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)