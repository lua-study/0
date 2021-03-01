## design pattern 参考《大话设计模式》
## [参考资料](http://blog.csdn.net/doleria/article/details/72617663)
将原作者项目自己敲了一遍，并添加了自己代码
## [原作者git地址](https://github.com/echoTheLiar/JavaCodeAcc.git) 

0. [设计原则](#0)
1. [简单工厂模式](#1)
2. [策略模式](#2)
3. [装饰模式](#3)
4. [代理模式](#4)
5. [原型模式](#5)
6. [模板方法模式](#6)
7. [外观模式](#7)
8. [建造者模式](#8)

 设计原则 


 
面对对象优势：（曹操吟诗-活字印刷术案例） 
    1.可维护 
    2.可复用 
    3.可扩展 
    4.灵活性好 
 
    1. 单一职责原则  
    如果一个类承担的职责过多，等于把这些职责耦合在一起，一个职责的变化可能会削弱或者抑制这个类完成其他职责的能力。 
    这种耦合会导致脆弱的设计，当变化发生时，设计会遭受到意想不到的破坏。 
    （例子：手机集合了照相功能，却比专门的照相机性能低） 
     
    2. 开发-分闭原则 
    对程序的改动是通过新增代码进行，而不是更改现有的代码 
     
    3. 依赖倒转原则 
    高层模块不应该依赖低层模块。两个都应该依赖抽象 
    抽象不应该依赖细节。细节应该依赖抽象 
 

    
    4. 里氏代换原则 
    子类型必须能够替换父类型 
    只有当子类能够替换掉父类，软件单位的功能不受影响时，父类才能真正被服用，而子类也能够在父类的基础上增加新的行为。 
    
    5. 迪米特法则 
    如果两个类不必彼此直接通信，那么这两个类就不应当发生直接的相互作用。如果其中的一个类需要调用另一个类的某一个方法的话，可以通过第三者转发这个调用。
     
    优势：在于降低类与类之间的耦合。由于每个类尽量减少对其他类的依赖，因此，很容易使得系统的功能模块功能独立，是的相互间存在尽可能少的依赖关系。
 

![image](https://note.youdao.com/yws/api/personal/file/85942E285E7842D3B5826D885CC39F47?method=download&shareKey=b88e1887b782bf99bf22c6a7c89cf476)

![image](https://note.youdao.com/yws/api/personal/file/B95BF583C190407D9AC6F16F368117F5?method=download&shareKey=c0df61ddd35c7f68dbb1c8f6f7919499)



 

- [简单工厂模式](./src/main/java/top/lfyao/designpattern/details/factory/simple/Calculator.java)

  ![image](https://note.youdao.com/yws/api/personal/file/F45E1C5511184669A7F42EB164DA7DA0?method=download&shareKey=52018f1dd838815195f2336ab7b9ca72)
  
 

- [策略模式](./src/main/java/top/lfyao/designpattern/details/strategy/Strategy.java)

    它定义了算法家族，分别封装起来，让它们之间可以互相替换，此模式让算法的变化，不会影响到使用算法的客户。策略模式就是用来封装算法的，但在实践中，我们发现可以用它来封装几乎任何类型的规则，只要在分析过程中听到需要在不同时间应用不同的业务规则，就可以考虑使用策略模式处理这种变化的可能性。
 
【组合：策略模式的Context很重要，在Context中组合Strategy成员对象，初始化Context时，选择适当的Strategy对象，调用对应Strategy对象的algorithmInterface()
 
  

    
 ![image](https://note.youdao.com/yws/api/personal/file/98A16514A8D7488AB185CFAB772E510F?method=download&shareKey=f4e5010decf0df8f477efaa73fa94bd4)
  
 
优势 
    1.为context定义了一系列可重用的算法或行为。继承有助于析出这些算法中的公共功能。 
    2.简化单元测试，因为每个算法都有自己的类，可以自己定义接口单独测试。
 

- [策略模式结合简单工厂模式](./src/main/java/top/lfyao/designpattern/details/factory/method/FactoryClient.java)
> 客户端只需要认识一个类algorithmContext就可以了，隐藏了工厂父类，耦合性更低


 

- [装饰模式](./src/main/java/top/lfyao/designpattern/details/decorator/DecoratorClient.java)
![image](https://note.youdao.com/yws/api/personal/file/BE84AB56C9474E29BA2BC4B1CA908810?method=download&shareKey=eba1f48fb786d85897c36e3d2ae631d6)

 

- [代理模式](./src/main/java/top/lfyao/designpattern/details/proxy/ProxyClient.java)

![image](https://note.youdao.com/yws/api/personal/file/01664672D885402884DA904F9463BA66?method=download&shareKey=da1b2def88aee08514306829b1ee35a8)


 

- [原型模式](./src/main/java/top/lfyao/designpattern/details/prototype/PrototypeClient.java)

 
用原型实例指定创建对象的种类，并且通过拷贝这些原型创建新的对象 
浅拷贝：实现Cloneable 重写clone方法 
深拷贝：对象序列化的方式  
 

 

- [模板方法模式](./src/main/java/top/lfyao/designpattern/details/template/AbstractTemplate.java)

 
定义一个操作中的算法的骨架，而将一些步骤延迟到子类中。模板方法使得子类可以不改变一个算法的结构即可重定义该算法的某些特定步骤。模板方法模式通过把不变行为搬移到超类，去除子类中的重复代码来体现它的优势。【继承+代码复用】
 
优势：通过把不变的行为搬移到超类，去除子类中重复的代码太体现优势。
 

![image](https://note.youdao.com/yws/api/personal/file/D0E1FAD3545A4BB182C559D8653D27C7?method=download&shareKey=4baf7f9a8d6ebb7930d60955b48af202)


 

- [外观模式](./src/main/java/top/lfyao/designpattern/details/facade/FacadeClient.java)

![image](https://note.youdao.com/yws/api/personal/file/04A8EB4FBC9747C889AD0CEDC988FEFD?method=download&shareKey=0cbef0c42c1b2d4082e7fdfe3ae83732)
![image](https://note.youdao.com/yws/api/personal/file/FBBF55FAF0644B4EA7FDEA03232595F5?method=download&shareKey=9c769d12e88307da1fafdde813fb16c4)


 

- [建造者模式](./src/main/java/top/lfyao/designpattern/details/builder/BuilderClient.java)


 
主要用于创建一些复杂的对象，这些对象内部构建间的建造顺序通常是稳定的，但对象的构建通常面临复杂的变化。 
好处：使建造代码与表示代码分离。 
 

![image](https://note.youdao.com/yws/api/personal/file/B419A5FA70E64B53874046D5D52074E9?method=download&shareKey=e61774d9badfac66e56477e6f65cbe82)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)