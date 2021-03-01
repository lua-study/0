cocos-py
============




wrap cocos2d-x (3.17.2) with python(3.7.0)  (第一版本先封装cocos，真正要更高效，应该直接把cocos模块整个使用pytypeobject的形式，但涉及渲染(opengl)流程不够熟悉)

已完成对基础cocos对象的封装


**对cocos源码的修改记录**：
-----------------------
  * cocos根目录下增加cocos-py封装python
    * python目录即python头文件及库目录
    * src底下
        * pycocos：封装cocos（也按2d/3d/base...目录形式）
        * pyscripts：python脚本层封装，主应用入口就是底下main.py
        * yourapp：就是你自己的业务，代码都放这里（目录均可更改，但对应需要在py_cocos2d.cpp修改）

  * 当前优先采用CLE的工具里面自带的[python3.7.0编译库](http://www.srplab.com/cn/files/products.html)

  * 修改TableViewCell，加入额外tag，应对复用cell的情况



**python交叉编译参考**：
-----------------------
 1. 参考github [QPython](https://github.com/yan12125/python3-android)编译过程 

 2. [python3.6移植](https://blog.csdn.net/whahu1989/article/details/86482669)

 3. 采用类似公共语言扩展CLE的方案，也是[crystax-ndk](https://blog.csdn.net/yingshukun/article/details/78571992) （依赖CLE第三方startcore等库）

 4. [3.7.1移植](http://blog.sina.com.cn/s/blog_67119e9a0102y31t.html)


**TODO**：
------

* python层如何封装更好（目前在写测试应用pytest时发现不够方便，经常异常时完全没有任何栈，需要自己try catch）
* scheduler参考lua封装的形式
* 引用计数问题
* python热更新
* 脚本启动顺序优化
* 脚本加密


```
python热更的思路：
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)