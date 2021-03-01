#Rxjava-sample  Rxjava使用例子
使用场景 http://m.blog.csdn.net/u012124438/article/details/53730717

###RxJava 到底是什么

一个词：`异步`。  
RxJava 在 GitHub 主页上的自我介绍是 "a library for composing asynchronous and event-based programs using observable sequences for the Java VM"（一个在 Java VM 上使用可观测的序列来组成异步的、基于事件的程序的库）。这就是 RxJava ，概括得非常精准。

    然而，对于初学者来说，这太难看懂了。因为它是一个『总结』，而初学者更需要一个『引言』。
    其实， RxJava 的本质可以压缩为异步这一个词。说到根上，它就是一个实现异步操作的库，而别的定语都是基于这之上的。

###RxJava 好在哪

一个词：`简洁`。  
异步操作很关键的一点是程序的简洁性，因为在调度过程比较复杂的情况下，异步代码经常会既难写也难被读懂。 Android 创造的 AsyncTask 和Handler ，其实都是为了让异步代码更加简洁。RxJava 的优势也是简洁，但它的简洁的与众不同之处在于，随着程序逻辑变得越来越复杂，它依然能够保持简洁。

####举个例子

    假设有这样一个需求：界面上有一个自定义的视图 imageCollectorView ，它的作用是显示多张图片，并能使用 addImage(Bitmap)
    方法来任意增加显示的图片。现在需要程序将一个给出的目录数组 File[] folders 中每个目录下的 png 图片都加载出来并显示在
    imageCollectorView 中。需要注意的是，由于读取图片的这一过程较为耗时，需要放在后台执行，而图片的显示则必须在 UI 线程执行。

####Java 实现方式：
![mahua](screenshots/image01.png)

####RxJava 实现方式：
![mahua](screenshots/image02.png)

观察一下你会发现， RxJava 的这个实现，是一条从上到下的链式调用，没有任何嵌套，这在逻辑的简洁性上是具有优势的。当需求变得复杂时，这种优势将更加明显（试想如果还要求只选取前 10 张图片，常规方式要怎么办？如果有更多这样那样的要求呢？再试想，在这一大堆需求实现完两个月之后需要改功能，当你翻回这里看到自己当初写下的那一片迷之缩进，你能保证自己将迅速看懂，而不是对着代码重新捋一遍思路？）。
###API 介绍和原理简析
####1.概念：扩展的观察者模式
RxJava 的异步实现，是通过一种扩展的观察者模式来实现的。

观察者模式

先简述一下观察者模式，已经熟悉的可以跳过这一段。
观察者模式面向的需求是：A 对象（观察者）对 B 对象（被观察者）的某种变化高度敏感，需要在 B 变化的一瞬间做出反应。举个例子，新闻里喜闻乐见的警察抓小偷，警察需要在小偷伸手作案的时候实施抓捕。在这个例子里，警察是观察者，小偷是被观察者，警察需要时刻盯着小偷的一举一动，才能保证不会漏过任何瞬间。程序的观察者模式和这种真正的『观察』略有不同，观察者不需要时刻盯着被观察者（例如 A 不需要每过 2ms 就检查一次 B 的状态），而是采用**注册**(Register)**或者称为订阅**(Subscribe)的方式，告诉被观察者：我需要你的某某状态，你要在它变化的时候通知我。 Android 开发中一个比较典型的例子是点击监听器 OnClickListener 。对设置 OnClickListener 来说， View 是被观察者， OnClickListener 是观察者，二者通过 setOnClickListener() 方法达成订阅关系。订阅之后用户点击按钮的瞬间，Android Framework 就会将点击事件发送给已经注册的 OnClickListener 。采取这样被动的观察方式，既省去了反复检索状态的资源消耗，也能够得到最高的反馈速度。当然，这也得益于我们可以随意定制自己程序中的观察者和被观察者，而警察叔叔明显无法要求小偷『你在作案的时候务必通知我』。
OnClickListener 的模式大致如下图：

![mahua](screenshots/image03.jpg)

如图所示，通过 setOnClickListener() 方法，Button 持有 OnClickListener 的引用（这一过程没有在图上画出）；当用户点击时，Button 自动调用 OnClickListener 的 onClick() 方法。另外，如果把这张图中的概念抽象出来（Button -> 被观察者、OnClickListener -> 观察者、setOnClickListener() -> 订阅，onClick() -> 事件），就由专用的观察者模式（例如只用于监听控件点击）转变成了通用的观察者模式。如下图：

![mahua](screenshots/image04.jpg)

而 RxJava 作为一个工具库，使用的就是通用形式的观察者模式。

RxJava 的观察者模式

RxJava 有四个基本概念：Observable (可观察者，即被观察者)、 Observer (观察者)、 subscribe (订阅)、事件。Observable 和 Observer 通过 subscribe() 方法实现订阅关系，从而 Observable 可以在需要的时候发出事件来通知 Observer。

与传统观察者模式不同， RxJava 的事件回调方法除了普通事件 onNext() （相当于 onClick() / onEvent()）之外，还定义了两个特殊的事件：onCompleted() 和 onError()。

onCompleted(): 事件队列完结。RxJava 不仅把每个事件单独处理，还会把它们看做一个队列。RxJava 规定，当不会再有新的 onNext() 发出时，需要触发 onCompleted() 方法作为标志。
onError(): 事件队列异常。在事件处理过程中出异常时，onError() 会被触发，同时队列自动终止，不允许再有事件发出。
在一个正确运行的事件序列中, onCompleted() 和 onError() 有且只有一个，并且是事件序列中的最后一个。需要注意的是，onCompleted() 和 onError() 二者也是互斥的，即在队列中调用了其中一个，就不应该再调用另一个。
RxJava 的观察者模式大致如下图：

![mahua](screenshots/image05.jpg)
####2.RxJava 基本使用
#####1）Observable 、 Observer、subscribe三种之间的关系
今天我用两根水管代替观察者和被观察者, 试图用通俗易懂的话把它们的关系解释清楚, 在这里我将从事件流这个角度来说明RxJava的基本工作原理。

先假设有两根水管：
![mahua](screenshots/image12.png)
上面一根水管为事件产生的水管，叫它`上游`吧，下面一根水管为事件接收的水管叫它`下游`吧。

