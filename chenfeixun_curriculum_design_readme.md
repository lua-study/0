第九周
---
> 反射基本使用`

- 这里是列表文本获取Class类的三种方法:
1. 这里是列表文本类名.class
2. 这里是列表文本对象名.getClass()
3. 这里是列表文本Class.forName(“要加载的类名”)
根据API写就行了，大致流程就是:

用上述三种方式之一获取特定类的Class类，即该类对应的字节码
1. 这里是列表文本调用Class对象的getConstructor(Class ... parameterTypes)获取构造方法对象
2. 这里是列表文本调用是构造方法类Constructor的newInstance(Object... initargs)方法新建对象
3. 这里是列表文本调用Class对象的getMethod(String name, Class ... parameterTypes)获取方法对象
4. 这里是列表文本调用方法对象类Method的invoke(Object obj, Object... args)方法，调用对象上相应方法

本周看了一下反射，以及重看了mvc

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)