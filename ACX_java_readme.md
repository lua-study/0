> 小猿“思前享后”为大家分享优质内容！————Share猿

&emsp;&emsp;这个项目是一个jdk源码阅读的项目，在源码阅读过程中可以直接在源码中写自己的理解和想法和疑问提交到项目中让更多的人帮你解决问题，下一个朋友遇到相关问题就可以不用再去查资料问别人了。我们的目标是做一个深入java的指南,只有大家的力量才能让这个这个开源的文档更完美！同时针对每个模块我单独做了一个子项目，可以在里面添加相关练习和一些优秀的文章和书籍推荐。

## 1.项目结构

### [1.1.java-code（jdk1.8源码）](https://gitee.com/shareyuan/java/tree/master/java-code)

&emsp;&emsp;这是jdk1.8的项目源码，大家可以把项目clone下来在里面进行提问，注释等等操作，具体注释的格式我在**项目日常push**中有提及，请按格式进行push。
### [1.2.java-data](https://gitee.com/shareyuan/java/tree/master/java-data)
### [1.3.java-algorithm](https://gitee.com/shareyuan/java/tree/master/java-algorithm)
### [1.4.java-collection](https://gitee.com/shareyuan/java/tree/master/java-collection)
&emsp;&emsp;通常，我们的程序需要根据程序运行时才知道创建多少个对象。但若非程序运行，程序开发阶段，我们根本不知道到底需要多少个数量的对象，甚至不知道它的准确类型。为了满足这些常规的编程需要，我们要求能在任何时候，任何地点创建任意数量的对象，而这些对象用什么来容纳呢？我们首先想到了数组，但是数组只能放统一类型的数据，而且其长度是固定的，那怎么办呢？集合便应运而生了！
### [1.5.java-thread](https://gitee.com/shareyuan/java/tree/master/java-thread)
### [1.6.java-design](https://gitee.com/shareyuan/java/tree/master/java-design)
### [1.7.java-stream](https://gitee.com/shareyuan/java/tree/master/java-stream)




## 2.项目日常push规范

&emsp;&emsp;请大家严格按照注释标准来进行提问或者注释，这样可以让我们养成很好的代码开发习惯，能严格安装标准编写一方面方便其他人阅读代码，另一方面可以展现出你的功底。

