# laydatePro

#### 项目介绍
对laydate的强化。
实际上目前laydate的已经足够应对很多的业务场景，各方面总的来说还都是足够好的。
但是，足够好也不能说没有问题，比如，无法通过elem设置某一类节点的选择器来一次性渲染多个节点，
再比如无法通过再次render一个已经存在的节点在更新里面的设置，要修改已经渲染过的节点里面的设置，
这个目前基本非常麻烦而且有一些属性不是你麻烦不麻烦的问题是根本改不了，再比如想要加入自定义按钮，
再比如想要加入快速选择，再比如想要...，再比如想要...，再比如想要...，
相信或多或少都会遇到这样或那样的需求目前laydate实现不了的。

#### 插件说明
力求对源码laydate最小的改动，不会影响以前的逻辑代码的前提下加强laydate功能还有更方便的使用。
目前laydate.js只修改了render返回的数据中添加多一个属性，保存当前laydate的实例，
然后提供过一个laydatePro.js供引入，后面很多加强的逻辑都在laydatePro里面处理实现，
不会再对laydate做更多的修改，所以对以前的代码来说应该是没有什么不好的影响的。

#### 目前实现的一些功能：

1. 支持一次性render多个节点。
2. 支持render一个已经render过的节点。
3. 新增lay-data属性来设置当前节点的laydate的配置。
4. 实现快速选择时间的功能。（quickSelect）
5. 纯月份年份点击直接确定。（quickConfirm）
6. 不完整的时分秒选择。（simpleModel & format）
7. 分裂式时间范围选择。（rangeType & range）
8. 新增快速选择的两种场景支持。（range & quickSelect）
9. 新增季度选择（type:'quarter'）
10. 新增可以定义周n作为一周的开始（weekStart）
11. 支持this标记的背景为圆圈（circleMark）
12. 日期选择多选（multiple）
13. 销毁laydate（laydatePro.destory）

##### 测试页面：[https://sun_zoro.gitee.io/laydatepro/testLaydate.html](https://sun_zoro.gitee.io/laydatepro/testLaydate.html)


#### 使用说明

新版本已经对laydatePro.js进行了一个较大的结构修改，现在是一份代码就可以两用了，所以使用起来不会像上次那么麻烦。
如果使用的是layui完整版本的，需要替换的还是之前的两个js（laydate.js和layui.all.js），然后把release/laydatePro整文件夹拷贝到自己项目
的合适位置，use laydatePro即可，不用管css，css会在js被引入的时候自动的去加载，只要确保css和js是在同一目录下就好;
如果使用的是独立Laydate，那么下载release/laydate 这个里面的内容覆盖到自己的项目中的laydate的目录，也可以简单的指拷贝其中的laydate.js，
实际有修改的只有这个，然后laydatePro跟使用完整的layui的差不多，也是将release/laydatePro整文件夹拷贝到自己项目的合适位置，然后在需要用到
的时候在引入jquery和laydate之后引入laydatePro.js即可，同样无需关心样式文件，插件自己会去找到同一个目录下的需要的css文件。


#### 参与贡献

1. Fork 本项目
2. 新建 Feat_xxx 分支
3. 提交代码
4. 新建 Pull Request


#### 码云特技

1. 使用 Readme\_XXX.md 来支持不同的语言，例如 Readme\_en.md, Readme\_zh.md
2. 码云官方博客 [blog.gitee.com](https://blog.gitee.com)
3. 你可以 [https://gitee.com/explore](https://gitee.com/explore) 这个地址来了解码云上的优秀开源项目
4. [GVP](https://gitee.com/gvp) 全称是码云最有价值开源项目，是码云综合评定出的优秀开源项目
5. 码云官方提供的使用手册 [https://gitee.com/help](https://gitee.com/help)
6. 码云封面人物是一档用来展示码云会员风采的栏目 [https://gitee.com/gitee-stars/](https://gitee.com/gitee-stars/)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)