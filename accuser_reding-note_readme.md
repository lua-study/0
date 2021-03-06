#reding-note
读书笔记，开卷有益
内容来源：http://techshow.ctrip.com/archives/784.html
                                             **为什么要在服务层设计读写分离** 
我的架构师同事问我：“为什么你总说要在服务层实现读写分离，我们已经在数据库实现了读写分离，是不是已经够用”。以下是我的解释，

在做网站性能优化的时候，我常常忘记还有数据库读写分离这件事，因为数据库读写分离，对性能带来的提高太有限了，实际上，就是一倍（一台服务器变成两台服务器）。当你的网站业务发展，如果从无到有地使用数据库读写分离，提高了一倍的服务能力，你很快就需要想新的优化方案。实际上，数据库的读写分离，更像是数据安全的一个副产品，用一台数据库服务器不安全（怕数据丢失），用一台服务器作为备份，既然有了两台服务器，就充分利用吧，于是有了“读写分离”，提高一倍也是好的。


于是，能够十倍百倍提高性能的方案出现了，缓存加服务器集群，这是最常用且有效的提高网站访问量的设计。使用共享缓存（memcached，redis）可以获得十到几十倍的性能提升，使用进程内缓存，可以得到百倍的性能提升；集群中增加一倍的服务器，可以增加一倍的计算能力，服务更多的并发请求。等一下，上面所说的方案，其实只对“读”操作才有效，对“写”操作可以说是毫无用处。

那么有什么办法可以提高“写”操作的性能，在架构部署的设计方面，我的答案是，“没有”。

从硬件入手，可以使用SSD硬盘。愿意替换底层数据库，可以使用hbase或者cassandra，都不在今天讨论的范围。我想说的是，既然使用缓存和增加服务器，对于“写”操作没有优化作用，在一开始，“写”操作相关的服务，就不该和“读”操作一起，被分配到数量庞大的计算机集群里。

想象这样的架构设计，我有一个“读”服务的集群，一共4台服务器，我有一台“写”服务器（另一台备用，故障时切换）。当我的网站访问量上升，我增加“读”服务器集群到8台，简单就能应付问题。因为“读”服务是状态无关的，增加到100台也不会带来错误的数据，这是一个重要的思想，状态无关的服务，才可以放心地水平扩展，事实上，状态无关的服务，通常只有“读”服务。

那么当“写”服务撑不住的时候，怎么办，嗯。。。总会有办法，反正不是加缓存或者是使用集群，这个可以做架构师面试题。

然后我解释一下为什么不该在集群里面运行“写”服务，我把“写”服务分为两种。

1. 和“状态”（可能发生冲突的情形）弱相关，比如用户提供内容（UGC）的操作，每个用户提交自己的评论，或者发布自己的微博，不太容易发生冲突。对于这类“写”服务，部署在集群里面勉强可行，虽然没带来什么好处，但也没有引入错误

2. 和“状态”（可能发生冲突的情形）强相关，比如包含库存操作的电商网站，上千人“秒杀”热门商品，允许这样的操作在集群内并发，是架构师自己作死的节奏啊

明白了这个道理，你就知道我之前为什么说是“一台”写服务器，只有一台服务器，才可以保证在“秒杀”场景下，不会在没有库存的情况下继续售卖成功。

细心的读者（嗯，就是你）会继续追问，在一台服务器的情况下，现在都是多核并发编程，保证串行操作也不是容易的事啊。问得太好了，我这大半年写的系列文章，都是为了解决这个问题，你需要的是actor模型。异步编程加上进程内的消息队列，可以高效地对并发操作进行串行的处理。

结论，使用服务器集群提高性能只对“读”服务有效，对“写”服务无效，“写”服务器应该使用主/从模式，同一时间只使用一台服务器。在“写”服务器内部，使用支持actor模型的编程语言，保证关键操作的串行。最后老生常谈，支持actor模型的编程语言是：Erlang，Go，Scala，F#

====================================================================================
内容来源：http://techshow.ctrip.com/archives/788.html
                                         **zookeeper在分布式应用中的作用** 
是不是要在标题的“作用”之前加上“重要”两个字，我犹豫了一下，zookeeper提供的功能是如此的重要，以至于如果你在应用中不使用它，早晚也会在你的应用中去实现zookeeper 的功能，所以，zookeeper值得你花（一点）时间去掌握。

zookeeper是为了“分布式”而诞生的，我反复在说“分布式”，并不是赶潮流，而是被潮流推着向前。在任何互联网生产应用中，哪怕你的公司规模小，访问量用一台服务器足够应付，仍然不能容忍当服务器故障时，没有备用的服务器可切换，这个称为“防止单点故障”，因为你至少要用两台服务器来防止单点故障，所以你已经在“分布式”的服务环境里。

我们来回顾上一篇提到的“为什么要在服务层设计读写分离”，我把应用层的通用服务分为“读”服务和“写”服务，“读”服务用集群来实现高可用高性能，而“写”服务用单台服务器来保证事务顺序执行。

那么，“单台服务器”听上去好危险的样子，于是今天的主角登场，我们需要zookeeper。

你也许听到过，这种应用场景叫做master/slave，或者我更喜欢称为主/备模式，在这种场景下，我有两台服务器（主和备），任何情况下，只有“主”在工作，“备”是在主出现故障时，接替“主”来提供服务。在zookeeper的支持下，这一过程是这样实现的，
Zookeeper提供目录和节点的服务，当我的两台服务器启动时，会在zookeeper的指定目录下创建对应自己的临时节点（这个过程称为“注册”），所谓临时节点，是靠心跳（定时向zookeeper服务器发送数据包）维系，当服务器出现故障（无法向zookeeper服务器发送数据包），zookeeper会删除临时节点。服务器向zookeeper注册时，zookeeper会分配序列号，我们认为序列号小的那个，就是“主”，序列号大的那个，就是“备”。

当我们的客户端（通常是web server）需要访问“写”服务时，需要连接zookeeper，获得指定目录下的临时节点列表，也就是已经注册的服务器信息，获得序列号小的那台“主”服务器的地址，进行后续的访问操作。以达到“总是访问主服务器”的目的。

当“主”服务器发生故障，zookeeper从指定目录下删除对应的临时节点，同时可以通知关心这一变化的所有客户端，高效且迅速的传播这一信息，你想一想，如果不是使用zookeeper，要自己实现这个功能，可没。。。那么简单（不许唱！）

我们为了消除单点故障而使用的主/备模式依赖zookeeper，那么zookeeper可不能有单点故障，所以zookeeper在诞生的时候，就是用集群的模式工作，用多台服务器来消除自身的单点故障隐患，怎么样，无可挑剔吧。

总结，在多核并行计算模式下，我认定基于消息传递的actor模型（源自erlang）是正确的编程方式，在actor模型下，可以简单实现基于服务层的串行操作，保证“写”操作的完整和一致。使用actor模型，需要用主/备的部署架构来消除单点故障，实现主/备的部署架构，最简单可靠的方法是使用zookeeper。所以我现在的软件架构是这么推导出来的高并发需求 -> 异步计算 (使用actor model) -> master/slave (使用zookeeper)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)