### 2.1.源码中类的注释规范示例
```
import java.nio.charset.Charset;
import java.nio.file.Files;
import java.nio.file.Path;
import java.util.Arrays;
import java.util.Collection;
import java.util.Comparator;
import java.util.Iterator;
import java.util.Objects;
import java.util.Optional;
import java.util.Spliterator;
import java.util.Spliterators;
import java.util.concurrent.ConcurrentHashMap;
import java.util.function.BiConsumer;
import java.util.function.BiFunction;
import java.util.function.BinaryOperator;
import java.util.function.Consumer;
import java.util.function.Function;
import java.util.function.IntFunction;
import java.util.function.Predicate;
import java.util.function.Supplier;
import java.util.function.ToDoubleFunction;
import java.util.function.ToIntFunction;
import java.util.function.ToLongFunction;
import java.util.function.UnaryOperator;

/**
 * A sequence of elements supporting sequential and parallel aggregate
 * operations.  The following example illustrates an aggregate operation using
 * {@link Stream} and {@link IntStream}:
 *
 *  {@code
 *     int sum = widgets.stream()
 *                      .filter(w -> w.getColor() == RED)
 *                      .mapToInt(w -> w.getWeight())
 *                      .sum();
 * } 
 *
 * In this example, {@code widgets} is a {@code Collection }.  We create
 * a stream of {@code Widget} objects via {@link Collection#stream Collection.stream()},
 * filter it to produce a stream containing only the red widgets, and then
 * transform it into a stream of {@code int} values representing the weight of
 * each red widget. Then this stream is summed to produce a total weight.
 *
 *  In addition to {@code Stream}, which is a stream of object references,
 * there are primitive specializations for {@link IntStream}, {@link LongStream},
 * and {@link DoubleStream}, all of which are referred to as "streams" and
 * conform to the characteristics and restrictions described here.
 *
 *  To perform a computation, stream
 *  operations  are composed into a
 *  stream pipeline .  A stream pipeline consists of a source (which
 * might be an array, a collection, a generator function, an I/O channel,
 * etc), zero or more  intermediate operations  (which transform a
 * stream into another stream, such as {@link Stream#filter(Predicate)}), and a
 *  terminal operation  (which produces a result or side-effect, such
 * as {@link Stream#count()} or {@link Stream#forEach(Consumer)}).
 * Streams are lazy; computation on the source data is only performed when the
 * terminal operation is initiated, and source elements are consumed only
 * as needed.
 *
 *  Collections and streams, while bearing some superficial similarities,
 * have different goals.  Collections are primarily concerned with the efficient
 * management of, and access to, their elements.  By contrast, streams do not
 * provide a means to directly access or manipulate their elements, and are
 * instead concerned with declaratively describing their source and the
 * computational operations which will be performed in aggregate on that source.
 * However, if the provided stream operations do not offer the desired
 * functionality, the {@link #iterator()} and {@link #spliterator()} operations
 * can be used to perform a controlled traversal.
 *
 *  A stream pipeline, like the "widgets" example above, can be viewed as
 * a  query  on the stream source.  Unless the source was explicitly
 * designed for concurrent modification (such as a {@link ConcurrentHashMap}),
 * unpredictable or erroneous behavior may result from modifying the stream
 * source while it is being queried.
 *
 *  Most stream operations accept parameters that describe user-specified
 * behavior, such as the lambda expression {@code w -> w.getWeight()} passed to
 * {@code mapToInt} in the example above.  To preserve correct behavior,
 * these  behavioral parameters :
 *  
 *  must be  non-interfering 
 * (they do not modify the stream source); and 
 *  in most cases must be  stateless 
 * (their result should not depend on any state that might change during execution
 * of the stream pipeline). 
 *  
 *
 *  Such parameters are always instances of a
 *  functional interface  such
 * as {@link java.util.function.Function}, and are often lambda expressions or
 * method references.  Unless otherwise specified these parameters must be
 *  non-null .
 *
 *  A stream should be operated on (invoking an intermediate or terminal stream
 * operation) only once.  This rules out, for example, "forked" streams, where
 * the same source feeds two or more pipelines, or multiple traversals of the
 * same stream.  A stream implementation may throw {@link IllegalStateException}
 * if it detects that the stream is being reused. However, since some stream
 * operations may return their receiver rather than a new stream object, it may
 * not be possible to detect reuse in all cases.
 *
 *  Streams have a {@link #close()} method and implement {@link AutoCloseable},
 * but nearly all stream instances do not actually need to be closed after use.
 * Generally, only streams whose source is an IO channel (such as those returned
 * by {@link Files#lines(Path, Charset)}) will require closing.  Most streams
 * are backed by collections, arrays, or generating functions, which require no
 * special resource management.  (If a stream does require closing, it can be
 * declared as a resource in a {@code try}-with-resources statement.)
 *
 *  Stream pipelines may execute either sequentially or in
 *  parallel .  This
 * execution mode is a property of the stream.  Streams are created
 * with an initial choice of sequential or parallel execution.  (For example,
 * {@link Collection#stream() Collection.stream()} creates a sequential stream,
 * and {@link Collection#parallelStream() Collection.parallelStream()} creates
 * a parallel one.)  This choice of execution mode may be modified by the
 * {@link #sequential()} or {@link #parallel()} methods, and may be queried with
 * the {@link #isParallel()} method.
 *
 * @param   the type of the stream elements
 * @since 1.8
 * @see IntStream
 * @see LongStream
 * @see DoubleStream
 * @see  java.util.stream 
 * 
 * 作用：
 * 	①Stream 是对集合（Collection）对象功能的增强。
 * 	②专注于对集合对象进行各种非常便利、高效的聚合操作
 * 	③大批量数据操作。
 * 	④Stream API 借助于同样新出现的 Lambda 表达式，极大的提高编程效率和程序可读性。
 * 疑问：
 * 	①什么是聚合操作？？？
 * 	回答：请到https://www.ibm.com/developerworks/cn/java/j-lo-java8streamapi/查看。
 * 	②什么是流？？？
 * 	回答：Stream 就如同一个迭代器（Iterator），单向，不可往复，数据只能遍历一次，遍历过一次后即用尽了，就好比流水从面前流过，一去不复返。（总结：https://www.ibm.com/developerworks/cn/java/j-lo-java8streamapi/）
 * 应用：
 * 	①用Lambda遍历
 * 	②
 * 	③
 */
public interface Stream  extends BaseStream > {

}
```
### 2.2.源码中方法的注释规范示例

```
    /**
     * Returns a stream consisting of the results of applying the given
     * function to the elements of this stream.
     *
     *  This is an  intermediate
     * operation .
     *
     * @param   The element type of the new stream
     * @param mapper a  non-interfering ,
     *                stateless 
     *               function to apply to each element
     * @return the new stream
     * 
     * 作用：
     * 疑问：
     *	①这里有一个疑问，map方法有两个参数，但是传值为什么是一个字符串？
     *	回答：
     *	②
     * 场景：
     * 	①
     * 	②
     * 	③
     * 优点：
     * 缺点：
     */
      Stream  map(Function  mapper);
```

## 3.优质java资源汇总
### 3.1.java基础
### 3.2.java思想
### 3.3.java应用
### 3.4.java轮子
### 3.5.java架构
&emsp;&emsp;【1】[后端架构师技术图谱·xingshaocheng](https://github.com/xingshaocheng/architect-awesome/blob/master/README.md#java%E4%B8%AD%E7%9A%84%E9%94%81%E5%92%8C%E5%90%8C%E6%AD%A5%E7%B1%BB)




---

**扫描以下公众号关注Share猿↓↓↓↓↓↓↓↓获取社区管理微信拉你入“jdk源码阅读群”群**

![](http://upload-images.jianshu.io/upload_images/3084894-e6e9a10cf3e08bba?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240 "")

更多资讯请在**简书、微博、今日头条、掘金、CSDN**都可以通过搜索“Share猿”找到哦！！！

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)