两根水管通过一定的方式连接起来，使得`上游`每产生一个事件，`下游`就能收到该事件。
这里的`上游`和`下游`就分别对应着RxJava中的`Observable`和`Observer`，它们之间的连接就对应着`subscribe()`，因此这个关系用RxJava来表示就是：
```java
        //创建一个上游 Observable：
        Observable  observable = Observable.create(new ObservableOnSubscribe () {
            @Override
            public void subscribe(ObservableEmitter  emitter) throws Exception {
                emitter.onNext(1);
                emitter.onNext(2);
                emitter.onNext(3);
                emitter.onComplete();
            }
        });
        //创建一个下游 Observer
        Observer  observer = new Observer () {
            @Override
            public void onSubscribe(Disposable d) {
                Log.d(TAG, "subscribe");
            }

            @Override
            public void onNext(Integer value) {
                Log.d(TAG, "" + value);
            }

            @Override
            public void onError(Throwable e) {
                Log.d(TAG, "error");
            }

            @Override
            public void onComplete() {
                Log.d(TAG, "complete");
            }
        };
        //建立连接
        observable.subscribe(observer);
```

这个运行的结果就是:

```java
12-02 03:37:17.818 4166-4166/zlc.season.rxjava2demo D/TAG: subscribe
12-02 03:37:17.819 4166-4166/zlc.season.rxjava2demo D/TAG: 1
12-02 03:37:17.819 4166-4166/zlc.season.rxjava2demo D/TAG: 2
12-02 03:37:17.819 4166-4166/zlc.season.rxjava2demo D/TAG: 3
12-02 03:37:17.819 4166-4166/zlc.season.rxjava2demo D/TAG: complete
```
`注意`: 只有当上游和下游建立连接之后, 上游才会开始发送事件. 也就是调用了`subscribe()` 方法之后才开始发送事件.

把这段代码连起来写就成了RxJava引以为傲的链式操作：

```java
  Observable.create(new ObservableOnSubscribe () {
            @Override
            public void subscribe(ObservableEmitter  emitter) throws Exception {
                emitter.onNext(1);
                emitter.onNext(2);
                emitter.onNext(3);
                emitter.onComplete();
            }
        }).subscribe(new Observer () {
            @Override
            public void onSubscribe(Disposable d) {
                Log.d(TAG, "subscribe");
            }

            @Override
            public void onNext(Integer value) {
                Log.d(TAG, "" + value);
            }

            @Override
            public void onError(Throwable e) {
                Log.d(TAG, "error");
            }

            @Override
            public void onComplete() {
                Log.d(TAG, "complete");
            }
        });
```

接下来解释一下其中两个陌生的玩意：`ObservableEmitter`和`Disposable`.

`ObservableEmitter`： Emitter是发射器的意思，那就很好猜了，这个就是用来发出事件的，它可以发出三种类型的事件，通过调用`emitter`的`onNext(T value)`、`onComplete()`和`onError(Throwable error)`就可以分别发出next事件、complete事件和error事件。

但是，请注意，并不意味着你可以随意乱七八糟发射事件，需要满足一定的规则：

`上游`可以发送无限个`onNext`, `下游`也可以接收无限个`onNext`.
当`上游`发送了一个`onComplete`后, `上游` 发送`onComplete`之后的事件将会继续发送, 而`下游`收到`onComplete`事件之后将不再继续接收事件.
当`上游`发送了一个`onError`后, `上游`发送`onError`之后的事件将继续发送, 而`下游`收到`onError`事件之后将不再继续接收事件.
`上游`可以不发送`onComplete`或`onError`.
最为关键的是`onComplete`和`onError`必须唯一并且互斥, 即不能发多个`onComplete`, 也不能发多个`onError`, 也不能先发一个`onComplete`, 然后再发一个`onError`, 反之亦然

`注`: 关于`onComplete`和`onError`唯一并且互斥这一点, 是需要自行在代码中进行控制, 如果你的代码逻辑中违背了这个规则, 并不一定会导致程序崩溃. 比如发送多个`onComplete`是可以正常运行的, 依然是收到第一个`onComplete`就不再接收了, 但若是发送多个  `onError`, 则收到第二个`onError`事件会导致程序会崩溃.

以上几个规则用示意图表示如下:

发送事件类型|示意图 |
----|---- |
只发送onNext事件|![mahua](screenshots/image_next.png)
发送onComplete事件|![mahua](screenshots/image_complete.png)
发送onError事件|![mahua](screenshots/image_error.png)

介绍了ObservableEmitter, 接下来介绍`Disposable`, 这个单词的字面意思是一次性用品,用完即可丢弃的. 那么在RxJava中怎么去理解它呢, 对应于上面的水管的例子, 我们可以把它理解成两根管道之间的一个机关, 当调用它的`dispose()`方法时, 它就会将两根管道切断, 从而导致下游收不到事件.


`注意`: 调用`dispose()`并不会导致上游不再继续发送事件, 上游会继续发送剩余的事件.

来看个例子, 我们让上游依次发送`1,2,3,complete,4,`在下游收到第二个事件之后, 切断水管, 看看运行结果:
```java
        Observable.create(new ObservableOnSubscribe () {
            @Override
            public void subscribe(ObservableEmitter  emitter) throws Exception {
                Log.d(TAG, "emit 1");
                emitter.onNext(1);
                Log.d(TAG, "emit 2");
                emitter.onNext(2);
                Log.d(TAG, "emit 3");
                emitter.onNext(3);
                Log.d(TAG, "emit complete");
                emitter.onComplete();
                Log.d(TAG, "emit 4");
                emitter.onNext(4);
            }
        }).subscribe(new Observer () {
            private Disposable mDisposable;
            private int i;

            @Override
            public void onSubscribe(Disposable d) {
                Log.d(TAG, "subscribe");
                mDisposable = d;
            }

            @Override
            public void onNext(Integer value) {
                Log.d(TAG, "onNext: " + value);
                i++;
                if (i == 2) {
                    Log.d(TAG, "dispose");
                    mDisposable.dispose();
                    Log.d(TAG, "isDisposed : " + mDisposable.isDisposed());
                }
            }

            @Override
            public void onError(Throwable e) {
                Log.d(TAG, "error");
            }

            @Override
            public void onComplete() {
                Log.d(TAG, "complete");
            }
        });
```

运行结果为:

