# 手动实现双向绑定，并理解原理及实现
Vue的双向绑定实现原理：由**数据劫持**结合**发布者-订阅者模式**实现的。

##数据劫持
通过Object.defineProperty()来劫持对象属性的setter和getter操作，在数据变动的时候做想做的事情。

### 理解对象及defineProperty
创建自定义的对象最简单的方式就是创建一个Object的实例，在为其添加属性和方法。
```javascript
var obj = new Object();
obj.name = 'Tom';
obj.age = 18;

obj.sayName = function () {
  console.log(this.name);
}

// 上面比较麻烦，后来改成字面量创建对象
var person = {
  name: 'Tom',
  age: 18,
  sayName: function () {
    console.log(this.name);
  }
}
```

**属性类型**

ECMA-262 第 5 版在定义只有内部才用的特性（attribute）时，描述了属性（property）的各种特征。ECMAScript中有两种属性：数据属性和访问器属性。

1. 数据属性:
   
    [[Configurable]]: 表示能否通过 delete 删除属性从而重新定义属性，能否修改属性的特性，或者能否把属性修改为访问器属性。像前面例子中那样直接在对象上定义的属性，它们的这个特性默认值为 true。

    [[Enumerable]]：表示能否通过 for-in 循环返回属性。像前面例子中那样直接在对象上定义的属性，它们的这个特性默认值为 true。

    [[Writable]]：表示能否修改属性的值。像前面例子中那样直接在对象上定义的属性，它们的这个特性默认值为 true。

    [[Value]]：包含这个属性的数据值。读取属性值的时候，从这个位置读；写入属性值的时候，把新值保存在这个位置。这个特性的默认值为 undefined。

    > 要修改属性默认的特性，必须使用ECMAScript5的Object.defineProperty()方法。接收三个参数：属性所在对象、属性名字和一个描述符对象。

![object.defineProperty](./img/J_2019-07-08_20-09-26.png)

    其中，**描述符(descriptor)**对象的属性必须是：configurable、enumerable、writable和 value。设置其中的一或多个值，可以修改对应的特性值。

  ```javascript
   var person = {};
   Object.defineProperty(person, 'name', {
     writable: false,
     value: 'Jerry'
   })

   console.log(person.name); // Jerry
   person.name = 'Jack';
   console.log(person.name); // Jerry

   // 创建了一个名为 name 的属性，它的值"Jerry"是只读的。这个属性的值是不可修改的，
   // 如果尝试为它指定新值，则在非严格模式下，赋值操作将被忽略；在严格模式下，
   // 赋值操作将会导致抛出错误。

  ```

2. 访问器属性

    [[Configurable]]：表示能否通过 delete 删除属性从而重新定义属性，能否修改属性的特性，或者能否把属性修改为数据属性。对于直接在对象上定义的属性，这个特性的默认值为true。

    [[Enumerable]]：表示能否通过 for-in 循环返回属性。对于直接在对象上定义的属性，这个特性的默认值为 true。

    [[Get]]：在读取属性时调用的函数。默认值为 undefined。

    [[Set]]：在写入属性时调用的函数。默认值为 undefined。

  ```javascript
  var obj = {
    _name: 'objName',
    characteristics: ''
  }

  Object.defineProperty(obj, 'name', {
    get: function() {
      return this._name;
    },
    set: function(newValue) {
      if(newValue) {
        this._name = newValue;
      }
    }
  })

  obj.name = 'Jack';
  console.log(obj.name); // Jack
  
  // 访问器属性 name 则包含一个getter 函数和一个 setter 函数。
  // getter 函数返回_name 的值，setter 函数通过计算，得到name应该设置的值。

  // 不一定非要同时指定 getter 和 setter。只指定 getter 意味着属性是不能写，尝试写入属性会被忽略。
  ```

> Object.defineProperties() 可以为对象定义多个属性。


## 使用Object.defineProperty()

```javascript
// 通过Object.defineProperty方式，在console.log(book.name)同时,直接给书加一个书号
var Book = {};
var name = '';
Object.defineProperty(Book,'name',{
  set:function(value) {
    name = value;
    console.log('你取了一个书名叫:' + value);
  },
  get:function() {
    console.log('get方法被监听到');
    return name;
  }
});
Book.name = '人性的弱点'; // 你取了一个书名叫:人性的弱点
console.log(Book.name); // ①get方法被监听到   ②人性的弱点
```
通过Object.defineProperty()这个方法设置了Book对象的name属性，对其get和set方法进行重写操作，get方法在获得name属性时被调用，set方法在设置name属性时被触发。所以在执行Book.name="人性的弱点"，这个语句时调用set方法，输出你取了一个书名叫：人性的弱点．当调用console.log(Book.name)时触发get方法，输出人性的弱点。


