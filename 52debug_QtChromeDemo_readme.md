# QtChromeDemo
使用Qt5.10自带的QtWebEngine, WebChannel进行C++和Qt通信，同时进行一般浏览器需要功能的简单尝试。

# 依赖环境   
> Qt5.10 MSVC 2015  
> Flash 的Pep插件，即Chrome版本的Flash  

运行时，需要将index.html复制到release/debug目录下。  

# 主要内容  
## 1. Cpp Call js
```cpp
m_pView->page()->runJavaScript("showmsg('I come from cpp call js scripts!');");
```

## 2. WebChannel
```cpp
// 声明变量
class MyCppObj : public QObject{
    Q_OBJECT
public:
    MyCppObj(QObject* p):QObject(p){

    }

public slots:
    void t1(QString msg){
        QMessageBox::warning(NULL,"I am a Qt native MsgBox","Msg: "+msg);
    }
signals:
    void sigNotify(QString msg);
};

// 加入WebChannel
// 早期的 WebView，使用 void QWebFrame::addToJavaScriptWindowObject(const QString& name...
// 新版本通过WebChannel来实现双向通信。
QWebChannel *pWebChannel   = new QWebChannel(m_pView->page());
m_pObj = new MyCppObj(NULL);
pWebChannel->registerObject("a1", m_pObj);
m_pView->page()->setWebChannel(pWebChannel);


// cpp call js
emit m_pObj->sigNotify("I come from Cpp call qt sig whcih connect js func! ");

// js call Cpp
    
   
function showmsg(message)  
{  
    var output = document.getElementById("output");  
    output.innerHTML = output.innerHTML + message + "\n";  
}  
//Web initial loading 
window.onload = function() { 
	showmsg("I am from web, call js func!");   
    new QWebChannel(qt.webChannelTransport, function(channel) { 
    
        //Get Qt interact object  
        var a1 = channel.objects.a1; 
        
        //Web send message to Qt 
        document.getElementById("send").onclick = function() {  
            var input = document.getElementById("input");  
            if (!input.value) {  
                return;  
            }  
            
            //Web use the interface of Qt 
            a1.t1(input.value);  // js call cpp
        }  
        
        //Web connect the Qt signal, then Qt can call "output" function
        a1.sigNotify.connect(function(str) {  
            showmsg(str);  
        });    
    });  
}  
  
```
## 3. Web新建窗口拦截 
```cpp
// 通过继承 QWebEngineView::createwindows进行拦截，这里修改为永远不新建
class MyWebView : public QWebEngineView{
    Q_OBJECT
public:
    void contextMenuEvent(QContextMenuEvent *event) {
        qDebug() globalPos();
        event->accept();
    }
    QWebEngineView *createWindow(QWebEnginePage::WebWindowType type) {
        qDebug() setUrl(QUrl("https://baidu.com"));
            return false;
        }

        return true;
    }
};
```