```java
12-02 06:54:07.728 7404-7404/zlc.season.rxjava2demo D/TAG: subscribe
12-02 06:54:07.728 7404-7404/zlc.season.rxjava2demo D/TAG: emit 1
12-02 06:54:07.728 7404-7404/zlc.season.rxjava2demo D/TAG: onNext: 1
12-02 06:54:07.728 7404-7404/zlc.season.rxjava2demo D/TAG: emit 2
12-02 06:54:07.728 7404-7404/zlc.season.rxjava2demo D/TAG: onNext: 2
12-02 06:54:07.728 7404-7404/zlc.season.rxjava2demo D/TAG: dispose
12-02 06:54:07.728 7404-7404/zlc.season.rxjava2demo D/TAG: isDisposed : true
12-02 06:54:07.728 7404-7404/zlc.season.rxjava2demo D/TAG: emit 3
12-02 06:54:07.728 7404-7404/zlc.season.rxjava2demo D/TAG: emit complete
12-02 06:54:07.728 7404-7404/zlc.season.rxjava2demo D/TAG: emit 4
```
从运行结果我们看到, 在收到`onNext 2`这个事件后, 切断了水管, 但是上游仍然发送了`3, complete, 4`这几个事件, 而且上游并没有因为发送了`onComplete`而停止. 同时可以看到下游的`onSubscribe()`方法是最先调用的.

`Disposable`的用处不止这些, 后面讲解到了线程的调度之后, 我们会发现它的重要性. 随着后续深入的讲解, 我们会在更多的地方发现它的身影.

另外, `subscribe()`有多个重载的方法:
```java
    public final Disposable subscribe() {}
    public final Disposable subscribe(Consumer  onNext) {}
    public final Disposable subscribe(Consumer  onNext, Consumer  onError) {}
    public final Disposable subscribe(Consumer  onNext, Consumer  onError, Action onComplete) {}
    public final Disposable subscribe(Consumer  onNext, Consumer  onError, Action onComplete, Consumer  onSubscribe) {}
    public final void subscribe(Observer  observer) {}
```

最后一个带有`Observer`参数的我们已经使用过了,这里对其他几个方法进行说明.

 * 不带任何参数的`subscribe() `表示下游不关心任何事件,你上游尽管发你的数据去吧, 老子可不管你发什么.
 *  带有一个`Consumer`参数的方法表示下游只关心`onNext`事件, 其他的事件我假装没看见, 因此我们如果只需要`onNext`事件可以这么写:

```java
        Observable.create(new ObservableOnSubscribe () {
            @Override
            public void subscribe(ObservableEmitter  emitter) throws Exception {
                Log.d(TAG, "emit 1");
                emitter.onNext(1);
                Log.d(TAG, "emit 2");
                emitter.onNext(2);
                Log.d(TAG, "emit 3");
                emitter.onNext(3);
                Log.d(TAG, "emit complete");
                emitter.onComplete();
                Log.d(TAG, "emit 4");
                emitter.onNext(4);
            }
        }).subscribe(new Consumer () {
            @Override
            public void accept(Integer integer) throws Exception {
                Log.d(TAG, "onNext: " + integer);
            }
        });

```
 * 其他几个方法同理, 这里就不一一解释了.

#####2）Scheduler —— 线程控制

还是以之前的例子, 两根水管:

![mahua](screenshots/image12.png)

正常情况下, `上游`和`下游`是工作在同一个线程中的, 也就是说上游在哪个线程发事件, 下游就在哪个线程接收事件.

怎么去理解呢, 以Android为例, 一个Activity的所有动作默认都是在主线程中运行的, 比如我们在onCreate中打出当前线程的名字:

```java
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        Log.d(TAG, Thread.currentThread().getName());
    }
```
结果便是:
```java
D/TAG: main
```
回到RxJava中, 当我们在主线程中去创建一个`上游Observable`来发送事件, 则这个`上游`默认就在主线程发送事件.

当我们在主线程去创建一个`下游Observer`来接收事件, 则这个下游默认就在主线程中接收事件, 来看段代码:
```java
@Override
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_main);

    Observable  observable = Observable.create(new ObservableOnSubscribe () {
        @Override
        public void subscribe(ObservableEmitter  emitter) throws Exception {
            Log.d(TAG, "Observable thread is : " + Thread.currentThread().getName());
            Log.d(TAG, "emit 1");
            emitter.onNext(1);
        }
    });

    Consumer  consumer = new Consumer () {
        @Override
        public void accept(Integer integer) throws Exception {
            Log.d(TAG, "Observer thread is :" + Thread.currentThread().getName());
            Log.d(TAG, "onNext: " + integer);
        }
    };

    observable.subscribe(consumer);
}
```

在主线程中分别创建`上游`和`下游`, 然后将他们连接在一起, 同时分别打印出它们所在的线程, 运行结果为:

```java
D/TAG: Observable thread is : main
D/TAG: emit 1
D/TAG: Observer thread is :main
D/TAG: onNext: 1
```

这就验证了刚才所说, `上下游默认`是在同一个线程工作.

这样肯定是满足不了我们的需求的, 我们更多想要的是这么一种情况, 在子线程中做耗时的操作, 然后回到主线程中来操作UI, 用图片来描述就是下面这个图片:

![mahua](screenshots/image_thread.png)

在这个图中, 我们用黄色水管表示子线程, 深蓝色水管表示主线程.

要达到这个目的, 我们需要先改变上游发送事件的线程, 让它去子线程中发送事件, 然后再改变下游的线程, 让它去主线程接收事件. 通过RxJava内置的线程调度器可以很轻松的做到这一点. 接下来看一段代码:

```java
@Override
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_main);

    Observable  observable = Observable.create(new ObservableOnSubscribe () {
        @Override
        public void subscribe(ObservableEmitter  emitter) throws Exception {
            Log.d(TAG, "Observable thread is : " + Thread.currentThread().getName());
            Log.d(TAG, "emit 1");
            emitter.onNext(1);
        }
    });

    Consumer  consumer = new Consumer () {
        @Override
        public void accept(Integer integer) throws Exception {
            Log.d(TAG, "Observer thread is :" + Thread.currentThread().getName());
            Log.d(TAG, "onNext: " + integer);
        }
    };

    observable.subscribeOn(Schedulers.newThread())
            .observeOn(AndroidSchedulers.mainThread())
            .subscribe(consumer);
}
```
还是刚才的例子, 只不过我们太添加了一点东西, 先来看看运行结果:

```java
 D/TAG: Observable thread is : RxNewThreadScheduler-2
 D/TAG: emit 1
 D/TAG: Observer thread is :main
 D/TAG: onNext: 1
```
可以看到, `上游`发送事件的线程的确改变了, 是在一个叫  RxNewThreadScheduler-2的线程中发送的事件, 而`下游`仍然在主线程中接收事件, 这说明我们的目的达成了, 接下来看看是如何做到的.

