# Intellij IDEA代码检视插件/ Intellij IDEA CodeReview Plugin

```
业余时间写的Intellij IDEA的一个Code Review代码检视、代码评审的插件。
```

最近在搞代码Review，一直想找个简单易用、适合自己习惯的`Intellij IDEA`的代码检视插件，但是一直没找到。想起好几年前在HUAWEI使用过的一个Eclipse的code review插件的用起来挺顺手的，所以凭着脑海中一些零星的记忆，重新写了个Intellij IDEA上的Code Review插件。

借助此插件，可以`方便的在本地IDEA工具里面记录代码检视发现的问题或者需要备注的信息`，同时`支持将IDEA中的评审意见导出为Excel表格`，方便发送给其它同事导入到自己的IDEA中，实现双击跳转到对应的代码位置，进行问题的确认。

**主要功能：**
  * Alt+A快速添加注释
  * 行号旁边图标标识有检视意见的位置
  * 支持双击评审意见跳转到代码对应位置
  * 支持对评审意见的删除、修改
  * 支持评审意见内容导出为Excel表格
  * 支持将导出的Excel表格中的评审意见导入到IDEA中进行查看与管理。

**后续计划**
  * 增加个网络交互能力、如果有空的话~~
  * 增加更细致的报表统计、如果有空的话~~~


**使用方法&效果图演示如下：**

![](assets/post_pics/README.md/use_guide_showcase.gif)


**安装方法**

```
导航到 File | Settings | Plugins 页面，点击 Install plugin from disk
```

![](assets/post_pics/README.md/install_local_plugin_showcase.gif)

**功版本变更记录：**

* **V1.0.0版本，2019-10-03更新：**
  1. 支持Alt+A快速添加选中代码部分的评审意见
  2. 支持添加了评审意见的地方，在代码的左侧窗口行号旁边显示一个图标标识
  3. 支持双击评审意见，直接跳转到代码对应位置
  4. 支持评审意见导出Excel表格


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)