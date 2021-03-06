# 不可错过的CMS学习笔记

#### 介绍
带着问题去学习一个东西，才会有目标感，我先把一直以来自己对CMS的一些疑惑罗列了下，希望这篇学习笔记能解决掉这些疑惑，希望也能对你有所帮助。

#### 说明
1.CMS出现的初衷、背景和目的？
2.CMS的适用场景？
3.CMS的trade-off是什么?优势、劣势和代价
4.CMS会回收哪个区域的对象？
5.CMS的GC Roots包括那些对象？
6.CMS的过程？
7.CMS和Full gc是不是一回事？
8.CMS何时触发？
9.CMS的日志如何分析？
10.CMS的调优如何做？
11.CMS扫描那些对象？
12.CMS和CMS collector的区别？
13.CMS的推荐参数设置？
为什么ParNew可以和CMS配合使用，而Parallel Scanvenge不可以？


#### 基础知识

1.CMS收集器：Mostly-Concurrent收集器，也称并发标记清除收集器（Concurrent Mark-Sweep GC，CMS收集器），它管理新生代的方式与Parallel收集器和Serial收集器相同，而在老年代则是尽可能得并发执行，每个垃圾收集器周期只有2次短停顿。

2、我之前对CMS的理解，以为它是针对老年代的收集器。今天查阅了《Java性能优化权威指南》和《Java性能权威指南》两本书，确认之前的理解是错误的。

3、CMS的初衷和目的：为了消除Throught收集器和Serial收集器在Full GC周期中的长时间停顿。

4、CMS的适用场景：如果你的应用需要更快的响应，不希望有长时间的停顿，同时你的CPU资源也比较丰富，就适合适用CMS收集器。


#### CMS的过程

CMS的正常过程

这里我们首先看下CMS并发收集周期正常完成的几个状态。
1、（STW）初始标记：这个阶段是标记从GcRoots直接可达的老年代对象、新生代引用的老年代对象，就是下图中灰色的点。这个过程是单线程的（JDK7之前单线程，JDK8之后并行，可以通过参数CMSParallelInitialMarkEnabled调整）。

2、并发标记：由上一个阶段标记过的对象，开始tracing过程，标记所有可达的对象，这个阶段垃圾回收线程和应用线程同时运行，如上图中的灰色的点。在并发标记过程中，应用线程还在跑，因此会导致有些对象会从新生代晋升到老年代、有些老年代的对象引用会被改变、有些对象会直接分配到老年代，这些受到影响的老年代对象所在的card会被标记为dirty，用于重新标记阶段扫描。这个阶段过程中，老年代对象的card被标记为dirty的可能原因，就是下图中绿色的线：

3、预清理：预清理，也是用于标记老年代存活的对象，目的是为了让重新标记阶段的STW尽可能短。这个阶段的目标是在并发标记阶段被应用线程影响到的老年代对象，包括：（1）老年代中card为dirty的对象；（2）幸存区(from和to)中引用的老年代对象。因此，这个阶段也需要扫描新生代+老年代。【PS：会不会扫描Eden区的对象，我看源代码猜测是没有，还需要继续求证】

4、可中断的预清理：这个阶段的目标跟“预清理”阶段相同，也是为了减轻重新标记阶段的工作量。可中断预清理的价值：在进入重新标记阶段之前尽量等到一个Minor GC，尽量缩短重新标记阶段的停顿时间。另外可中断预清理会在Eden达到50%的时候开始，这时候离下一次minor gc还有半程的时间，这个还有另一个意义，即避免短时间内连着的两个停顿

CMS的异常情况

上面描述的是CMS的并发周期正常完成的情况，但是还有几种CMS并发周期失败的情况：

1、并发模式失败（Concurrent mode failure）：CMS的目标就是在回收老年代对象的时候不要停止全部应用线程，在并发周期执行期间，用户的线程依然在运行，如果这时候如果应用线程向老年代请求分配的空间超过预留的空间（担保失败），就回触发concurrent mode failure，然后CMS的并发周期就会被一次Full GC代替——停止全部应用进行垃圾收集，并进行空间压缩。如果我们设置了UseCMSInitiatingOccupancyOnly和
CMSInitiatingOccupancyFraction参数，其中CMSInitiatingOccupancyFraction的值是70，那预留空间就是老年代的30%。

2、晋升失败：新生代做minor gc的时候，需要CMS的担保机制确认老年代是否有足够的空间容纳要晋升的对象，担保机制发现不够，则报concurrent mode failure，如果担保机制判断是够的，但是实际上由于碎片问题导致无法分配，就会报晋升失败。

3、永久代空间（或Java8的元空间）耗尽，默认情况下,CMS不会对永久代进行收集，一旦永久代空间耗尽，就回触发Full GC。

#### CMS的调优

针对永久代的调优
如果永久代需要垃圾回收（或元空间扩容），就会触发Full GC。默认情况下，CMS不会处理永久代中的垃圾，可以通过开启CMSPermGenSweepingEnabled配置来开启永久代中的垃圾回收，开启后会有一组后台线程针对永久代做收集，需要注意的是，触发永久代进行垃圾收集的指标跟触发老年代进行垃圾收集的指标是独立的，老年代的阈值可以通过CMSInitiatingPermOccupancyFraction参数设置，这个参数的默认值是80%。开启对永久代的垃圾收集只是其中的一步，还需要开启另一个参数——CMSClassUnloadingEnabled，使得在垃圾收集的时候可以卸载不用的类。

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)