和上一段代码相比,这段代码只不过是增加了两行代码:
```java
.subscribeOn(Schedulers.newThread())
.observeOn(AndroidSchedulers.mainThread())
```
简单的来说, `subscribeOn()` 指定的是`上游`发送事件的线程, `observeOn()` 指定的是`下游`接收事件的线程.

多次指定`上游`的线程只有第一次指定的有效, 也就是说多次调用`subscribeOn()` 只有第一次的有效, 其余的会被忽略.

多次指定`下游`的线程是可以的, 也就是说每调用一次`observeOn()` , `下游`的线程就会切换一次.

举个例子:
```java
observable.subscribeOn(Schedulers.newThread())
         .subscribeOn(Schedulers.io())
         .observeOn(AndroidSchedulers.mainThread())
         .observeOn(Schedulers.io())
         .subscribe(consumer);
```

这段代码中指定了两次上游发送事件的线程, 分别是newThread和IO线程, 下游也指定了两次线程,分别是main和IO线程. 运行结果为:

```java
D/TAG: Observable thread is : RxNewThreadScheduler-3
D/TAG: emit 1
D/TAG: Observer thread is :RxCachedThreadScheduler-1
D/TAG: onNext: 1
```
可以看到, `上游`虽然指定了两次线程, 但只有第一次指定的有效, 依然是在RxNewThreadScheduler 线程中, 而`下游则`跑到了RxCachedThreadScheduler 中, 这个CacheThread其实就是IO线程池中的一个.

为了更清晰的看到`下游`的线程切换过程, 我们加点log:
```java
      observable.subscribeOn(Schedulers.newThread())
                .subscribeOn(Schedulers.io())
                .observeOn(AndroidSchedulers.mainThread())
                .doOnNext(new Consumer () {
                    @Override
                    public void accept(Integer integer) throws Exception {
                        Log.d(TAG, "After observeOn(mainThread), current thread is: " + Thread.currentThread().getName());
                    }
                })
                .observeOn(Schedulers.io())
                .doOnNext(new Consumer () {
                    @Override
                    public void accept(Integer integer) throws Exception {
                        Log.d(TAG, "After observeOn(io), current thread is : " + Thread.currentThread().getName());
                    }
                })
                .subscribe(consumer);
```
我们在下游线程切换之后, 把当前的线程打印出来, 运行结果:

```java
D/TAG: Observable thread is : RxNewThreadScheduler-1
D/TAG: emit 1
D/TAG: After observeOn(mainThread), current thread is: main
D/TAG: After observeOn(io), current thread is : RxCachedThreadScheduler-2
D/TAG: Observer thread is :RxCachedThreadScheduler-2
D/TAG: onNext: 1
```

可以看到, 每调用一次`observeOn()` 线程便会切换一次, 因此如果我们有类似的需求时, 便可知道如何处理了.

在RxJava中, 已经内置了很多线程选项供我们选择, 例如有:

 * Schedulers.io() 代表io操作的线程, 通常用于网络,读写文件等io密集型的操作
 * Schedulers.computation() 代表CPU计算密集型的操作, 例如需要大量计算的操作
 * Schedulers.newThread() 代表一个常规的新线程
 * AndroidSchedulers.mainThread() 代表Android的主线程
这些内置的Scheduler已经足够满足我们开发的需求, 因此我们应该使用内置的这些选项, 在RxJava内部使用的是线程池来维护这些线程, 所有效率也比较高.

#####3）操作符map和FlatMap 对数据进行转换

####应用场景1：注册成功后进行登录

定义Retrofit Api 接口
```java
public interface Api {
    @GET
    Observable  login(@Body LoginRequest request);

    @GET
    Observable  register(@Body RegisterRequest request);
}


```
接着创建一个Retrofit客户端:
```java
private static Retrofit create() {
            OkHttpClient.Builder builder = new OkHttpClient().newBuilder();
            builder.readTimeout(10, TimeUnit.SECONDS);
            builder.connectTimeout(9, TimeUnit.SECONDS);

            if (BuildConfig.DEBUG) {
                HttpLoggingInterceptor interceptor = new HttpLoggingInterceptor();
                interceptor.setLevel(HttpLoggingInterceptor.Level.BODY);
                builder.addInterceptor(interceptor);
            }

            return new Retrofit.Builder().baseUrl(ENDPOINT)
                    .client(builder.build())
                    .addConverterFactory(GsonConverterFactory.create())
                    .addCallAdapterFactory(RxJava2CallAdapterFactory.create())
                    .build();
}
```
很明显, 这是一个嵌套的网络请求, 首先需要去请求注册, 待注册成功回调了再去请求登录的接口.

我们当然可以想当然的写成这样:
```java
    private void login() {
        api.login(new LoginRequest())
                .subscribeOn(Schedulers.io())               //在IO线程进行网络请求
                .observeOn(AndroidSchedulers.mainThread())  //回到主线程去处理请求结果
                .subscribe(new Consumer () {
                    @Override
                    public void accept(LoginResponse loginResponse) throws Exception {
                        Toast.makeText(MainActivity.this, "登录成功", Toast.LENGTH_SHORT).show();
                    }
                }, new Consumer () {
                    @Override
                    public void accept(Throwable throwable) throws Exception {
                        Toast.makeText(MainActivity.this, "登录失败", Toast.LENGTH_SHORT).show();
                    }
                });
    }

    private void register() {
        api.register(new RegisterRequest())
                .subscribeOn(Schedulers.io())               //在IO线程进行网络请求
                .observeOn(AndroidSchedulers.mainThread())  //回到主线程去处理请求结果
                .subscribe(new Consumer () {
                    @Override
                    public void accept(RegisterResponse registerResponse) throws Exception {
                        Toast.makeText(MainActivity.this, "注册成功", Toast.LENGTH_SHORT).show();
                        login();   //注册成功, 调用登录的方法
                    }
                }, new Consumer () {
                    @Override
                    public void accept(Throwable throwable) throws Exception {
                        Toast.makeText(MainActivity.this, "注册失败", Toast.LENGTH_SHORT).show();
                    }
                });
    }
```
(其实能写成这样的代码的人也很不错了, 至少没写到一起...)

这样的代码能够工作, 但不够优雅, 通过本节的学习, 可以让我们用一种更优雅的方式来解决这个问题.

#####3.1）map 操作符 一对一的转转换
map是RxJava中最简单的一个变换操作符了, 它的作用就是对`上游`image发送的每一个事件应用一个函数, 使得每一个事件都按照指定的函数去变化. 用事件图表示如下:
![mahua](screenshots/image_map.png)

