# z_netlib
1. 异步多线程网络架构
2. 对ATS底层机制的模仿和实现

# 安装
1. cmake
2. gcc/g++ version > 4.1

# 里程碑
1. 使用CMake进行代码管理并组织代码结构
2. 封装pthread函数库
3. 封装高精度的时间函数库
4. 封装GNU原子操作相关函数
5. 封装基于引用计数的智能指针Ptr
6. 抽象最基础最核心数据结构--延续性编程第一版
7. 封装ProxyMutex,并提供相关操作宏,封装范围锁和手动锁
8. 封装Action,安全回调Continuation.
9. 封装Event,用于事件系统安全执行Continuation.
10. 封装Thread类,用于实现事件池底层线程模型基类
11. 封装外部队列,优先级队列和负队列
12. 封装EThread库,并修改以前的测试案例
13. 实现R类型EThread处理任务的能力
14. 提炼Event,并将其独立出来
15. 使编译的可执行文件具备gdb调试的能力
16. 修改EThread D类型线程的初始化接口
17. 封装EventProcessor,此为事件系统的调度接口
18. bugfix:修复EThread::processor中上锁失败,重新调度时,时间计算出错问题.
19. 实现EThread保存线程私有数据的能力,并在EventProcessor中提供统一使用线程组私有数据空间的接口
20. 事件模型基本完成.
21. 给Event添加事件调度接口
22. 对Polling子系统进行封装
23. 实现网络线程组初始化
24. 将NetHandler作为事件投放到事件系统中,每个事件线程驱动各自的epoll_wait任务.
25. bugfix:修改I_Ptr中错误本应该释放tmp_ptr而释放了m_ptr导致的段错误.
26. 封装基于可伸缩的一写多读IO缓冲区
27. 封装安全操作的socket相关底层函数库
28. 封装IpEntry类
29. 将sockfd封装成UnixNetVConnect,以后的读写操作都是针对VC来实现
30. 实现将UnixNetVConnect通过EvenIO将自身的fd假如到对应epoll_fd的监控中
31. 初步设计NetHandler对epoll_wait结果集的处理方式
32. bugfix:修改偏移量为0为判断条件导致程序出现的段错误
33. 在事件系统的外部队列和NetHandler的外部队列都使用了阻塞队列,待修改为原子队列---->new feature
34. 修改BlockQueue,将底层queue修改为list.在关闭连接的时候需要从enable队列中移除对应的元素.
35. 将std::list进行简单封装为NonBlockList.
36. 在UniNetProcessor中提供使用EventIO和get_PollDescriptor的接口.
37. 封装NetState(用于记录当前VC上的读写事件及状态)和VIO(IO View用于获取当前IO的执行状态)
38. 在NetHandler中实现将UnixNetVC加入到各队列以及相关的处理操作.
39. 为UnixNetVConnect提供do_io_*以及reenable系列接口.
40. 修改IpEntry的初始化接口,并添加获取sockaddr的接口.
41. 封装Connection类,该类用于向Server发起连接和记录一个客户端.
42. 为Action提供虚函数的cancle接口,用于取消特殊的Action.
43. 封装AcceptOptions和NetOptions类,分别用于设置accept和connect过程中的一些属性
44. 封装Server类,该类继承自Connection类,用于接受一个连接并产生(加工)一个Connection类
45. 封装NetAcceptAdapter类,该类为accept适配器,共支持三种模式(多D线程工作模式, 单R线程周期工作模式, R线程组周期工作模式,现阶段仅支持模式1)
46. bugfix:修复:EventProcessor中错误使用snprint方法
47. 通过NetAcceptAdapter监听来自客户端的连接,为每个建立的连接创建UnixNetVConnection,然后将其调度到所属线程中.
48. 回调UnixNetVConnect的acceptEvent,使vc可以加入到所属线程的NetHandler的管理中.
49. 实现向Server端发起连接并将vc加入所属线程的NetHandler管理中.
50. 对UnixNetVConnect提供signal_update signal_done 以及 signal_error接口.
51. 为signal_update加入重入计数器,因为VC可能被异步关闭,如果这个VC当前正在被使用,则会导致程序出现错误.如果VC不允许异步关闭,但是VC上已经没有读写事件所驱动,那么将会导致文件描述符泄露.
52. 修改Connection::connect接口.程序通常期望先设置IpEntry,然后再执行connect操作,我们需要执行这种方式.
53. 完成NetHandler中对vc读写事件的处理,并封装process_ready_list函数来处理就绪队列.
54. 实现close_UnixNetVConnect,用来关闭UnixNetVConnect.
55. 为Connection提供close方法,用来关闭底层的sockfd
56. 修改VIO的init_reader和init_writer接口
57. 实现UnixNetVConnect的do_io系列接口和reenable接口
58. 封装底层操作函数read和readv
59. bugfix:修复错误使用ntodo类型,造成的整形溢出错误
60. 实现UnixNetVConnect读写数据的能力
61. bugfix:修改EventIO.modify接口中类型的问题
62. bugfix:修改在UnixNetVConnect的connectEvent中打开socket之后,将fd保存到UnixNetVConnect上.
63. 封装system resouse limit获取和设置的函数.
64. 为epoll_wait实现受控阻塞
65. bugfix:修复在ready list队列中同一个vc出现多次,并且在关闭时导致程序异常的bug. 限制:队列中的vc只允许出现一次
66. bugfix:修复Buffer水位限制错误使用read_alive导致block无法自动追加的问题
67. bugfix:修复在epoll_wait中time=0的判断条件错误导致CPU占用率过高的问题.


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)