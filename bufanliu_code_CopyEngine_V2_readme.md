#CopyEngine_V2

---

### Contact

Eran : `iamzealotwang@126.com`  

QQ  :  `66840053`

### DevLog

**2015-1-6**

重构了List模块,使得List更容易初始化 并且更改了refresh方法

更改了List的DisplayObjectSharePool 目前和InfoTree绑死 返回的是一个buildResult 这样上层CellRender就可以获取到quickFindDic

**2015-1-5**

SceneBasic下面增加了挂在DisposableObject,可以把一些对象挂上面 场景切换时候自动卸载

CERes加载部分取消了先push到一个Vector里面 然后再push到Queue中的做法 可以直接Push到Queue里面

**2015-1-2**

实现了Polygon,用坐标点描述图形 从而达到在纹理图中的像素级碰撞检测,并且提供`getRandomPointInPolygon`方法

**2015-12-28**

实现了Sequence,和GreenSock的TimeLine类似不过可以挂在代码

**2015-12-25**

20:11:45 增加二进制格式的文件加载支持 和GAF格式的文件加载支持

**2015-12-23**

16:57:39 完成网络模块Socket部分,同时提供了一种数据包结构的解析(ZFB项目在使用)

**2015-12-22**

11:38:25 完成CEDialog

15:32:55 完成CEScene

**2015-12-21**

11:42:53 完成CEList

14:00:29 完成了通过`CEGuiUtils.getScrollPanel`方法获取ScrollPanel 同时提供对应的Utils帮助类`CEScrollPanelUtils`

15:16:02 完成了通过`CEGuiUtils.getList`方法获取List 同时提供对应的Utils帮助类`CEListUtils` 实现refreshDataProvider方法

17:19:19 初步完成了TextFiled支持,不过Starling和FLA里面的渲染不同 所以导致无法再FLA中很完美的所见即所得的方式编辑 后续在做优化

17:45:07 加入FNT支持,使用BMFont制作FNT,再将FNT的纹理和GUI纹理通过InfoTree打包在一起 可以大幅度降低RAW

**2015-12-19**

21:26:45 完成ScrollPanel

**2015-12-17**

10:47:03 完成CEMovieClip

12:10:55 完成S3,S9,PH

14:57:56 整理了InfoTreeBuild的Result, 增加了快速访问的Dic , 可以直接  
``var mc:* = result.getMc("root[name1][name2][name3]")``  的方式直接取得MC原件

15:57:33 完成了ColorFilterButton

16:25:27 完成了ColorFilterSelectableButton

17:03:22 完成了ColorFilterTabbar

18:24:58 完成了Mask 和 ChangeSize 的 Progress

**2015-12-16**

00:04:29 重新整理了CopyEngine的包结构 使得结构更清晰. 准备实现loadCEFileAndWillUseTexture函数,完成该函数后  
1· 在ZFB项目中用resProxy.getTextureFromAtlas(xxx,xxx)直接调用 看看是否可以从纹理中加载素材  
2· 实现函数buildDisplayObject函数 完成一个显示树的渲染(不包括TF,S3,S9,PH等)  
3· 实现S3,S9,PH  
4· 构建Component->Button  

18:01:17 完成目标1,2  可以加载资源且构建显示树(Sprite+Image)

**2015-12-3**

15:26:19 完成工具Folder2Json且配置好了批处理工具,可以实现FLA到最终的纹理+atlas+ce 一步到位

**2015-12-2**

12:32:13 初步完成InfoTree的流程, 可以手动的生成ce和atlas文件到相应的目录 下午制作InfoTreeMetaGenerator用于读读Atlas更新ce文件

20:59:04 完成InfoTree相关的工作流建立,完成IT_Fixer工具

**2015-12-1**

11:45:03 完成InfoTree的流程修改,目前导出png散图+直接压缩的meta文件

16:41:24 InfoTree中支持了S3和S9 TileRepeat后期再支持

19:28:53 S9在ZFB项目中可以用纯手写代码的方式构建出来


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)