图中map中的函数作用是将圆形事件转换为矩形事件, 从而导致`下游`接收到的事件就变为了矩形.用代码来表示这个例子就是:

```java
    Observable.create(new ObservableOnSubscribe () {
            @Override
            public void subscribe(ObservableEmitter  emitter) throws Exception {
                emitter.onNext(1);
                emitter.onNext(2);
                emitter.onNext(3);
            }
        }).map(new Function () {
            @Override
            public String apply(Integer integer) throws Exception {
                return "This is result " + integer;
            }
        }).subscribe(new Consumer () {
            @Override
            public void accept(String s) throws Exception {
                Log.d(TAG, s);
            }
        });
```

在`上游`我们发送的是数字类型, 而在`下游`我们接收的是String类型, 中间起转换作用的就是map操作符, 运行结果为:
```java
 D/TAG: This is result 1
 D/TAG: This is result 2
 D/TAG: This is result 3
```

通过Map, 可以将`上游`发来的事件转换为任意的类型, 可以是一个Object, 也可以是一个集合, 如此强大的操作符你难道不想试试?

接下来我们来看另外一个广为人知的操作符flatMap.


#####3.2）FlatMap 操作符 多对多的转转换

flatMap是一个非常强大的操作符, 先用一个比较难懂的概念说明一下:

`FlatMap`将一个发送事件的`上游Observable`变换为多个发送事件的`Observables`，然后将它们发射的事件合并后放进一个单独的`Observable`里.

这句话比较难以理解, 我们先通俗易懂的图片来详细的讲解一下, 首先先来看看整体的一个图片:
![mahua](screenshots/image_flatmap.png)

先看看`上游`, 上游发送了三个事件, 分别是1,2,3, 注意它们的颜色.

中间flatMap的作用是将圆形的事件转换为一个发送矩形事件和三角形事件的新的上游Observable.

还是不能理解? 别急, 再来看看分解动作:

![mahua](screenshots/image_flatmap2.png)


这样就很好理解了吧 !!!

`上游`每发送一个事件, `flatMap`都将创建一个新的水管, 然后发送转换之后的新的事件, 下游接收到的就是这些新的水管发送的数据. 这里需要`注意的是, flatMap并不保证事件的顺序`, 也就是图中所看到的, 并不是事件1就在事件2的前面. 如果需要保证顺序则需要使用concatMap.

说了原理, 我们还是来看看实际中的代码如何写吧:
```java
        Observable.create(new ObservableOnSubscribe () {
            @Override
            public void subscribe(ObservableEmitter  emitter) throws Exception {
                emitter.onNext(1);
                emitter.onNext(2);
                emitter.onNext(3);
            }
        }).flatMap(new Function >() {
            @Override
            public ObservableSource  apply(Integer integer) throws Exception {
                final List  list = new ArrayList<>();
                for (int i = 0; i  () {
            @Override
            public void accept(String s) throws Exception {
                Log.d(TAG, s);
            }
        });
```

如代码所示, 我们在flatMap中将`上游`发来的每个事件转换为一个新的发送三个String事件的水管, 为了看到flatMap结果是无序的,所以加了10毫秒的延时, 来看看运行结果吧:

```java
D/TAG: I am value 1
D/TAG: I am value 1
D/TAG: I am value 1
D/TAG: I am value 3
D/TAG: I am value 3
D/TAG: I am value 3
D/TAG: I am value 2
D/TAG: I am value 2
D/TAG: I am value 2
```

结果也确实验证了我们之前所说.

这里也简单说一下`concatMap`吧, 它和`flatMap`的作用几乎一模一样, `只是它的结果是严格按照上游发送的顺序来发送的`, 来看个代码吧:

```java
 Observable.create(new ObservableOnSubscribe () {
            @Override
            public void subscribe(ObservableEmitter  emitter) throws Exception {
                emitter.onNext(1);
                emitter.onNext(2);
                emitter.onNext(3);
            }
        }).concatMap(new Function >() {
            @Override
            public ObservableSource  apply(Integer integer) throws Exception {
                final List  list = new ArrayList<>();
                for (int i = 0; i  () {
            @Override
            public void accept(String s) throws Exception {
                Log.d(TAG, s);
            }
        });
```

只是将之前的flatMap改为了concatMap, 其余原封不动, 运行结果如下:

```java
D/TAG: I am value 1
D/TAG: I am value 1
D/TAG: I am value 1
D/TAG: I am value 2
D/TAG: I am value 2
D/TAG: I am value 2
D/TAG: I am value 3
D/TAG: I am value 3
D/TAG: I am value 3
```
可以看到, 结果仍然是有序的.

好了关于RxJava的操作符最基本的使用就讲解到这里了, RxJava中内置了许许多多的操作符, 这里通过讲解`map`和`flatMap`只是起到一个抛砖引玉的作用, 关于其他的操作符只要大家按照本文的思路去理解, 再仔细阅读文档, 应该是没有问题的了, 如果大家有需要也可以将需要讲解的操作符列举出来, 我可以根据大家的需求讲解一下.

学习了FlatMap操作符, 登录注册那个问题了.

如何优雅的解决嵌套请求, 只需要用flatMap转换一下就行了.

先回顾一下上一节的请求接口:
```java
public interface Api {
    @GET
    Observable  login(@Body LoginRequest request);

    @GET
    Observable  register(@Body RegisterRequest request);
}
```

可以看到登录和注册返回的都是一个上游Observable, 而我们的flatMap操作符的作用就是把一个Observable转换为另一个Observable, 因此结果就很显而易见了:

```java
            api.register(new RegisterRequest())            //发起注册请求
                .subscribeOn(Schedulers.io())               //在IO线程进行网络请求
                .observeOn(AndroidSchedulers.mainThread())  //回到主线程去处理请求注册结果
                .doOnNext(new Consumer () {
                    @Override
                    public void accept(RegisterResponse registerResponse) throws Exception {
                        //先根据注册的响应结果去做一些操作
                    }
                })
                .observeOn(Schedulers.io())                 //回到IO线程去发起登录请求
                .flatMap(new Function >() {
                    @Override
                    public ObservableSource  apply(RegisterResponse registerResponse) throws Exception {
                        return api.login(new LoginRequest());
                    }
                })
                .observeOn(AndroidSchedulers.mainThread())  //回到主线程去处理请求登录的结果
                .subscribe(new Consumer () {
                    @Override
                    public void accept(LoginResponse loginResponse) throws Exception {
                        Toast.makeText(MainActivity.this, "登录成功", Toast.LENGTH_SHORT).show();
                    }
                }, new Consumer () {
                    @Override
                    public void accept(Throwable throwable) throws Exception {
                        Toast.makeText(MainActivity.this, "登录失败", Toast.LENGTH_SHORT).show();
                    }
                });
```