## 5. Url resource 拦截 
```cpp
// 通过继承 QWebEngineUrlRequestInterceptor::interceptRequest进行拦截
// 也可以通过这里进行资源替换
class WebUrlRequestInterceptor : public QWebEngineUrlRequestInterceptor
{
    Q_OBJECT
public:
    WebUrlRequestInterceptor(QObject *p = Q_NULLPTR)
        :QWebEngineUrlRequestInterceptor(p){
    }
    void interceptRequest(QWebEngineUrlRequestInfo &info){
        QString rsrct = "";
        switch(info.resourceType()){
            case 0:rsrct="ResourceTypeMainFrame = 0, // top level page";break;
            case 1:rsrct="ResourceTypeSubFrame, // frame or iframe";break;
            case 2:rsrct="ResourceTypeStylesheet, // a CSS stylesheet";break;
            case 3:rsrct="ResourceTypeScript, // an external script";break;
            case 4:rsrct="ResourceTypeImage, // an image (jpg/gif/png/etc)";break;
            case 5:rsrct="ResourceTypeFontResource, // a font";break;
            case 6:rsrct="ResourceTypeSubResource, // an other subresource.";break;
            case 7:rsrct="ResourceTypeObject, // an object (or embed) tag for a plugin,";break;
            case 8:rsrct="ResourceTypeMedia, // a media resource.";break;
            case 9:rsrct="ResourceTypeWorker, // the main resource of a dedicated worker.";break;
            case 10:rsrct="ResourceTypeSharedWorker, // the main resource of a shared worker.";break;
            case 11:rsrct="ResourceTypePrefetch, // an explicitly requested prefetch";break;
            case 12:rsrct="ResourceTypeFavicon, // a favicon";break;
            case 13:rsrct="ResourceTypeXhr, // a XMLHttpRequest";break;
            case 14:rsrct="ResourceTypePing, // a ping request for  ";break;
            case 15:rsrct="ResourceTypeServiceWorker, // the main resource of a service worker.";break;
            case 16:rsrct="ResourceTypeUnknown";break;

            default : rsrct="未知类型";break;
        }
      // 这里拦截 url resource 请求
      qDebug() setRequestInterceptor(webInterceptor);
```
## 6. 下载拦截 
```cpp
auto profile = QWebEngineProfile::defaultProfile();
QObject::connect(
    profile, SIGNAL(downloadRequested(QWebEngineDownloadItem*)),
    this, SLOT(downloadRequested(QWebEngineDownloadItem*)));

// 下载的处理
void Dialog::downloadRequested(QWebEngineDownloadItem *download)
{
    qDebug() id() url() mimeType();
    QString path = QFileDialog::getSaveFileName(this, tr("Save as"), download->path());
    if (path.isEmpty())
        return;

    download->setPath(path);
    //download->accept();
    download->cancel();
    // 通过Download对象可以获取到下载的进度信息
}
```
## 7. 右键菜单 
```cpp
class MyWebView : public QWebEngineView{
    Q_OBJECT
public:
    void contextMenuEvent(QContextMenuEvent *event) {
	    QMenu *menu = page()->createStandardContextMenu(); // 通过这个获取标准web菜单
	    const QList  actions = menu->actions();
	    auto it = std::find(actions.cbegin(), actions.cend(), page()->action(QWebEnginePage::OpenLinkInThisWindow));
	    if (it != actions.cend()) {
	        (*it)->setText(tr("Open Link in This Tab"));
	        ++it;
	        QAction *before(it == actions.cend() ? nullptr : *it);
	        menu->insertAction(before, page()->action(QWebEnginePage::OpenLinkInNewWindow));
	        menu->insertAction(before, page()->action(QWebEnginePage::OpenLinkInNewTab));
	    }
	    menu->popup(event->globalPos());
    }
};
```
## 8. Qt控件与Web叠加渲染
```cpp
auto a2 = new QLabel(this);
a2->setText(" Hello, world! ");
a2->setGeometry(50,50, 200, 100);
a2->setStyleSheet("color: red; background-color: rgba(10,10,100,160);"); // 半透明控件
a2->show();
```

## 9. Qt/JS函数有返回值   
默认的Demo中，Qt函数或者js函数有返回值，则返回undefined。  
原因是：  
> Note that all communication between the HTML client and the QML/C++ server is asynchronous. Properties are cached on the HTML side. Furthermore keep in mind that only QML/C++ data types which can be converted to JSON will be (de-)serialized properly and thus accessible to HTML clients. 
> http://blog.csdn.net/xsolver/article/details/15505465

解决办法见Demo:  
```js
new QWebChannel(yourTransport, function(channel) {
	// Connect to a signal:
	channel.objects.foo.mySignal.connect(function() {
	  // This callback will be invoked whenever the signal is emitted on the C++/QML side.
	  console.log(arguments);
	});

	// To make the object known globally, assign it to the window object, i.e.:
	window.foo = channel.objects.foo;

	// Invoke a method:
	foo.myMethod(arg1, arg2, function(returnValue) {
	  // This callback will be invoked when myMethod has a return value. Keep in mind that
	  // the communication is asynchronous, hence the need for this callback.
	  console.log(returnValue);
	});

	// Read a property value, which is cached on the client side:
	console.log(foo.myProperty);

	// Writing a property will instantly update the client side cache.
	// The remote end will be notified about the change asynchronously
	foo.myProperty = "Hello World!";

	// To get notified about remote property changes,
	// simply connect to the corresponding notify signal:
	foo.onMyPropertyChanged.connect(function(newValue) {
	  console.log(newValue);
	});

	// One can also access enums that are marked with Q_ENUM:
	console.log(foo.MyEnum.MyEnumerator);
});
``` 
即，在js函数的最后一个参数之后，加上一个function, 返回值会以函数参数方式提供给该函数。
 
原因就是，这个通信过程是异步的，返回值不能直接返回。  

同时，只有能够被JSON序列化的数据类型可以传递到HTML端，所以Qt中函数的参数和返回值都是有要求的。  




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)