订阅者和发布者模式，通常用于消息队列中．一般有**两种形式来实现消息队列**：
+ 使用`生产者和消费者`来实现；
+ 使用`订阅者－发布者`模式来实现；
其中订阅者和发布者实现消息队列的方式，就会用订阅者模式。

所谓的订阅者，就像我们在日常生活中，订阅报纸一样。我们订阅报纸的时候，通常都得需要在报社或者一些中介机构进行注册。当有新版的报纸发刊的时候，邮递员就需要向订阅该报纸的人，依次发放报纸。
如果用代码实现该模式，需要进行两个步骤：

+ 初始化发布者、订阅者
+ 订阅者需要注册到发布者，发布者发布消息时，依次向订阅者发布消息。

## 实现过程

要想实现mvvm，主要包含两个方面:
+ 视图变化更新数据
+ 数据变化更新视图

data变化更新view的重点是如何知道view什么时候变化了，只要知道什么时候view变化了，那么接下来的就好处理了．

这个时候我们上文提到的Object.defineProperty()就起作用了．通过Object.defineProperty()对属性设置一个set函数，当属性变化时就会触发这个函数，所以我们只需要将一些更新的方法放在set函数中就可以实现data变化更新view了．

1. 实现一个监听器Observer，用来劫持并监听所有属性，如果有变动的，就通知订阅者`订阅者Watcher`,因为属性可能是多个，所以会有多个订阅者，故我们需要一个消息`订阅器Dep`来专门收集这些订阅者，并在监听器Observer和订阅者Watcher之间进行统一的管理。
2. 实现一个订阅者Watcher，可以收到属性的变化通知并执行相应的函数，从而更新视图。
3. 实现一个解析器Compile，对每个元素节点的指令进行扫描和解析，根据指令模板替换数据，以及绑定相应的更新函数。
4. mvvm入口函数，整合以上三者。

![流程图](./img/2.png)

## 实现监听器Observer
数据监听器的核心方法就是Object.defineProperty()，通过遍历循环对所有属性值进行监听，并对其进行Object.defineProperty()处理。
```javascript
// 对所有的属性都要监听，递归遍历所有属性。
function observer(data) {
  if (!data || typeof data !== 'object'){
    return;
  }

  // 遍历取出所有的属性
  Object.keys(data).forEach(key => {
    defineReactive(data, key, data['key']);
  })
}

function defineReactive(data, key, val) {
  observer(val); // 监听子属性
  Object.defineProperty(data, key, {
    enumerable: true, // 可枚举
    configurable: false, // 不能再define
    get: function() {
      return val;
    },
    set: function(newVal) {
      console.log('监听到值变化：'+val+' ---> '+newVal);
      val = newVal;
    }
  })
}

// 测试
// var obj = {name: 'Tom'};
// observer(obj);
// obj.name = 'Jerry'; // 监听到值变化：Tom ---> Jerry
```
通过observe()方法进行遍历向下找到所有的属性，并通过defineReactive()方法进行数据劫持监听。

在上面的思路中，我们需要一个可以容纳消息订阅者的消息订阅器Dep，订阅器主要收集消息订阅者，然后在属性变化时执行相应订阅者的更新函数，那么消息订阅器Dep需要有一个容器，用来存放消息订阅者．我们将上面的监听器Observer稍微修改一下：

```javascript
// Observer.js
// ...省略
Object.defineProperty(data, key, {
	get: function() {
		// 由于需要在闭包内添加watcher，所以通过Dep定义一个全局target属性，暂存watcher, 添加完移除
		Dep.target && dep.addDep(Dep.target);
		return val;
	}
    // ... 省略
});

// Watcher.js
Watcher.prototype = {
	get: function(key) {
		Dep.target = this;
		this.value = data[key];	// 这里会触发属性的getter，从而添加订阅者
		Dep.target = null;
	}
}
```
## 实现Compile
compile主要做的事情是解析模板指令，将模板中的变量替换成数据，然后初始化渲染页面视图，并将每个指令对应的节点绑定更新函数，添加监听数据的订阅者，一旦数据有变动，收到通知，更新视图。

因为遍历解析的过程有多次操作dom节点，为提高性能和效率，会先将vue实例根节点的el转换成文档碎片fragment进行解析编译操作，解析完成，再将fragment添加回原来的真实dom节点中。