从这个例子也可以看到我们切换线程是多么简单.

#####4）操作符zip

`Zip`通过一个函数将多个Observable发送的事件结合到一起，然后发送这些组合到一起的事件. 它按照严格的顺序应用这个函数。它只发射与发射数据项最少的那个Observable一样多的数据。

我们再用通俗易懂的图片来解释一下:

![mahua](screenshots/image_zip.png)
从这个图中可以看见, 这次上游和以往不同的是, 我们有两根水管了.

其中一根水管负责发送圆形事件 , 另外一根水管负责发送`三角形事件` , 通过Zip操作符, 使得`圆形事件` 和`三角形事件` 合并为了一个`矩形事件` .

下面我们再来看看分解动作：

![mahua](screenshots/image_zip.png)

通过分解动作我们可以看出:

 * 组合的过程是`分别从` 两根水管里`各取出一个事件` 来进行组合, 并且一个事件`只能被使用一次`, 组合的顺序是`严格按照事件发送的顺利` 来进行的, 也就是说不会出现`圆形1` 事件和`三角形B `事件进行合并, 也不可能出现`圆形2` 和`三角形A` 进行合并的情况.
 * 最终`下游收到的事件数量` 是和`上游中发送事件最少的那一根水管的事件数量` 相同. 这个也很好理解, 因为是从`每一根水管` 里取一个事件来进行合并,` 最少的` 那个肯定就`最先取完` , 这个时候其他的水`管尽管还有事件` , 但是已经没有足够的事件来组合了, 因此下游就不会收到剩余的事件了.

分析了大概的原理, 我们还是劳逸结合, 先来看看实际中的代码怎么写吧:

```java
Observable  observable1 = Observable.create(new ObservableOnSubscribe () {
    @Override
    public void subscribe(ObservableEmitter  emitter) throws Exception {
        Log.d(TAG, "emit 1");
        emitter.onNext(1);
        Log.d(TAG, "emit 2");
        emitter.onNext(2);
        Log.d(TAG, "emit 3");
        emitter.onNext(3);
        Log.d(TAG, "emit 4");
        emitter.onNext(4);
        Log.d(TAG, "emit complete1");
        emitter.onComplete();
    }
});

Observable  observable2 = Observable.create(new ObservableOnSubscribe () {
    @Override
    public void subscribe(ObservableEmitter  emitter) throws Exception {
        Log.d(TAG, "emit A");
        emitter.onNext("A");
        Log.d(TAG, "emit B");
        emitter.onNext("B");
        Log.d(TAG, "emit C");
        emitter.onNext("C");
        Log.d(TAG, "emit complete2");
        emitter.onComplete();
    }
});

Observable.zip(observable1, observable2, new BiFunction () {
    @Override
    public String apply(Integer integer, String s) throws Exception {
        return integer + s;
    }
}).subscribe(new Observer () {
    @Override
    public void onSubscribe(Disposable d) {
        Log.d(TAG, "onSubscribe");
    }

    @Override
    public void onNext(String value) {
        Log.d(TAG, "onNext: " + value);
    }

    @Override
    public void onError(Throwable e) {
        Log.d(TAG, "onError");
    }

    @Override
    public void onComplete() {
        Log.d(TAG, "onComplete");
    }
});


```
我们分别创建了两个上游水管, 一个发送1,2,3,4,Complete, 另一个发送A,B,C,Complete, 接着用Zip把发出的事件组合, 来看看运行结果吧:
```java
D/TAG: onSubscribe
D/TAG: emit 1
D/TAG: emit 2
D/TAG: emit 3
D/TAG: emit 4
D/TAG: emit complete1
D/TAG: emit A
D/TAG: onNext: 1A
D/TAG: emit B
D/TAG: onNext: 2B
D/TAG: emit C
D/TAG: onNext: 3C
D/TAG: emit complete2
D/TAG: onComplete
```
结果似乎是对的... 但是总感觉什么地方不对劲...

哪儿不对劲呢, 为什么感觉是水管一发送完了之后, 水管二才开始发送啊? 到底是不是呢, 我们来验证一下:

```java
Observable  observable1 = Observable.create(new ObservableOnSubscribe () {
    @Override
    public void subscribe(ObservableEmitter  emitter) throws Exception {
        Log.d(TAG, "emit 1");
        emitter.onNext(1);
        Thread.sleep(1000);

        Log.d(TAG, "emit 2");
        emitter.onNext(2);
        Thread.sleep(1000);

        Log.d(TAG, "emit 3");
        emitter.onNext(3);
        Thread.sleep(1000);

        Log.d(TAG, "emit 4");
        emitter.onNext(4);
        Thread.sleep(1000);

        Log.d(TAG, "emit complete1");
        emitter.onComplete();
    }
});

Observable  observable2 = Observable.create(new ObservableOnSubscribe () {
    @Override
    public void subscribe(ObservableEmitter  emitter) throws Exception {
        Log.d(TAG, "emit A");
        emitter.onNext("A");
        Thread.sleep(1000);

        Log.d(TAG, "emit B");
        emitter.onNext("B");
        Thread.sleep(1000);

        Log.d(TAG, "emit C");
        emitter.onNext("C");
        Thread.sleep(1000);

        Log.d(TAG, "emit complete2");
        emitter.onComplete();
    }
});

Observable.zip(observable1, observable2, new BiFunction () {
    @Override
    public String apply(Integer integer, String s) throws Exception {
        return integer + s;
    }
}).subscribe(new Observer () {
    @Override
    public void onSubscribe(Disposable d) {
        Log.d(TAG, "onSubscribe");
    }

    @Override
    public void onNext(String value) {
        Log.d(TAG, "onNext: " + value);
    }

    @Override
    public void onError(Throwable e) {
        Log.d(TAG, "onError");
    }

    @Override
    public void onComplete() {
        Log.d(TAG, "onComplete");
    }
});
```

这次我们在每发送一个事件之后加入了一秒钟的延时, 来看看运行结果吧, 注意这是个GIF图:
![mahua](screenshots/image_zip3.gif)

好像真的是先发送的水管一再发送的水管二呢, 为什么会有这种情况呢? 因为我们两根水管都是运行在同一个线程里, 同一个线程里执行代码肯定有先后顺序呀.

