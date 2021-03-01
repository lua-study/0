#  ToDo 响应式

模型修改：

将原本的 `var todoItems: [TodoItem] = []` 修改为 `let todoItems = Variable ([])`，并提供 `let bag = DisposeBag()` 来回收其中的资源。模型通过 `todoItems.value` 来获取实际的数据。

另一方面，当需要监听另一个页面的信息，并通过信息改变来改变本页面的数据，则通过 `fileprivate let todoSubject = PublishSubject ()` 的 PublishSubject 来传递事件。

当需要监听某个事件的完成情况时，可以通过返回 `Observable` 来监听，如项目中封装保存、上传到 iCloud 的逻辑。在合适的实际调用 `onError`、`onCompleted`，并最后返回 `Disposables.create()`。



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)