```javascript
function Compile(el) {
  this.$el = this.isElementNode(el) ? el : document.querySelector(el);
  if (this.$el) {
    this.$fragment = this.node2Fragment(this.$el);
    this.init();
    this.$el.appendChild(this.$fragment);
  }
}
Compile.prototype = {
	init: function() { this.compileElement(this.$fragment); },
  node2Fragment: function(el) {
    var fragment = document.createDocumentFragment(), child;
    // 将原生节点拷贝到fragment
    while (child = el.firstChild) {
      fragment.appendChild(child);
    }
    return fragment;
  },
  compileElement: function(el) {
    var childNodes = el.childNodes, me = this;
    [].slice.call(childNodes).forEach(function(node) {
      var text = node.textContent;
      var reg = /\{\{(.*)\}\}/;	// 表达式文本
      // 按元素节点方式编译
      if (me.isElementNode(node)) {
        me.compile(node);
      } else if (me.isTextNode(node) && reg.test(text)) {
        me.compileText(node, RegExp.$1);
      }
      // 遍历编译子节点
      if (node.childNodes && node.childNodes.length) {
        me.compileElement(node);
      }
    });
  }
};

// 指令处理集合
var compileUtil = {
    text: function(node, vm, exp) {
        this.bind(node, vm, exp, 'text');
    },
    // ...省略
    bind: function(node, vm, exp, dir) {
        var updaterFn = updater[dir + 'Updater'];
        // 第一次初始化视图
        updaterFn && updaterFn(node, vm[exp]);
        // 实例化订阅者，此操作会在对应的属性消息订阅器中添加了该订阅者watcher
        new Watcher(vm, exp, function(value, oldValue) {
        	// 一旦属性值有变化，会收到通知执行此更新函数，更新视图
            updaterFn && updaterFn(node, value, oldValue);
        });
    }
};

// 更新函数
var updater = {
    textUpdater: function(node, value) {
        node.textContent = typeof value == 'undefined' ? '' : value;
    }
    // ...省略
};
```
这里通过递归遍历保证了每个节点及子节点都会解析编译到，包括了{{}}表达式声明的文本节点。指令的声明规定是通过特定前缀的节点属性来标记，如span v-text="content" other-attr中v-text便是指令，而other-attr不是指令，只是普通的属性。 监听数据、绑定更新函数的处理是在compileUtil.bind()这个方法中，通过new Watcher()添加回调来接收数据变化的通知。

至此，一个简单的Compile就完成了。

## 实现Watcher
Watcher订阅者作为Observer和Compile之间通信的桥梁，主要做的事情是:
1、 在自身实例化时往属性订阅器(dep)里面添加自己 
2、自身必须有一个update()方法 
3、待属性变动dep.notice()通知时，能调用自身的update()方法，并触发Compile中绑定的回调，则功成身退。

```javascript
function Watcher(vm, exp, cb) {
    this.cb = cb;
    this.vm = vm;
    this.exp = exp;
    // 此处为了触发属性的getter，从而在dep添加自己，结合Observer更易理解
    this.value = this.get(); 
}
Watcher.prototype = {
    update: function() {
        this.run();	// 属性值变化收到通知
    },
    run: function() {
        var value = this.get(); // 取到最新值
        var oldVal = this.value;
        if (value !== oldVal) {
            this.value = value;
            this.cb.call(this.vm, value, oldVal); // 执行Compile中绑定的回调，更新视图
        }
    },
    get: function() {
        Dep.target = this;	// 将当前订阅者指向自己
        var value = this.vm[exp];	// 触发getter，添加自己到属性订阅器中
        Dep.target = null;	// 添加完毕，重置
        return value;
    }
};
// 这里再次列出Observer和Dep，方便理解
Object.defineProperty(data, key, {
	get: function() {
		// 由于需要在闭包内添加watcher，所以可以在Dep定义一个全局target属性，暂存watcher, 添加完移除
		Dep.target && dep.addDep(Dep.target);
		return val;
	}
    // ... 省略
});
Dep.prototype = {
    notify: function() {
        this.subs.forEach(function(sub) {
            sub.update(); // 调用订阅者的update方法，通知变化
        });
    }
};
```

实例化Watcher的时候，调用get()方法，通过Dep.target = watcherInstance标记订阅者是当前watcher实例，强行触发属性定义的getter方法，getter方法执行的时候，就会在属性的订阅器dep添加当前watcher实例，从而在属性值有变化的时候，watcherInstance就能收到更新通知。

## 实现MVVM
MVVM作为数据绑定的入口，整合Observer、Compile和Watcher三者，通过Observer来监听自己的model数据变化，通过Compile来解析编译模板指令，最终利用Watcher搭起Observer和Compile之间的通信桥梁，达到数据变化 -> 视图更新；视图交互变化(input) -> 数据model变更的双向绑定效果。

一个简单的MVVM构造器是这样子：
```javascript
function MVVM(options) {
    this.$options = options;
    var data = this._data = this.$options.data, me = this;
    // 属性代理，实现 vm.xxx -> vm._data.xxx
    Object.keys(data).forEach(function(key) {
        me._proxy(key);
    });
    observe(data, this);
    this.$compile = new Compile(options.el || document.body, this)
}

MVVM.prototype = {
	_proxy: function(key) {
		var me = this;
        Object.defineProperty(me, key, {
            configurable: false,
            enumerable: true,
            get: function proxyGetter() {
                return me._data[key];
            },
            set: function proxySetter(newVal) {
                me._data[key] = newVal;
            }
        });
	}
};
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)