因此我们来稍微改一下, 不让他们在同一个线程, 不知道怎么切换线程的, 请掉头看前面几节.

```java
Observable  observable1 = Observable.create(new ObservableOnSubscribe () {
    @Override
    public void subscribe(ObservableEmitter  emitter) throws Exception {
        Log.d(TAG, "emit 1");
        emitter.onNext(1);
        Thread.sleep(1000);

        Log.d(TAG, "emit 2");
        emitter.onNext(2);
        Thread.sleep(1000);

        Log.d(TAG, "emit 3");
        emitter.onNext(3);
        Thread.sleep(1000);

        Log.d(TAG, "emit 4");
        emitter.onNext(4);
        Thread.sleep(1000);

        Log.d(TAG, "emit complete1");
        emitter.onComplete();
    }
}).subscribeOn(Schedulers.io());

Observable  observable2 = Observable.create(new ObservableOnSubscribe () {
    @Override
    public void subscribe(ObservableEmitter  emitter) throws Exception {
        Log.d(TAG, "emit A");
        emitter.onNext("A");
        Thread.sleep(1000);

        Log.d(TAG, "emit B");
        emitter.onNext("B");
        Thread.sleep(1000);

        Log.d(TAG, "emit C");
        emitter.onNext("C");
        Thread.sleep(1000);

        Log.d(TAG, "emit complete2");
        emitter.onComplete();
    }
}).subscribeOn(Schedulers.io());

Observable.zip(observable1, observable2, new BiFunction () {
    @Override
    public String apply(Integer integer, String s) throws Exception {
        return integer + s;
    }
}).subscribe(new Observer () {
    @Override
    public void onSubscribe(Disposable d) {
        Log.d(TAG, "onSubscribe");
    }

    @Override
    public void onNext(String value) {
        Log.d(TAG, "onNext: " + value);
    }

    @Override
    public void onError(Throwable e) {
        Log.d(TAG, "onError");
    }

    @Override
    public void onComplete() {
        Log.d(TAG, "onComplete");
    }
});
```

好了, 这次我们让水管都在IO线程里发送事件, 再来看看运行结果:
```java
D/TAG: onSubscribe
D/TAG: emit A
D/TAG: emit 1
D/TAG: onNext: 1A
D/TAG: emit B
D/TAG: emit 2
D/TAG: onNext: 2B
D/TAG: emit C
D/TAG: emit 3
D/TAG: onNext: 3C
D/TAG: emit complete2
D/TAG: onComplete
```
![mahua](screenshots/image_zip4.gif)

诶! 这下就对了嘛, 两根水管同时开始发送, 每发送一个, Zip就组合一个, 再将组合结果发送给下游.

不对呀! 可能细心点的朋友又看出端倪了, 第一根水管明明发送了四个数据+一个Complete, 之前明明还有的, 为啥到这里没了呢?

这是因为我们之前说了, zip发送的事件数量跟上游中发送事件最少的那一根水管的事件数量是有关的, 在这个例子里我们第二根水管只发送了三个事件然后就发送了Complete, 这个时候尽管第一根水管还有事件4 和事件Complete 没有发送, 但是它们发不发送还有什么意义呢? 所以本着节约是美德的思想, 就干脆打断它的狗腿, 不让它发了.

至于前面的例子为什么会发送, 刚才不是已经说了是！在！同！一！个！线！程！里！吗！！！！再问老子打死你！

有好事的程序员可能又要问了， 那我不发送Complete呢？ 答案是显然的, 上游会继续发送事件, 但是下游仍然收不到那些多余的事件. 不信你可以试试.

####应用场景2：获取多个接口数据返回后再显示数据

比如一个界面需要展示用户的一些信息, 而这些信息分别要从两个服务器接口中获取, 而只有当两个都获取到了之后才能进行展示, 这个时候就可以用Zip了:

首先分别定义这两个请求接口:

```java
public interface Api {
    @GET
    Observable  getUserBaseInfo(@Body UserBaseInfoRequest request);

    @GET
    Observable  getUserExtraInfo(@Body UserExtraInfoRequest request);

}
```
接着用Zip来打包请求:
```java
Observable  observable1 =
        api.getUserBaseInfo(new UserBaseInfoRequest()).subscribeOn(Schedulers.io());

Observable  observable2 =
        api.getUserExtraInfo(new UserExtraInfoRequest()).subscribeOn(Schedulers.io());

Observable.zip(observable1, observable2,
        new BiFunction () {
            @Override
            public UserInfo apply(UserBaseInfoResponse baseInfo,
                                  UserExtraInfoResponse extraInfo) throws Exception {
                return new UserInfo(baseInfo, extraInfo);
            }
        }).observeOn(AndroidSchedulers.mainThread())
        .subscribe(new Consumer () {
            @Override
            public void accept(UserInfo userInfo) throws Exception {
                //do something;
            }
        });
```




























####4.创建 Observer 对象 -即创建观察者对象
序号|方法名称 | 参数类型 |说明
----|---- | ---- | ------
1|Observable.create()/ Observable.just()/ Flowable.just()|ObservableOnSubscribe |通过ObservableOnSubscribe对象创建一个Observable对象
2|Observable.fromArray()|Object[]|通过数组对象创建一个Observable对象
3|Observable.fromIterable()|Iterable|通过Iterable的子类对象创建一个Observable对象
4|Observable.interval()|long initialDelay, long period, TimeUnit unit|创建个每隔指定的时间间隔就发射一个序号的 Observable 对象，可用来做倒计时心跳包等操作，无限发送，除非调用dispose()可以终止。
5|Observable.timer()|long delay, TimeUnit unit|创建一个在指定延迟时间后发射一条数据（ 固定值：0 ）的 Observable 对象，可用来做定时操作。
6|Observable.range()|int start,int count|创建一个可以发射一个指定范围的数的 Observable 对象，可用来控制指定范围了的数据。



####5. 操作符的使用

序号|操作符|参数类型 |说明
----|----|----|----
1|subscribeOn|Scheduler scheduler|设置被订阅者执行的线程，即被观察者在的线程
2|observeOn|Scheduler scheduler|设置观察者执行的线程
3|map|Scheduler scheduler|map 操作符是可以将返回的数据变换成新的数据类新，比如你可以使用 map 操作符将原来要发射的字符串数据变换成数值型在发射出去。
4|map|Function  mapper|map 操作符是可以将返回的数据变换成新的数据类新，比如你可以使用 map 操作符将原来要发射的字符串数据变换成数值型在发射出去。
5|flatMap|Function > mapper|不同于map的是flatMap 返回的是一个全新的Observable 对象。
6|filter|Predicate  predicate|filter这个操作符可以作为数据筛选器，帮你过滤不想要的数据。
7|take|long count|take此操作符用于指定想要的数据数量,比如获取数组前面10
8|doOnNext|Consumer  onNext|doOnNext此操作符可以在消费者也就是被观察者 接收到数据之前做事。
9|doAfterNext|Consumer  onNext|doOnNext此操作符可以在消费者也就是被观察者 接收到数据之后做事。
9|doOnError|Consumer  onError|doOnError此操作符可以在消费者也就是被观察者出现异常之前，收到处理事件，可以用在保存错误信息
10|doOnComplete|Action onComplete|doOnComplete 此操作符可以在消费者也就是被观察者所有事件处理完成以后发出事件，要比subscribe（订阅者）中的doOnComplete先执行
11|subscribe|Consumer  onNext, Consumer  onError, Action onComplete|subscribe 此操作符用来订阅被观察者的事件

####6.Subscribe (订阅)

创建了 Observable**(被观察者)** 和 Observer**（观察者）** 之后，再用 subscribe() 方法将它们联结起来，整条链子就可以工作了。代码形式很简单：

observable.subscribe(observer);
// 或者：
observable.subscribe(subscriber);

    有人可能会注意到， subscribe() 这个方法有点怪：它看起来是『observalbe 订阅了 observer / subscriber』而不是
    『observer / subscriber 订阅了 observalbe』，这看起来就像『杂志订阅了读者』一样颠倒了对象关系。
    这让人读起来有点别扭，不过如果把 API 设计成 observer.subscribe(observable) / subscriber.subscribe(observable) ，
    虽然更加符合思维逻辑，但对流式 API 的设计就造成影响了，比较起来明显是得不偿失的。

**Observable.subscribe(Subscriber) 的内部实现是这样的（仅核心代码）：**

![mahua](screenshots/image06.png)

可以看到，**subscriber()** 做了3件事：
调用 Subscriber.onStart() 。这个方法在前面已经介绍过，是一个可选的准备方法。
调用 Observable 中的 OnSubscribe.call(Subscriber) 。在这里，事件发送的逻辑开始运行。从这也可以看出，在 RxJava 中， Observable 并不是在创建的时候就立即开始发送事件，而是在它被订阅的时候，即当 subscribe() 方法执行的时候。
将传入的 Subscriber 作为 Subscription 返回。这是为了方便 unsubscribe().
整个过程中对象间的关系如下图：
![mahua](screenshots/image07.jpg)

或者可以看动图：

![mahua](screenshots/image08.gif)

####7.线程控制 —— Scheduler (一)

在不指定线程的情况下， RxJava 遵循的是线程不变的原则，即：在哪个线程调用 subscribe()，就在哪个线程生产事件；
在哪个线程生产事件，就在哪个线程消费事件。如果需要切换线程，就需要用到 Scheduler （调度器）。

1) Scheduler 的 API

在RxJava 中，Scheduler ——调度器，相当于线程控制器，RxJava 通过它来指定每一段代码应该运行在什么样的线程。RxJava 已经内置了几个 Scheduler ，它们已经适合大多数的使用场景：

- Schedulers.immediate(): 直接在当前线程运行，相当于不指定线程。这是默认的 Scheduler。
- Schedulers.newThread(): 总是启用新线程，并在新线程执行操作。
- Schedulers.io(): I/O 操作（读写文件、读写数据库、网络信息交互等）所使用的 Scheduler。行为模式和 newThread() 差不多，区别在于 io() 的内部实现是是用一个无数量上限的线程池，可以重用空闲的线程，因此多数情况下 io() 比 newThread() 更有效率。不要把计算工作放在 io() 中，可以避免创建不必要的线程。
- Schedulers.computation(): 计算所使用的 Scheduler。这个计算指的是 CPU 密集型计算，即不会被 I/O 等操作限制性能的操作，例如图形的计算。这个 Scheduler 使用的固定的线程池，大小为 CPU 核数。不要把 I/O 操作放在 computation() 中，否则 I/O 操作的等待时间会浪费 CPU。
另外， Android 还有一个专用的 AndroidSchedulers.mainThread()，它指定的操作将在 Android 主线程运行。
有了这几个 Scheduler ，就可以使用 subscribeOn() 和 observeOn() 两个方法来对线程进行控制了。 * subscribeOn(): 指定 subscribe() 所发生的线程，即 Observable.OnSubscribe 被激活时所处的线程。或者叫做事件产生的线程。 * observeOn(): 指定 Subscriber 所运行在的线程。或者叫做事件消费的线程。

文字叙述总归难理解，上代码：

![mahua](screenshots/image09.png)

2) Scheduler 的原理

RxJava 的 Scheduler API 很方便，也很神奇（加了一句话就把线程切换了，怎么做到的？而且 subscribe() 不是最外层直接调用的方法吗，它竟然也能被指定线程？）。然而 Scheduler 的原理需要放在后面讲，因为它的原理是以下一节《变换》的原理作为基础的。

好吧这一节其实我屁也没说，只是为了让你安心，让你知道我不是忘了讲原理，而是把它放在了更合适的地方。


####8.变换

RxJava 提供了对事件序列进行变换的支持，这是它的核心功能之一，也是大多数人说『RxJava 真是太好用了』的最大原因。所谓变换，就是将事件序列中的对象或整个序列进行加工处理，转换成不同的事件或事件序列。概念说着总是模糊难懂的，来看 API。

##### 使用map 一对一转换

![mahua](screenshots/image10.png)

这里出现了一个叫做 Function 的类。它和 Action 非常相似，也是 RxJava 的一个接口，用于包装含有一个参数的方法。 Function 和 Action 的区别在于， Function 包装的是有返回值的方法。

可以看到，map() 方法将参数中的 String 对象转换成一个 Bitmap 对象后返回，而在经过 map() 方法后，事件的参数类型也由 String 转为了 Bitmap。这种直接变换对象并返回的，是最常见的也最容易理解的变换。不过 RxJava 的变换远不止这样，它不仅可以针对事件对象，还可以针对整个事件队列，这使得 RxJava 变得非常灵活。我列举几个常用的变换：

- map(): 事件对象的直接变换，具体功能上面已经介绍过。它是 RxJava 最常用的变换。 map() 的示意图：

![mahua](screenshots/image11.jpg)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)