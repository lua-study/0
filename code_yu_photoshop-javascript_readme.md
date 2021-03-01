# Photoshop 脚本参考文档中文翻译
 参考地址 
 	
			
 这篇文章是 Adobe 官方发布的&nbsp;《 Photoshop CC 2015 JavaScript Reference 》的常用部分的汉化版，增加了少量官方文档没有提及的属性。适用于入门者查阅，为此有一些补充，并附有&nbsp;PhotoShop 中相应的功能截图，希望初学者能够快速入门，并学会参考官方文档。 
 没有接触过&nbsp;ExtendScript 的请参考上一篇： 「 5 」 Photoshop ExtendScript 入门 &nbsp;来阅读。 
 本文尚未完结，不定期修改扩充中。 
  图层与图层组  
 Layer 与&nbsp;ArtLayer 都是图层，在&nbsp;PhotoShop CC 2015 以后是等效的概念。 
 而在使用上有一个区别： 
 在  Document.artLayers  中的  artLayers  是文档根目录的图层的集合。 
而  Document.layers  是所有图层和图层组的集合。 
 而画板是一个特殊的图层组。 
 比如下面这个文档： 
  查看图片  
  通过&nbsp;  app.activeDocument.artLayers[0]  和  [1]  可以获得图层 5 和图层 4，而&nbsp; app.activeDocument.layers &nbsp;除此之外还有  [2]  可以获得画板 1。 
  &nbsp;artLayer 对象  
  属性  
  kind　  LayerKind  
 图层类型。 
 
 
 
 LayerKind 
 
 
 LayerKind.NORMAL 
 普通 
 
 
 LayerKind.TEXT 
 文本 
 
 
 LayerKind.SMARTOBJECT 
 智能对象 
 
 
 LayerKind.SOLIDFILL 
 填充形状 
 
 
 LayerKind.VIDEO 
 视频 
 
 
 LayerKind.LAYER3D 
 3D 图层 
 
 
 填充或调整图层： 
 
 
 LayerKind.BLACKANDWHITE 
 黑白 
 
 
 LayerKind.BRIGHTNESSCONTRAST 
 明度对比 
 
 
 LayerKind.CHANNELMIXER 
 通道混合器 
 
 
 LayerKind.COLORBALANCE 
 色彩平衡 
 
 
 LayerKind.COLORLOOKUP 
 色彩查找 
 
 
 LayerKind.CURVES 
 曲线 
 
 
 LayerKind.EXPOSURE 
 曝光 
 
 
 LayerKind.GRADIENTFILL 
 渐变填充 
 
 
 LayerKind.GRADIENTMAP 
 渐变映射 
 
 
 LayerKind.HUESATURATION 
 色相饱和度 
 
 
 LayerKind.INVERSION 
 反相 
 
 
 LayerKind.PATTERNFILL 
 图案填充 
 
 
 LayerKind.PHOTOFILTER 
 照片滤镜 
 
 
 LayerKind.POSTERIZE 
 色调分离 
 
 
 LayerKind.SELECTIVECOLOR 
 可选颜色 
 
 
 LayerKind.THRESHOLD 
 阈值 
 
 
 LayerKind.LEVELS 
 色阶 
 
 
 LayerKind.VIBRANCE 
 自然饱和度 
 
 
 

  opacity   number  
 不透明度。图层的不透明属性（0~100）。 
  fillOpacity   number  
 填充不透明度。图层的填充属性（0~100）。 
  visible   boolean  
 可视性。 
  查看图片  

  linkedLayers   ArtLayer 或 LayerSet 数组  
 图层链接，只读。 
  查看图片  
  itemIndex   number  
 内部索引号。图层在 PhotoShop 内部的的索引号，无关图层组嵌套。序号从下至上递增，背景图层为 1。图层组与图层相同，也有一个索引号。 

   allLocked&nbsp;   boolean  
 图层锁定全部。true 为锁定。完全不能选中和编辑图层。 
  查看图片  
  pixelsLocked&nbsp;  boolean  
 图层像素锁定。true 为锁定。无法编辑图层像素，但可以移动图层位置。 
   
  positionLocked&nbsp;  boolean  
 图层位置锁。true 为锁定。无法移动图层位置。 
  查看图片  
  transparentPixelsLocked&nbsp;  boolean  
 图层透明度锁。true 为锁定。无法改变图层透明度。 
  查看图片  
  grouped   boolean  
 剪贴蒙版组，设置为&nbsp;true ，当前图层就为把下一个图层作为剪切蒙版。 
  查看图片  
  bounds    UnitValue  数组  
 图层区域。 只读。 [0,1,2,3] 分别是 0:左侧左边距 ，1:顶侧顶边距 ，2:右侧左边距 ，3:底侧顶边距。 
  查看图片  
  boundsNoEffects    UnitValue  数组  
 不包括样式（比如阴影）的图层区域。 
  filterMaskDensity   double  
 滤镜蒙版 浓度（0.0 ~100.0）。 
  查看图片  
  filterMaskFeather   double  
 滤镜蒙版 羽化（0.0 ~ 250.0）。 
  layerMaskDensity   double  
 图层蒙版 浓度（0.0 ~100.0）。 
  layerMaskFeather   double  
 图层蒙版 羽化（0.0 ~ 250.0）。 
  vectorMaskDensity   double  
 矢量蒙版 浓度（0.0 ~100.0）。 
  vectorMaskFeather   double  
 矢量蒙版 羽化（0.0 ~ 250.0）。 
  isBackgroundLayer   boolean  
 是否为背景图层，为这把图层转换为背景图层，并把图层放到最底层，如果已有背景图层，设置此属性会失败。 
  查看图片  
  textItem   TextItem  
 文本项。 
  blendMode    BlendMode   
  混合模式 。 
  xmpMetadata   xmpMetadata  
 XMP 元数据。 
  
  方法  
  adjustBrightnessContrast(&nbsp; 亮度, 对比度&nbsp; )  
 调整亮度、对比度。相当于“使用旧版”的亮度/对比度调节。（范围： -100~100） 
  查看图片  
  adjustColorBalance(&nbsp; [阴影], [中间调], [高光] , 保持明度 &nbsp;  )  
 调整色彩平衡。前三个参数放入色彩平衡值的数组，分别调整阴影、中间调、高光的平衡，最后一个参数为真即为保持明度。（范围： -100~100） 
  app.activeDocument.artLayers[0].adjustColorBalance([0,0,0], [2,-23,22], [0,0,0], true)  
 &nbsp; 查看图片  
  adjustCurves(  [曲线坐标数组]  )  
 图层的曲线调节。参数是一个数组，其中可以有最多 14 组坐标，表示曲线的点。每组坐标 [x,y] 的 x 对应曲线面板中的输入，y 对应输出。 
  app.activeDocument.artLayers[0].adjustCurves([[0,0], [149,58], [255,255]])  
  查看图片  
  adjustLevels(&nbsp; 输入开始位置, 输入结束位置, 输入 Gamma 值, 输出开始位置, 输出结束位置  )  
 调整色阶。 
  app.activeDocument.artLayers[0].adjustLevels(37, 255, 0.46, 63, 174)  
 &nbsp; 查看图片  
  applyAddNoise(  数量, 分布方式, 单色  )  
 添加杂色（滤镜）。数量参数范围： 0~400，分布方式使用常数  NoiseDistribution.GAUSSIAN  和  NoiseDistribution.UNIFORM ，分别代表高斯分布和平均分布，单色为真时产生无单色杂色。 
  查看图片  
  applyAverage()  
 应用“模糊-平均”滤镜。 
  applyBlur()  
 应用“模糊-模糊”滤镜。 
  applyClouds ()  
 应用“渲染-云彩”滤镜。 
  applyCustomFilter(  [特征值数组], 缩放, 位移  )  
 应用“其他-自定”滤镜。 
  查看图片  
  applyDeInterlace(  消除方式, 创建新场方式  )  
 应用“视频-逐行…” 滤镜 
 消除方式： 

 
 
 
 
  
  
 
 
 EliminateFields.EVENFIELDS 
 偶数行 
 
 
 EliminateFields.ODDFIELDS 
 奇数行 
 
 
 
 
 创建新场方式： 

 
 
 
 
  
  
 
 
 CreateFields.DUPLICATION 
 复制 
 
 
 CreateFields.INTERPOLATION 
 插值 
 
 
 
 
  查看图片  
  applyDespeckle()  
 应用”杂色-去斑”滤镜 
  applyDifferenceClouds()  
 应用“渲染-分层彩云”滤镜。 
  applyDiffuseGlow(  粒度, &nbsp;发光量, &nbsp;清除数量  )  
 应用”滤镜库-扭曲-扩撒亮光”滤镜。 
  查看图片  
  autoContrast()  
 自动对比度。 
  autoLevels()  
 自动色调。 
  clear()  
 清除图层内容，如果是形状图层将会删除本图层，如果是智能对象将会报“无法删除”错误。 
  copy(  混合  )  
 复制图层内容。混合参数为真会复制所有图层可见内容。 
  cut()  
 剪切图层。 
  desaturate()  
 去色。 
  duplicate(  相对图层\组,  相对位置   )  
 创建一个图层副本， 可不传入参数，将副本放在原件之后。此外还可以用参数控制创建的副本在图层面板中的位置，新的副本创建在相对图层\组的 相对位置 。 
 
 
 
  
  
 
 
 ElementPlacement.INSIDE 
 插入图层组 
 
 
 ElementPlacement.PLACEATBEGINNING 
 图层组首位 
 
 
 ElementPlacement.PLACEATEND 
 图层组末位 
 
 
 ElementPlacement.PLACEBEFORE 
 之前 
 
 
 ElementPlacement.PLACEAFTER 
 之后 
 
 
 
  app.activeDocument.artLayers[0].duplicate(app.activeDocument.layers[1], ElementPlacement.INSIDE)  
 &nbsp; 查看图片  
  equalize()  
 色调均化。 
  invert()  
 反相。 
  link(  连接目标  )  
 与连接目标创建图层连接，连接目标可以是图层或图层组。 
  app.activeDocument.artLayers[0].link( app.activeDocument.artLayers[1] )  
 &nbsp; 查看图片  
  merge()  
 向下合并图层，返回值为合并后的图层。 

  mixChannels(  [输出通道数组] , 单色  )  
 通道混合器。第一个参数是输出通道数组：[[红] , [绿] , [蓝]]（当图像是 CMYK 则是相应的 CMYK 通道），没一个通道也是一个数组，分别是红色、绿、蓝和常数。如果单色参数为真，就只需一组灰度通道参数。 
  //非单色
app.activeDocument.artLayers[0].mixChannels([[100, 100,110,115], [100, 100,110,115], [100, 100,110,115] ],flase)
// 单色：
app.activeDocument.artLayers[0].mixChannels([[100, 100,110,115]],true)  
 &nbsp; 查看图片  
  move(  相对图层\组,  相对位置   )  
 移动图层在面板中的位置。 
  app.activeDocument.artLayers[0].move(app.activeDocument.artLayers[2], ElementPlacement.PLACEBEFORE)  
  photoFilter(  填充颜色, 浓度, 保留明度  )  
 照片滤镜。 
  查看图片  
  var c = new SolidColor()
c.rgb.hexValue="ff0000"
app.activeDocument.artLayers[0].photoFilter(c,25,true )  
  posterize(  色阶  )  
 色调分离 。（1~100） 
  查看图片  
  rasterize(  目标  )  
 栅格化图层，目标可以为： 
 
 
 
  
  
 
 
 RasterizeType.ENTIRELAYER 
 栅格化图层 
 
 
 RasterizeType.FILLCONTENT 
 栅格化填充内容（生成矢量蒙版） 
 
 
 RasterizeType.LAYERCLIPPINGPATH 
 栅格化矢量蒙版 
 
 
 RasterizeType.TEXTCONTENTS 
 栅格化文字 
 
 
 RasterizeType.LINKEDLAYERS 
 栅格化链接的图层 
 
 
 RasterizeType.SHAPE 
 栅格化形状 
 
 
 
  remove()  
 删除图层。 
  resize(  水平位置, 垂直位置,  描点位置   )  
 重设图层尺寸，锚点位置即为不动点的位置 查看图片 ，在手动使用 PS 的自由变换工具时，鼠标操作点的对点，就是缩放的锚点。锚点参数可空，缺省值是正中。 锚点位置 。 
  查看图片  
  rotate(  角度 , 描点位置  )  
 旋转。顺时针旋转。 
  查看图片  

  selectiveColor(  方法, [红色], [黄色], [绿色], [青色], [蓝色], [洋红], [白色], [中性色], [黑色]  )  
 可选颜色，方法参数可为： 
 
 
 
 AdjustmentReference.ABSOLUTE 
 绝对 
 
 
 AdjustmentReference.RELATIVE 
 相对 
 
 
 
 每个颜色的参数为 [C, M, Y, K] 颜色数组(-100~100) 
  查看图片  
  shadowHighlight(  阴影数量, 色调, 阴影半径, 高光数量, 高光色调, 高光半径, 调整颜色, 调整中间调, 调整修剪黑色, 调整修正白色  )  
 阴影/高高。 
  查看图片  
  threshold(  阈值色阶  )  
 阈值。（1~255） 
  查看图片  
  translate(  X 偏移值 , Y 偏移值 )  
 移动，移动图层位置。 
 其偏移值是 UnitValue 类型。 
  var X =UnitValue("22 mm")
var Y =UnitValue("44 mm")
app.activeDocument.artLayers[0].translate(X , Y);
  
 或者直接使用整数，其单位将是首选项的标尺单位设置： 
  app.activeDocument.activeLayer.translate(22, 256);  
  查看图片  
  unlink()  
 取消图层链接。 

  LayerSet  
 图层组。图层组很多属性和方法都和图层一样，所以可以参考图层中的用法。图层组的关键是它和  docment  一样有&nbsp; artLayers 、 layerSets  和&nbsp; layers &nbsp;三个合集，用它们遍历图层组中的嵌套的图层和图层组。 
  属性  
  allLocked&nbsp;  boolean  
 图层组锁定全部。true 为锁定。完全不能选中和编辑图层。 
  blendMode&nbsp;   BlendMode   
 混合模式。 
  artLayers&nbsp;  ArtLayers  
 图层组中的图层。不包括图层组和图层组中的图层。 
  layers&nbsp;  Layers  
 图层和图层组的合集。 
  layerSets   LayerSets  
 图层组的合集。 
  itemIndex   number  
 内部索引号。图层组在 PhotoShop 内部的的索引号，无关图层组嵌套。序号从下至上递增，背景图层为 1。图层组与图层相同，都有一个索引号。 
  linkedLayers   ArtLayer 或 LayerSet 数组  
 图层链接，只读。 
  查看图片  
  name&nbsp;  string  
 名称。 
  opacity&nbsp;  number  
 不透明度（0-100）。 
  visible&nbsp;  boolean  
 是否可视。 
  enabledChannels&nbsp;  Channel 数组  
 启用通道。 
  方法  
  LayerSet   duplicate(  相对图层\组,  相对位置   )  
 创建一个图层组副本。可不传入参数，将副本放在原件之后。此外还可以用参数控制创建的副本在图层面板中的位置，新的副本创建在相对图层\组的 相对位置 。 
 
 
 
 &nbsp;ElementPlacement 
 
 
 ElementPlacement.INSIDE 
 插入图层组 
 
 
 ElementPlacement.PLACEATBEGINNING 
 图层组首位 
 
 
 ElementPlacement.PLACEATEND 
 图层组末位 
 
 
 ElementPlacement.PLACEBEFORE 
 之前 
 
 
 ElementPlacement.PLACEAFTER 
 之后 
 
 
 
  link(  连接目标  )  
 与连接目标创建图层连接，连接目标可以是图层或图层组。 
  unlink()  
 取消图层链接。 
  merge()  
 向下合并图层，返回值为合并后的图层。 
  move(  相对图层\组,  相对位置   )  
 移动图层组在图层面板中的位置。 
 remove() 
 删除图层组。 
  resize(  水平位置, 垂直位置,  描点位置   )  
 重设图层尺寸。锚点位置即为不动点的位置 查看图片 ，在手动使用 PS 的自由变换工具时，鼠标操作点的对点，就是缩放的锚点。锚点参数可空，缺省值是正中。 锚点位置 。 
  rotate(  角度 , 描点位置  )  
 旋转。顺时针旋转。 
  translate(  X 偏移值 , Y 偏移值 )  
 移动，移动图层位置。 


  文本与字体  
  TextItem  
  属性  
  contents   string  
 文本内容。 
  color    SolidColor   
 文本颜色。 
  position　    UnitValue  数组  
 文本框位置，以 UnitValue 数组形式表示：[X, Y]
   查看图片  
  size     UnitValue   
 字体大小 
  alternateLigatures   boolean  
 自由连字。 
  查看图片  
  antiAliasMethod   AntiAlias  
 消除锯齿方式。 
 
 
 
  
  
 
 
 AntiAlias.CRISP 
 犀利 
 
 
 AntiAlias.NONE 
 无 
 
 
 AntiAlias.SHARP 
 锐利 
 
 
 AntiAlias.SMOOTH 
 模糊 
 
 
 AntiAlias.STRONG 
 浑厚 
 
 
 
 Winodws 或 Winodws LCD 方式需要使用 ActionDescriptor ： 
  var idsetd = charIDToTypeID( "setd" );
    var desc = new ActionDescriptor();
    var idnull = charIDToTypeID( "null" );
        var ref = new ActionReference();
        var idPrpr = charIDToTypeID( "Prpr" );
        var idAntA = charIDToTypeID( "AntA" );
        ref.putProperty( idPrpr, idAntA );
        var idTxLr = charIDToTypeID( "TxLr" );
        var idOrdn = charIDToTypeID( "Ordn" );
        var idTrgt = charIDToTypeID( "Trgt" );
        ref.putEnumerated( idTxLr, idOrdn, idTrgt );
    desc.putReference( idnull, ref);
    var idT = charIDToTypeID( "T   " );
    var idAnnt = charIDToTypeID( "Annt" );
    //antiAliasPlatformGray 是“Windows”，antiAliasPlatformLCD 是“Windows LCD”
    var idantiAliasPlatformLCD = stringIDToTypeID( "antiAliasPlatformLCD" );
    desc.putEnumerated( idT, idAnnt, idantiAliasPlatformLCD );
executeAction( idsetd, desc, DialogModes.NO );  
  autoKerning   AutoKernType  
 字距调整，调整两个字符间距微调。 
 
 
 
  
  
 
 
 AutoKernType.MANUAL 
 手动指定 
 
 
 AutoKernType.METRICS 
 度量标准 
 
 
 AutoKernType.OPTICAL 
 视觉 
 
 
 
  查看图片  
  useAutoLeading   boolean  
 使用自动行距。 
  app.activeDocument.artLayers[0].textItem.useAutoLeading=false  
  查看图片  
  autoLeadingAmount   number  
 自动行距数量。 [0.01 ~ 5000.00]
 
  baselineShift    UnitValue   
 基线偏移。 
  查看图片  
  capitalization   TextCase  
 大写化。 
 
 
 
  
  
 
 
 TextCase.NORMAL 
 正常 
 
 
 TextCase.ALLCAPS 
 全部大写 
 
 
 TextCase.SMALLCAPS 
 小型大写字母 
 
 
 
  查看图片  
  desiredGlyphScaling   number  
 字符缩放期望（50~200），用于 2 侧对齐时。 
  desiredLetterScaling&nbsp;  number  
 字距缩放期望（100~500），用于 2 侧对齐时。 
  direction   Direction  
 文本取向。 
 
 
 
  
  
 
 
 Direction.HORIZONTAL 
 水平 
 
 
 Direction.VERTICAL 
 垂直 
 
 
 
  fauxBold   boolean  
 仿粗体。 
  fauxItalic   boolean  
 仿斜体。 
  firstLineIndent    UnitValue  (pt)  
 首行缩进，单位是 pt 。 
  查看图片  
  font   string  
 字体。指定字体的 postScriptName 名称。 
  hangingPunctuation   boolean  
 标点悬挂，标点符号位置能否超出文本框范围 
标点悬挂为真： 
  查看图片  
 标点悬挂为假： 
  查看图片  

  height    UnitValue   
 文本框高度。 
  width   UnitValue  
 文本框宽度 
  horizontalScale   number  
 水平缩放 （0~1000）。 
  查看图片  
  hyphenation   boolean  
 换行时使用连字符。 
  hyphenateCapitalWords   boolean  
 允许换行时对大写单词使用连字符。 
  hyphenateAfterFirst   number  
 换行符后可以有多少字（1~15）。 
  hyphenateBeforeLast   number  
 换行符前可以有多少字（1~15）。 
  hyphenationZone     UnitValue   
 行末到令文本不能对齐的字的距离 （0~720 pc 派卡 ）。 
  hyphenLimit   number  
 连接符可连接最大字数。 
  justification   Justification  
 段落对齐方式： 
 
 
 
  
  
 
 
 Justification.LEFT 
 左对齐 
 
 
 Justification.CENTER 
 居中 
 
 
 Justification.RIGHT 
 右对齐 
 
 
 Justification.LEFTJUSTIFIED 
 两侧对齐，最后一行左对齐 
 
 
 Justification.CENTERJUSTIFIED 
 两侧对齐，最后一行居中 
 
 
 Justification.RIGHTJUSTIFIED 
 两侧对齐，最后一行右对齐 
 
 
 Justification.FULLYJUSTIFIED 
 两侧对齐，全部对齐 
 
 
 
  查看图片  
  kind   TextType  
 文本类型 
 
 
 
  
  
 
 
 TextType.PARAGRAPHTEXT 
 段落文字，文本框 
 
 
  查看图片  
 
 
 TextType.POINTTEXT 
 点文本，没有文本框 
 
 
  查看图片  
 
 
 
 language  Language  
 文本语言，很多不支持。 
 
 
 
  
  
 
 
 Language.BRAZILLIANPORTUGUESE 
 巴西葡萄牙语 
 
 
 Language.CANADIANFRENCH 
 加拿大法语 
 
 
 Language.DANISH 
 丹麦语 
 
 
 Language.DUTCH 
 荷兰语 
 
 
 Language.ENGLISHUK 
 英式英语 
 
 
 Language.ENGLISHUSA 
 美式英语 
 
 
 Language.FINNISH 
 芬兰语 
 
 
 Language.FRENCH 
 法语 
 
 
 Language.GERMAN 
 德语 
 
 
 Language.ITALIAN 
 意大利语 
 
 
 Language.NORWEGIAN 
 挪威语 
 
 
 Language.NYNORSKNORWEGIAN 
 新挪威语 
 
 
 Language.OLDGERMAN 
 古德语 
 
 
 Language.PORTUGUESE 
 葡萄牙语 
 
 
 Language.SPANISH 
 西班牙语 
 
 
 Language.SWEDISH 
 瑞典语 
 
 
 Language.SWISSGERMAN 
 瑞士德语 
 
 
 
  leading     UnitValue   
 行距。 
  查看图片  
  leftIndent     UnitValue   
 左缩进（-1296~1296 pt）。无法设置 
  查看图片  
  rightIndent     UnitValue   
 右缩进（-1296~1296 pt）。无法设置 
  ligatures   boolean  
 使用连字 
  spaceAfter  UnitValue 
 断后添加空格（-1296~1296 pt）。无法设置 
  查看图片  
  spaceBefore  UnitValue 
 断前添加空格（-1296~1296 pt）。无法设置 
  maximumGlyphScaling   number  
 最大字符缩放（50~200）。在两端对齐时，字符的最大可缩放大小，为 100 时不缩放。 
  minimumGlyphScaling   number  
 最小字符缩放（50~200）。 
  查看图片  
  maximumLetterScaling   number  
 最大单词中缩放（0~500）。在两端对齐时，单词中最大的可拉伸距离，如果为 0 ，则不拉伸单词中的距离，而是全部由单词间的空格填补距离。 
  minimumLetterScaling   number  
 最小单词中缩放（0~500）。 
  查看图片  
  maximumWordScaling   number  
 最大单词间缩放（0~1000）。在两端对齐时，单词间最大的可拉伸距离。 
  minimumWordScaling&nbsp; number   
 最小单词间缩放（0~1000）。 
  noBreak   boolean  
 不自动换行 
  oldStyle   boolean  
 使用老样式 
  underline   UnderlineType  
 下划线，在垂直方向的文本框中可以控制下划线左右方向。水平方向的文本框两种常量没有区别。 
 
 
 
  
  
 
 
 UnderlineType.UNDERLINELEFT 
 左下划线 
 
 
 UnderlineType.UNDERLINERIGHT 
 右下划线 
 
 
 UnderlineType.UNDERLINEOFF 
 无下划线 
 
 
 
 左下划线与右下划线： 
  查看图片   查看图片  
  strikeThru   StrikeThruType  
 删除线。 
 
 
 
  
  
 
 
 StrikeThruType.STRIKEBOX 
 偏上 
 
 
  查看图片  
 
 
 StrikeThruType.STRIKEHEIGHT 
 中间 
 
 
  查看图片  
 
 
 StrikeThruType.STRIKEOFF 
 无删除线 
 
 
 

  textComposer  TextComposer 
 文本处理器，影响换行断字和对齐方法 
 
 
 
  
  
 
 
 TextComposer.ADOBEEVERYLINE 
 &nbsp;Adobe 每行 
 
 
 TextComposer.ADOBESINGLELINE 
 Adobe 单一行 
 
 
 

  tracking   number  
 字距调整值（-1000~10000）。 
  查看图片  
  useAutoLeading   boolean  
 自动行距，使用字体自带的行距信息 
  verticalScale   number  
 垂直缩放（0~1000） 
  查看图片  
  warpStyle   WarpStyle  
 变形文字，样式。 
 
 
 
  
  
  查看图片  
 
 
 WarpStyle.NONE 
 无 
 
 
 WarpStyle.ARC 
 扇形 
 
 
 WarpStyle.ARCLOWER 
 下弧 
 
 
 WarpStyle.ARCUPPER 
 上弧 
 
 
 WarpStyle.ARCH 
 拱形 
 
 
 WarpStyle.BULGE 
 凸起 
 
 
 WarpStyle.SHELLLOWER 
 贝壳 
 
 
 WarpStyle.SHELLUPPER 
 花冠 
 
 
 WarpStyle.FLAG 
 旗帜 
 
 
 WarpStyle.WAVE 
 波浪 
 
 
 WarpStyle.FISH 
 鱼形 
 
 
 WarpStyle.RISE 
 增加 
 
 
 WarpStyle.FISHEYE 
 鱼眼 
 
 
 WarpStyle.INFLATE 
 膨胀 
 
 
 WarpStyle.SQUEEZE 
 挤压 
 
 
 WarpStyle.TWIST 
 扭转 
 
 
 
  warpBend  number 
 弯曲（-100~100），变形文字的弯曲选参数。 
  查看图片  
  warpDirection    Direction   
 变形文字方向 
 
 
 
  
  
 
 
 Direction.HORIZONTAL 
 水平 
 
 
 Direction.VERTICAL 
 垂直 
 
 
 
  warpHorizontalDistortion   number  
 变形文字， 水平扭曲（-100~100）. 
  warpVerticalDistortion   number  
 变形文字， 垂直扭曲（-100~100）. 
  方法  
  convertToShape()  
 转换为形状。 
  createPath()  
 创建工作路径。 

  宿主与文档  
  Application  
  属性  
  activeDocument   Document  
 当前文档。 
  backgroundColor   SolidColor  
 背景颜色。 
  查看图片  
  foregroundColor   SolidColor  
 前景颜色。 
  build   string  
 宿主程序信息。 
如： 16.1.2 (2015.1.2 20160113.r.355 2016/01/13:23:59:59 CL 1059143)  
  colorSettings   string  
 颜色设置。即为 PS 的菜单：“编辑-颜色设置-设置”。 
  查看图片  
  currentTool   string  
 当前工具，如“artboardTool”（画板工具）。 
  工具名称列表  
 
 
 
  
  
 
 
 moveTool 
 移动工具 
 
 
 artboardTool 
 画板工具 
 
 
 marqueeRectTool 
 矩形选框工具 
 
 
 lassoTool 
 套索工具 
 
 
 quickSelectTool 
 快速选择工具 
 
 
 cropTool 
 剪裁工具 
 
 
 sliceTool 
 切片工具 
 
 
 sliceSelectTool 
 切片选择工具 
 
 
 eyedropperTool 
 吸管工具 
 
 
 colorSamplerTool 
 颜色取样器工具 
 
 
 rulerTool 
 标尺工具 
 
 
 paintbrushTool 
 画笔工具 
 
 
 pencilTool 
 铅笔工具 
 
 
 eraserTool 
 橡皮擦工具 
 
 
 bucketTool 
 油漆桶工具 
 
 
 gradientTool 
 渐变工具 
 
 
 typeCreateOrEditTool 
 横排文字工具 
 
 
 typeVerticalCreateOrEditTool 
 直排文字工具 
 
 
 typeVerticalCreateOrEditTool 
 钢笔工具 
 
 
 typeVerticalCreateOrEditTool 
 自由钢笔工具 
 
 
 addKnotTool 
 添加锚点工具 
 
 
 deleteKnotTool 
 删除锚点工具 
 
 
 convertKnotTool 
 转换点工具 
 
 
 directSelectTool 
 直接选择工具 
 
 
 pathComponentSelectTool 
 路径选择工具 
 
 
 rectangleTool 
 矩形工具 
 
 
 polygonTool 
 多边形工具 
 
 
 roundedRectangleTool 
 圆角矩形工具 
 
 
 ellipseTool 
 椭圆工具 
 
 
 customShapeTool 
 自定形状工具 
 
 
 handTool 
 抓手工具 
 
 
 handTool 
 缩放工具 
 
 
 marqueeEllipTool 
 椭圆选框工具 
 
 
 marqueeSingleRowTool 
 单行选框工具 
 
 
 marqueeSingleColumnTool 
 单列选框工具 
 
 
 polySelTool 
 多边形套索工具 
 
 
 magneticLassoTool 
 磁性套索工具 
 
 
 perspectiveCropTool 
 透视裁剪工具 
 
 
 spotHealingBrushTool 
 污点修复画笔工具 
 
 
 magicStampTool 
 修复画笔工具 
 
 
 patchSelection 
 修补工具 
 
 
 recomposeSelection 
 内容感知移动工具 
 
 
 redEyeTool 
 红眼工具 
 
 
 cloneStampTool 
 仿制图章工具 
 
 
 patternStampTool 
 图案图章工具 
 
 
 backgroundEraserTool 
 背景橡皮擦工具 
 
 
 magicEraserTool 
 魔术橡皮擦工具 
 
 
 dodgeTool 
 减淡工具 
 
 
 burnInTool 
 加深工具 
 
 
 saturationTool 
 海绵工具 
 
 
 blurTool 
 模糊工具 
 
 
 sharpenTool 
 锐化工具 
 
 
 smudgeTool 
 涂抹工具 
 
 
 3DMaterialSelectTool 
 3D 材质吸管工具 
 
 
 textAnnotTool 
 注释工具 
 
 
 countTool 
 计数工具 
 
 
 colorReplacementBrushTool 
 颜色替换工具 
 
 
 wetBrushTool 
 混合器画笔工具 
 
 
 historyBrushTool 
 历史记录画笔工具 
 
 
 artBrushTool 
 历史记录艺术画笔工具 
 
 
 3DMaterialDropTool 
 3D 材质拖放工具 
 
 
 typeVerticalCreateMaskTool 
 直排文字蒙版工具 
 
 
 typeCreateMaskTool 
 横排文字蒙版工具 
 
 
 lineTool 
 直线工具 
 
 
 rotateTool 
 旋转视图工具 
 
 
 
  

  查看图片  
  displayDialogs   DialogModes  
 运行脚本时宿主程序和时弹出对话框。 
 
 
 
  
  
 
 
 DialogModes.ALL 
 弹出所有 
 
 
 DialogModes.ERROR 
 只有弹出错误对话框 
 
 
 DialogModes.NO 
 不弹出对话框 
 
 
 
  documents   Documents  
 所有打开文档的合集。只读。 
  fonts   TextFonts  
 系统中的字体列表。 
  
  freeMemory   number  
 空闲内存。PS 能够使用的剩余内存量。 
  locale   string  
 宿主的地域语言。 
格式为 xx_YY，xx 为 2 个字节的 ISO-639 语言代码，YY 为 2 个字节的 ISO 3166&nbsp;国家代码。 
如： zh_CN 、  en_US 、 en_UK 、 ja_JP  
  measurementLog   MeasurementLog  
 测量记录。可以导出或删除测量工具的测量记录。 
  name   string  
 宿主名称。 
如： Adobe Photoshop  
  notifiersEnabled   boolean  
 是否启用脚本事件。 
  notifiers   Notifiers  
 脚本事件合集。可以添加或移除脚本事件。 
  查看图片  
  path   File  
 宿主应用所在目录。 
如：  /d/Creative/Adobe/Adobe%20Photoshop%20CC%202015  
（%20 代表空格） 
  playbackDisplayDialogs   DialogModes  
 重放对话框设置。 
 
 
 
  
  
 
 
 DialogModes.ALL 
 弹出所有 
 
 
 DialogModes.ERROR 
 只有弹出错误对话框 
 
 
 DialogModes.NO 
 不弹出对话框 
 
 
 
  playbackParameters   ActionDescriptor  
 重复参数。 
  preferences   Preferences  
 首选项。获得首选项参数。只读。 
 recentFiles  File 数组  
 最近文件列表。只读。 
  scriptingBuildDate   string  
 脚本接口生成时间。 
如： Jan 13 2016 00:19:41  
  scriptingVersion   string  
 脚本接口版本。 
如： 16.1.2  
  systemInformation   string  
 系统信息。与“菜单-帮助-系统信息”中获取的内容相同。 
  查看图片  
  version   string  
 宿主版本号。 
  macintoshFileTypes   string 数组  
 宿主可以打开的文件格式数组（Mac）。 
  windowsFileTypes   string 数组  
 宿主可以打开的文件格式数组（Windows）。 
  方法  
  load ( 文档 ) 
 载入文档。 
 app.load( new File("/E/图片库/2014_8_29[22.48.52].png") )  
  open (文档, 打开选项, 是否作为智能对象 ) 
 打开文件。 
 打开一个文档。打开选项是可选的，可用使用 OpenDocumentType 指定文件格式，也能使用下面这些对象作为打开特定格式时的选项，例如导入 PDF 时的选项： 
CameraRAWOpenOptions、DICOMOpenOptions、EPSOpenOptions、PDFOpenOptions、PhotoCDOpenOptions、RawFormatOpenOptions 
 是否作为智能对象为真时会把文档作为智能对象添加到已打开的文档中。 
 文档： File  
打开选项： object 或 OpenDocumentType  
是否作为智能对象： boolean  
   File 数组   openDialog()  
 打开文件对话框。弹出打开文件对话框让用户选择文件（选中的文件不会被宿主打开），返回打开文件的 File 数组。 
  beep()  
 发出提示音。 
  boolean   showColorPicker()  
 打开拾色器，如果用户没有选择颜色返回假。 
  bringToFront () 
 激活宿主应用的窗口。 
  doAction (动作名, 动作组名) 
 执行一个动作。 
 app.doAction("动作 1", "组 1")  
  查看图片  
  doProgress ( 进度条文本, 执行代码 ) 
 执行进度条任务。 
进度条文本：string 
执行代码：string 
  app.doProgress("已经完成 0/10 了哟！","task()")

function task(){
    for( var i=1;i&lt;10; i++)
    {
        updateProgress(i, 10);
        changeProgressText("已经完成 " + i + " / 10 了哟！")
        app.refresh();//刷新界面，这会让脚步运行速度大大降低，尽量减少频率
    }
}  
 &nbsp; 查看图片  
  updateProgress ( 已完成, 总数 ) 
 更新进度条。 
 已完成： number  
总数： number  
  changeProgressText ( 进度条文本 ) 
 改变进度条文本。 
 进度条文本： string  
  doForcedProgress ( 进度条文本, 执行代码 ) 
 执行无法取消的进度条任务。 
 进度条文本： string  
执行代码： string  
  doProgressSegmentTask ( 段长度, 已完成长度, 总长度, 执行代码 ) 
 执行进度条任务段。 
 段长度： number  
已完成长度： number  
总长度： number  
执行代码： string  
  doProgressSubTask ( 任务索引, 任务总数, 执行代码 ) 
 执行进度条子任务。 
 任务索引： number  
任务总数： number  
执行代码： string  
  doProgressTask ( 任务长度, 执行代码 ) 
 执行进度条任务。 
 任务长度： number  
执行代码： string  

  ActionDescriptor   getCustomOptions ( 键 ) 
 取自定义选项。 
  putCustomOptions ( 键, 自定义选项, 持久化 ) 
 添加自定义选项。键是这个自定义选项的唯一可识别标志。持久化如果为真，这个自定义选项在此脚本结束后仍有效。 
 键： string  
 自定义选项： ActionDescriptor  
持久化： boolean  
  eraseCustomOptions ( 键 ) 
 清除自定义选项。 
从宿主中清除指定 ID 的用户对象。 
 键： string  

  executeAction ( 事件, 动作描述符, 对话框模式 ) 
 执行动作代理事件。 
 事件： number  
动作描述符： ActionDescriptor  
对话框模式： DialogModes  
  ActionDescriptor   executeActionGet ( 动作参考 ) 
 取执行动作描述符。 
从一个 ActionReference 中得到 ActionDescriptor 信息。 
  boolean   featureEnabled ( 名称 ) 
 查询特性可用。 
查询属于各版本的功能是否可用。 
 "photoshop/extended" ：扩展版 
 "photoshop/standard" ：标准版 
 "photoshop/trial" ：体验版 
  //查询扩展版功能是否可用
app.featureEnabled("photoshop/extended")  
  boolean   isQuicktimeAvailable () 
 系统中是否安装了 Quicktime。 
  purge ( 目标 ) 
 清除缓存。 
 
 
 
  
  
 
 
 PurgeTarget.ALLCACHES 
 全部缓存 
 
 
 PurgeTarget.CLIPBOARDCACHE 
 剪切板缓存 
 
 
 PurgeTarget.HISTORYCACHES 
 历史记录 
 
 
 PurgeTarget.UNDOCACHES 
 重做缓存 
 
 
 
  refresh () 
 刷新宿主。暂停脚本而刷新宿主，常用于在执行长时间脚本时让用户看的当前结果。 
  refreshFonts () 
 刷新字体列表。 
  runMenuItem ( 菜单 ID ) 
 打开一个指定菜单。 
 菜单 ID： number  
  number   charIDToTypeID ( charID ) 
 将字符 ID 转换为实际运行 ID。 
 charID： string  
  number   stringIDToTypeID ( stringID ) 
 把字符串 ID 转换为实际运行 ID。 
 stringID： string  
  string   typeIDToCharID ( typeID ) 
 实际运行 ID 转化为字符 ID。 
 typeID： number  
  string   typeIDToStringID ( typeID ) 
 实际运行 ID 转化为字符串 ID。 
 typeID： number  
  togglePalettes () 
 切换宿主窗口显示模式。 
  boolean   toolSupportsBrushes (工具) 
 检查工具可用。 
 工具： string  
  batch ( 输入文件, 动作, 目标, 选项 ) 
 批处理。“菜单-文件-自动-批处理”。 
 输入文件：File 数组 
动作：string 
目标：string 
选项：BatchOptions 
  查看图片  
  Document  
  属性  
  channels   Channels  
 通道合集。 
  activeHistoryBrushSourceGuide   HistoryState  
 当前编辑的历史历史记录（即有“笔图标”的历史记录）。 
  查看图片  
  activeHistoryState   HistoryState  
 当前选中的历史记录 
  activeLayer   ArtLayer 或 LayerSet  
 选中的图层或图层组。 
  artLayers   ArtLayers  
 文档根目录的图层合集。不包括图层组。 
  backgroundLayer   ArtLayer  
 背景图层。 
  bitsPerChannel   BitsPerChannelType  
 颜色位数。 
 
 
 
  
  
 
 
 BitsPerChannelType.EIGHT 
 8 位（默认） 
 
 
 BitsPerChannelType.ONE 
 1 位 
 
 
 BitsPerChannelType.SIXTEEN 
 16 位 
 
 
 BitsPerChannelType.THIRTYTWO 
 32 位 
 
 
 
  colorProfileType   ColorProfile  
 色彩管理方式。 
 
 
 
  
  
 
 
 ColorProfile.NONE 
 不对此文档应用色彩管理 
 
 
 ColorProfile.WORKING 
 工作中的色彩配置文件 
 
 
 ColorProfile.CUSTOM 
 自定义配置文件 
 
 
 
  colorProfileName   string  
 色彩配置文件名。需要色彩管理方式为&nbsp; ColorProfile.CUSTOM &nbsp;。 
  app.activeDocument.colorProfileName = "Adobe RGB (1998)"
app.activeDocument.colorProfileType = ColorProfile.CUSTOM  
 &nbsp; 查看图片  
  mode   DocumentMode  
 文档色彩模型。 
 
 
 
  
  
 
 
 DocumentMode.BITMAP 
 位图 
 
 
 DocumentMode.CMYK 
 CMYK 
 
 
 DocumentMode.DUOTONE 
 双色调 
 
 
 DocumentMode.INDEXEDCOLOR 
 索引颜色 
 
 
 DocumentMode.GRAYSCALE 
 灰度 
 
 
 DocumentMode.MULTICHANNEL 
 多通道 
 
 
 DocumentMode.RGB 
 RGB 
 
 
 DocumentMode.LAB 
 Lab 
 
 
 

  colorSamplers   ColorSamplers  
 色彩取样点合集。 
 
 
 
 方法 
 作用 
 
 
 ColorSamplers.add(x, y) 
 添加采样点 
 
 
 ColorSamplers.removeAll() 
 移除全部采样点 
 
 
 

  componentChannels   Channel 数组  
 构成通道合集，如 RGB 色彩模式的红、绿、蓝通道。 
  fullName   File  
 文件完整路径。 
  app.activeDocument.fullName //"/e/Work/m.psd"  
  guides   Guides  
 参考线合集。 
  height     UnitValue   
 文档高度。只读。 
 width    UnitValue   
 文档宽度。只读。 
  histogram   number 数组  
 直方图。256 个数的数组表示的直方图。 
 historyStates  HistoryStates  
 历史记录合集。 
  info   DocumentInfo  
 文档元数据信息。 
  layerComps    LayerComps   
 图层复合。 
  layers   layers  
 图层和图层组的合集。 
  layerSets   LayerSets  
 图层组的合集。 
 managed  boolean  
 是否是工作组文档，只读。 
  name   string  
 文档名称。只读。 
  path   File  
 文档所在目录路径。 
如： /e/Work/GitHub/PS.fonTags/logo  
  pathItems   PathItems  
 路径元素合集。只读。 
  pixelAspectRatio   number  
 像素长宽比。 
  查看图片  
  printSettings   DocumentPrintSettin  
 文档打印设置。只读。 
  quickMaskMode   boolean  
 快速蒙版模式。 
  查看图片  
  resolution   number  
 文档分辨率（像素/英寸）。 
  saved   boolean  
 最后一次编辑后文档是否已保存。 
  selection   Selection  
 文档选中区域。 
  xmpMetadata   xmpMetadata  
 XMP 元数据。用 xmpMetadata.rawData 获取和修改 XMP 原数据的 XML 。 
  countItems   countItems  
 计数工具，计数点合集。 
  方法  
  changeMode ( 目标模型, 选项 ) 
 改变文档色彩模型。 
 目标模型： ChangeMode  
 
 
 
  
  
 
 
 ChangeMode.BITMAP 
 位图 
 
 
 ChangeMode.CMYK 
 CMYK 
 
 
 ChangeMode.GRAYSCALE 
 灰度 
 
 
 ChangeMode.INDEXEDCOLOR 
 索引颜色 
 
 
 ChangeMode.LAB 
 Lab 
 
 
 ChangeMode.MULTICHANNEL 
 多通道 
 
 
 ChangeMode.RGB 
 RGB 
 
 
 
 选项：&nbsp;  BitmapConversionOptions  （位图）或&nbsp; IndexedConversionOptions （索引颜色） 
  close ( 是否存储 ) 
 关闭文档。 
 是否存储： SaveOptions  
 
 
 
  
  
 
 
 SaveOptions.DONOTSAVECHANGES 
 不存储改变 
 
 
 SaveOptions.PROMPTTOSAVECHANGES 
 用户选择（弹出对话框） 
 
 
 SaveOptions.SAVECHANGES 
 存储改变 
 
 
 
  convertProfile ( 目标空间配置文件, 意图, 黑场补偿, 使用仿色 ) 
 转化为配置文件。 
 目标空间配置文件： string  
意图： intent  
 
 
 
  
  
 
 
 Intent.PERCEPTUAL 
 可感知 
 
 
 Intent.SATURATION 
 饱和度 
 
 
 Intent.RELATIVECOLORIMETRIC 
 相对比色 
 
 
 Intent.ABSOLUTECOLORIMETRIC 
 绝对比色 
 
 
 
 黑场补偿： boolean  
使用仿色： boolean   
  查看图片  
  crop ( 区域, 角度, 新宽度, 新高度 ) 
 剪裁。按区域进行剪裁。角度和新宽度、新高度是可选选项，是将剪裁后的内容选择并拉伸到新尺寸，可省略。在文档有画板的情况下不能剪裁。 
 区域：   UnitValue  数组  
角度： number  
新宽度：   UnitValue   
新高度：   UnitValue   
  app.activeDocument.crop([UnitValue ("0px"), UnitValue ("0px"), UnitValue ("150px"), UnitValue ("250px")]);  

  duplicate ( 新名称, 拼合图层 ) 
 复制文档。创建一个文档的副本，你可以指定副本的名称，和是否拼合新文档的所有图层。 
 新名称： name  
拼合图层： boolean  
  查看图片  
  exportDocument ( 文档路径, 导出类型, 选项 ) 
 导出文档，即是菜单-文件-导出中的 “路径到illustrator…” ，“存储为 Web 所用格式”。 
 文档路径： ExportType  
 
 
 
  
  
 
 
 ExportType.ILLUSTRATORPATHS 
 导出为 illustrator路径 
 
 
 ExportType.SAVEFORWEB 
 存储为 Web 所用格式 
 
 
 
 选项： ExportOptionsIllustrator  或&nbsp;  ExportOptionsSaveForWeb   
 
 
 
 ExportOptionsIllustrator 
 
 
 path  IllustratorPathType  
 
 IllustratorPathType.ALLPATHS 
 
 所有路径 
 
 
 
 IllustratorPathType.DOCUMENTBOUNDS 
 
 文档范围 
 
 
 
 IllustratorPathType.NAMEDPATH 
 
 
 指定名称路径 
 
 
 
 pathName  string  
 路径名称，当路径类型为&nbsp;IllustratorPathType.NAMEDPATH 的时候有效，指定要导出的路径名称。 
 
 
 
  ExportOptionsSaveForWeb  

  flatten () 
 拼合图像。 
  resizeCanvas  ( 宽度, 高度, 锚点 ) 
 重设画布大小。 
 宽度：   UnitValue   
宽度：   UnitValue   
锚点： AnchorPosition  
 
 
 
 AnchorPosition 
 
 
  AnchorPosition.TOPLEFT 
  左上  
  AnchorPosition.TOPCENTER 
  正上  
  AnchorPosition.TOPRIGHT 
  右上  
 
 
  AnchorPosition.MIDDLELEFT 
  左中  
  AnchorPosition.MIDDLECENTER 
  正中  
  AnchorPosition.MIDDLERIGHT 
  右中  
 
 
  AnchorPosition.BOTTOMLEFT 
  左下  
  AnchorPosition.BOTTOMCENTER 
  正下  
  AnchorPosition.BOTTOMRIGHT 
  右下  
 
 
 
  resizeImage ( 宽度, 高度, 分辨率, 重新采样, 减少杂色 ) 
 重设图像大小。 
宽度：   UnitValue   
高度：   UnitValue   
分辨率： number  
重新采样： ResampleMethod  
 
 
 
 ResampleMethod 
 
 
 ResampleMethod.AUTOMATIC 
 自动 
 
 
 ResampleMethod.BICUBIC 
 两次立方 
 
 
 ResampleMethod.BICUBICAUTOMATIC 
 两次立方自动 
 
 
 ResampleMethod.BICUBICSHARPER 
 两次立方（较锐利）（缩减） 
 
 
 ResampleMethod.BICUBICSMOOTHER 
 两次立方（较平滑）（扩大） 
 
 
 ResampleMethod.BILINEAR 
 两次线性 
 
 
 ResampleMethod.NEARESTNEIGHBOR 
 邻近（硬边缘） 
 
 
 ResampleMethod.NONE 
 无 
 
 
 ResampleMethod.PRESERVEDETAILS 
 保留细节（扩大） 
 
 
 
  查看图片  
  revealAll () 
 显示全部。“菜单-图像-显示全部” 
自动调整画布尺寸以显示所有内容。 
  save () 
 保存。 

  saveAs ( 文件, 选项, 作为副本, 扩展名大小写&nbsp;) 
 另存为。 
 文件： File  
选项： BMPSaveOptions 、 GIFSaveOptions 、 JPEGSaveOptions 、 PNGSaveOptions  
作为副本： boolean  
扩展名大小写： Extension  
 
 
 
 Extension 
 
 
 Extension.LOWERCASE 
 小写 
 
 
 Extension.UPPERCASE 
 大写 
 
 
 Extension.NONE 
 不处理 
 
 
 
 splitChannels() 
 分离通道，把通道分离为单个文档。返回新建的 Document 数组。 
  suspendHistory ( 历史记录名称, 代码) 
 创建历史记录。 
执行一段代码，并为其创建一个历史记录： 
  app.activeDocument.suspendHistory("新建 3 个图层哟", "addLayer(3)");
function addLayer(n){
    for(var i=0; i     
 &nbsp; 查看图片  

  rotateCanvas ( 角度 ) 
 旋转画布。 
 角度： number  
  flipCanvas (方向) 
 翻转画布 。 
 方向： Direction  

 
 
 
 Direction 
 
 
 Direction.HORIZONTAL 
 水平 
 
 
 Direction.VERTICAL 
 垂直 
 
 
 
 importAnnotations( 注释文件 ) 
 导入注释。“菜单-文件-导入注释”。 
  mergeVisibleLayers () 
 合并可见图层。 
  rasterizeAllLayers () 
 栅格化所有图层。 
  paste ( 粘贴到选择区域 ) 
 粘贴。如果粘贴到选择区域为真，则会粘贴到选择区域。 
 粘贴到选择区域： boolean  
  trim ( 裁切类型, 顶, 左, 底, 右 ) 
 裁切。 
 裁切类型： TrimType  
 
 
 
  
  
 
 
 TrimType.BOTTOMRIGHT 
 右下角像素颜色 
 
 
 TrimType.TOPLEFT 
 左上角像素颜色 
 
 
 TrimType.TRANSPARENT 
 透明像素 
 
 
 
 顶： boolean  
左： boolean  
底： boolean  
右： boolean  
  查看图片  
  print ( 源空间, 打印空间, 意图, 黑点补偿 ) 
 打印文档。 
 源空间： SourceSpaceType  
打印空间： string  
意图： Intent  
黑点补偿： boolean  

  trap ( 宽度 ) 
 烙印。菜单-图像-烙印。当图像为 CMYK 模式时有效。 
  查看图片  
  measurementScale   MeasurementScale  
 “菜单-图像-分析-设置测量比例”的设置。只有 Extended 版的 PS 才有此功能。 
  查看图片  
 
 
 
 MeasurementScale 
 
 
 pixelLength  number  
 像素长度 
 
 
 logicalLength  number  
 逻辑长度 
 
 
 logicalUnits  string  
 逻辑单位 
 
 
 
  recordMeasurements&nbsp; ( 来源, 数据点 ) 
 记录测量。 
 来源： MeasurementSource  
 
 
 
 MeasurementSource 
 
 
 MeasurementSource.MEASURESELECTION 
 选区 
 
 
 MeasurementSource.MEASURECOUNTTOOL 
 计数工具 
 
 
 MeasurementSource.MEASURERULERTOOL 
 标尺工具 
 
 
 
 数据点： string 数组  
  查看图片  
  autoCount ( 通道, 阈值 ) 
 自动计数。 
 通道： Channel  
阈值： number  
  选区与通道  
   Selection   
 选区。 
  属性  
  bounds     UnitValue  数组  
 选区边界位置，只读。[0,1,2,3] 分别是 0:左侧左边距 1:顶侧顶边距 2:右侧左边距 3:底侧顶边距。 
  查看图片  
  solid   boolean  
 是否是矩形选区。 
  方法  
  clear () 
 清除选区内容。 
  contract ( 收缩量 ) 
 收缩选区。 
 收缩量：   UnitValue   
  expand ( 扩展量 ) 
 扩展选区。 
 扩展量为：   UnitValue   
  feather ( 羽化量 ) 
 羽化选区。 
 羽化量：   UnitValue  。 
  fill ( 填充颜色, 混合模式, 不透明度, 保留透明区域 ) 
 填充。 
 填充颜色： SolidColor  
混合模式： ColorBlendMode  
不透明度： number（0~100）  
保留透明区域： boolean  
  查看图片  
  grow ( 容差, 消除锯齿 ) 
 扩展。 
 容差 number 
消除锯齿 boolean 
  invert () 
 反选。 
  load ( 通道, 选区操作, 反相 ) 
 载入选区。从通道载入选区。 
 通道： Channel  
选区操作： SelectionType  
 
 
 
  
  
 
 
 SelectionType.DIMINISH 
 从选区中减去 
 
 
 SelectionType.EXTEND 
 添加到选区 
 
 
 SelectionType.INTERSECT 
 与选区交叉 
 
 
 SelectionType.REPLACE 
 新建选区 
 
 
 
 反相： boolean  
  查看图片  
  makeWorkPath ( 容差 ) 
 建立工作路径。 
  查看图片  
  resize ( 水平位置, 垂直位置, 锚点位置 ) 
 自由变换，重设选区内容尺寸。 
  resizeBoundary ( 水平位置, 垂直位置, 锚点位置 ) 
 变换选区，重设选区尺寸。 
 水平位置： number  
垂直位置： number  
锚点位置： AnchorPosition  

  rotate ( &nbsp;角度, 锚点 ) 
 旋转。 
 角度： number  
锚点： AnchorPosition  
  resizeBoundary ( 角度, 锚点 ) 
 旋转选区。 
 角度： number  
锚点： AnchorPosition  

  select ( 区域, 操作, 羽化, 消除锯齿 ) 
 创建选区。 
 区域是一个4个角的坐标数组：[左上, 右上, 右下, 左下]
操作可以是： 
 区域： number 数组 
 操作： SelectionType 
  
 
 
 
 SelectionType.DIMINISH 
 从选区中减去 
 
 
 SelectionType.EXTEND 
 添加到选区 
 
 
 SelectionType.INTERSECT 
 与选区交叉 
 
 
 SelectionType.REPLACE 
 新建选区 
 
 
 
 羽化： boolean 
 消除锯齿： boolean 
  
  app.activeDocument.selection.select([[0,0],[300,0],[555,100],[50,110]] ,SelectionType.REPLACE,0,false)  
  selectAll () 
 全选。 
  selectBorder ( 宽度 ) 
 边界选区。 
 宽度：UnitValue 
  查看图片  
  similar ( 容差, 消除锯齿 ) 
 选取相似。 
 容差： number  
消除锯齿： boolean  
  smooth ( 取样半径 ) 
 取样半径： number  
  查看图片  
  store ( 通道, &nbsp;操作 ) 
 存储选区。 
 通道： Channel  
操作： SelectionType  
  查看图片  
  stroke ( 描边颜色, 描边宽度,位置, 混合模式, 不透明度, 保持透明度区域 ) 
 描边。 
描边颜色： SolidColor  
描边宽度： number  
位置： StrokeLocation  
 
 
 
 StrokeLocation 
 
 
 StrokeLocation.CENTER 
 居中 
 
 
 StrokeLocation.INSIDE 
 内部 
 
 
 StrokeLocation.OUTSIDE 
 居外 
 
 
 
 混合模式： ColorBlendMode  
不透明度： number  
保持透明度区域： boolean  
  查看图片  
  translate ( X 偏移值 , Y 偏移值 ) 
 移动。移动选区内容位置。 
  translateBoundary ( X 偏移值 , Y 偏移值 ) 
 移动。移动选区位置。 
  copy ( 复制所有可见图层 ) 
 复制选区内容。如果“复制所有可见图层”参数为真，将复制选区下所有可见图层内容，否则只复制当前图层内容。 
 复制所有可见图层： boolean  
  cut () 
 剪切选区内容。 
  deselect () 
 取消选择。 
  Channel  
 通道。 
  属性  
  kind   ChannelType  
 通道类型，即通道选项中色彩指示的选项。 
 
 
 
 ChannelType 
 
 
 ChannelType.COMPONENT 
 色彩模型相关的通道（如红、绿、蓝） 
 
 
 ChannelType.MASKEDAREA 
 被蒙版区域 
 
 
 ChannelType.SELECTEDAREA 
 所选区域 
 
 
 ChannelType.SPOTCOLOR 
 专色 
 
 
 
  查看图片  
  histogram   number 数组  
 直方图。一个 256 个数的数组表示的直方图信息。只读。 
  name   string  
 通道名称。 
  color   SolidColor  
 颜色。通道颜色，如果通道类型是 ChannelType.COMPONENT：色彩模型相关的通道，颜色设置是无效的。 
  查看图片  
  opacity   number  
 不透明度（0~100）。只有通道类型为 ChannelType.MASKEDAREA（被蒙版区域）和 ChannelType.SELECTEDAREA（所选区域）时才有效。 
  visible   boolean  
 通道可视性。 
  方法  
  duplicate ( 目标文档 ) 
 复制通道，创建一个通道的副本到目标文档，如果不填目标文档参数，将创建到当前文档。 
  app.activeDocument.channels[0].duplicate(app.documents[1])  
  merge () 
 合并专色通道。只有通道类型是： ChannelType.SPOTCOLOR ：专色才可用。 

  动作代理  
 脚本除了直接操作 DOM ，还有一种更加底层的操作宿主的方式：Action Manager ，与操作&nbsp;DOM 不同，DOM 只是封装了宿主一部的操作，而动作代理几乎能完成所有宿主的操作。关于动作代理的使用，推荐去阅读文章： 「 5 」 Photoshop ExtendScript 入门#动作代理  
  ActionDescriptor  
 动作描述符。 
  属性  
  count   number  
 数量。描述中键值数量。 
  方法  
  clear () 
 清空描述符。 
  erase ( 键) 
 清除一个键值。 
 键： number  
  boolean   getBoolean ( 键&nbsp;) 
 取布尔值类型的键值。 
 键：number 
  number   getClass ( 键 ) 
 取类类型的键值。 
 键： number  
  string   getData ( 键 ) 
 取键值的原始数据的字节数据。 
 键： number  
  number   getDouble ( 键 ) 
 取双精度浮点数类型的键值。 
 键： number  
  number  getEnumerationType(键值) 
 取键值的枚举类型。 
 键： number  
  number   getEnumerationValue (键值) 
 取键值的枚举值。 
 键： number  
  number   getInteger (键) 
 取整数类型的键值。 
 键： number  
  number   getKey ( 索引号 ) 
 根据索引号取键值。 
 索引号： number  
  number   getLargeInteger (键) 
 取长整数类型的键值。 
 键： number  
  ActionList  getList( 键 ) 
 取动作列表类型的键值。 
 键： number  
  number  getObjectType(键值) 
 获取一个键值对象的类标识( class ID) 
 键： number  
  ActionDescriptor   getObjectValue ( 键 ) 
 获取一个键值的对象。 
 键： number  
  File   getPath (键) 
 取路径类型的键值。 
 键： number  
  ActionReference   getReference (键) 
 获取键值对应的动作参数。 
 键： number  
 string  getString (键) 
 获取键值对应的字符串。 
 键：number 
  DescValueType   getType (键值) 
 获取键的类型 
 键： number  
 描述符值类型。 
 
 
 
 DescValueType 
 
 
 DescValueType.ALIASTYPE 
 别名类型 
 
 
 DescValueType.BOOLEANTYPE 
 布尔值类型 
 
 
 DescValueType.CLASSTYPE 
 类 
 
 
 DescValueType.DOUBLETYPE 
 双精度浮点数类型 
 
 
 DescValueType.ENUMERATEDTYPE 
 枚举类型 
 
 
 DescValueType.INTEGERTYPE 
 整数类型 
 
 
 DescValueType.LARGEINTEGERTYPE 
 长整数类型 
 
 
 DescValueType.LISTTYPE 
 列表类型 
 
 
 DescValueType.OBJECTTYPE 
 对象类型 
 
 
 DescValueType.RAWTYPE 
 原始数据类型 
 
 
 DescValueType.REFERENCETYPE 
 动作参数类型 
 
 
 DescValueType.STRINGTYPE 
 字符串类型 
 
 
 DescValueType.UNITDOUBLE 
 单位偶 
 
 
 
 number  getUnitDoubleType (键) 
 取单位偶的单位类型。 
 键：number 
  number   getUnitDoubleValue (键) 
 取单位偶的单位类型。 
 键：number 
  boolean   hasKey ( 键 ) 
 检查描述符是否有键。 
 键： number  
  boolean   isEqual (动作描述符) 
 与另一个动作描述符比较是否相等，相等返回真。 
 动作描述符： 
  putBoolean (键, 值) 
 添加一个布尔值类型的键值。 
 键： number  
值： boolean  
  putClass (键, 值) 
 添加一个类类型的键值。 
 键： number  
值： number  
  putData (键, 值) 
 添加一个原始数据类型的键值。 
 键： number  
值： string  
  putEnumerated (键, 枚举类型, 值) 
 添加一个枚举键值。 
 键： number  
枚举类型： number  
值： number  
  putInteger ( 键, 值 ) 
 添加一个整数类型的键值。 
 键： number  
值： number  
  putLargeInteger ( 键, 值 ) 
 添加一个长整数类型的键值。 
 键： number  
值： number  
  putList (键, 值) 
 添加一个列表类型的键值。 
 键： number  
值： ActionList  
  putObject (键, 类ID, 值) 
 添加一个对象类型的键值。 
 键： number  
类 ID (classID)： number  
值： ActionDescriptor  
  putPath ( 键, 值 ) 
 添加一个文件路径类型的键值。 
 键： number  
值： File  
  putReference (键, 值) 
 添加一个动作参数类型的键值。 
 键： number  
值： ActionReference  
  putString (键, 值) 
 添加一个字符串类型的键值。 
 键：number 
值：string 
  putUnitDouble (键, 单位 ID, 值) 
 添加一个单位偶键值。 
 键：number 
单位 ID：number 
值：number 
  string   toStream () 
 生成标识符的字节流。用以把标识符保存为文件。 
  fromStream ( 值 ) 
 从字节流读取描述符。用从文件中载入标识符。 
 值： string  
  ActionReference  
 动作参考。 
  方法  
  ActionReference   getContainer () 
 获取一个包含此动作参考的容器。 
  number   getDesiredClass () 
 获取请求类。 
  number   getEnumeratedType () 
 获取枚举类型。 
  number   getEnumeratedValue () 
 获取枚举值。 
  ReferenceFormType   getForm () 
 获取此动作参考的应用类型。 
 
 
 
 ReferenceFormType 
 
 
 ReferenceFormType.CLASSTYPE 
 类类型 
 
 
 ReferenceFormType.ENUMERATED 
 枚举类型 
 
 
 ReferenceFormType.IDENTIFIER 
 标识符 
 
 
 ReferenceFormType.INDEX 
 索引 
 
 
 ReferenceFormType.NAME 
 名称 
 
 
 ReferenceFormType.OFFSET 
 偏移值 
 
 
 ReferenceFormType.PROPERTY 
 属性 
 
 
 
  number   getIdentifier () 
 获取标识符值。 
  number   getIndex () 
 获取索引号。 
  string   getName () 
 获取名称。 
  number   getOffset () 
 获取偏移值。 
  number   getProperty () 
 获取属性 ID 值。 
  putClass&nbsp; (&nbsp;请求类 ) 
 添加请求类。 
 请求类： number   
  putEnumerated ( 请求类, 列举类型, 值&nbsp;) 
 添加枚举值。 
 请求类： number 
 列举类型： number  
值： number  
  putIdentifier ( 请求类, 值&nbsp;) 
 添加标识符。 
 请求类： number  
值： number  
  putIndex (&nbsp;请求类, 值) 
 添加索引。 
 请求类： number  
值： number  
  putName (&nbsp;请求类, 值) 
 添加名称。 
 请求类： number  
值： number  
  putOffset ( 请求类, 值&nbsp;) 
 添加偏移值。 
 请求类： number  
值： number  
 putProperty( 请求类 , 值) 
 添加属性。 
 请求类： number  
值： number  
  ActionList  
 动作列表，类似于数组的数据存储对象，不过只能添加成员数据，不能修改已经添加的数据，除非清空列表重新添加。 
  属性  
  number   count  
 列表成员数。 
  方法  
  boolean   getBoolean ( 索引号 ) 
 取布尔值类型的指定列表元素。 
  number   getClass ( 索引号 ) 
 取类类型的指定列表元素。 
  string   getData ( 索引号 ) 
 取的指定列表元素的原始数据。 
  string   getDouble ( 索引号 ) 
 取双精度浮点类型的指定列表元素。 
  string   getEnumerationType ( 索引号 ) 
 取枚举类型的指定列表元素。 
  number   getEnumerationValue ( 索引号 ) 
 取指定列表元素的枚举值。 
  number   getInteger ( 索引号 ) 
 取指定列表元素的枚举值。 








  数据类型与常数  
    Documents  
  属性  
  length   number  
 长度。documents 合集中 document 的数量。 

  方法  
  add (  宽带, 高度, 分辨率, 名称, 文档颜色模式, 背景内容, 像素长宽比, 颜色位数, 色彩管理&nbsp; )  
 新建一个文档。 
 宽度：   UnitValue   
高度：   UnitValue   
分辨率： number  
名称： string  
文档颜色模式： NewDocumentMode  
 
 
 
  
  
 
 
 NewDocumentMode.BITMAP 
 位图 
 
 
 NewDocumentMode.CMYK 
 CMYK 颜色 
 
 
 NewDocumentMode.GRAYSCALE 
 灰度 
 
 
 NewDocumentMode.LAB 
 Lab 颜色 
 
 
 NewDocumentMode.RGB 
 RGB 颜色 
 
 
 
 背景内容： DocumentFill  
 
 
 
  
  
 
 
 DocumentFill.BACKGROUNDCOLOR 
 拾色器背景颜色 
 
 
 DocumentFill.TRANSPARENT 
 透明背景 
 
 
 DocumentFill.WHITE 
 白色背景 
 
 
 
 像素长宽比： number （默认为1） 
  查看图片  
 颜色位数： BitsPerChannelType  
 
 
 
  
  
 
 
 BitsPerChannelType.EIGHT 
 8 位（默认） 
 
 
 BitsPerChannelType.ONE 
 1 位 
 
 
 BitsPerChannelType.SIXTEEN 
 16 位 
 
 
 BitsPerChannelType.THIRTYTWO 
 32 位 
 
 
 
 色彩管理： string  （色彩配置文件名称） 
  Document   getByName ( 名称 ) 
 根据名称取文档。查找并返回指定名称的文档。 


  File  
 文件。File&nbsp;是非常重要的对象，打开文件、存储文件等都需要使用 File 处理路径。 
  属性  
  fsName&nbsp;  string  
 当前系统文件风格的完整路径。只读。 
  D:\Creative\Adobe\Adobe Photoshop CC 2015\Photoshop.exe  
  fullName &nbsp; string  
 完整路径。只读。 
  /d/Creative/Adobe/Adobe Photoshop CC 2015/Photoshop.exe  
  absoluteURI&nbsp;  string&nbsp;  
 绝对 URI 路径。完整路径转义后的&nbsp;URI 形式。只读。 
  /d/Creative/Adobe/Adobe%20Photoshop%20CC%202015/Photoshop.exe  
  relativeURI &nbsp; string  
 相对 URI 路径。文件相对于当前文件夹的&nbsp;URI 路径。只读。 
  //当前目录是：D:\Creative\Adobe\Adobe Photoshop CC 2015\ 时：
Photoshop.exe
  
 name&nbsp; string  
 文件名（完整路径）。转义后的&nbsp;URI 形式。只读。 
  /d/Creative/Adobe/Adobe%20Photoshop%20CC%202015/Photoshop.exe  
  displayName &nbsp;&nbsp; string&nbsp;   
 显示文件名。本地显示的文件名，（不包括路径）。 只读。 
  Photoshop.exe  
  path &nbsp; string  
 文件所在目录的路径。 
   /d/Creative/Adobe/Adobe%20Photoshop%20CC%202015  
  alias   boolean  
 别名。如果为真则说明这个文件是一个操作系统别名或快捷方式。只读。 

  created   Date   
 文件创建日期。如果为空说明此文件是未创建的。只读。 
  modified&nbsp; Data   
 文件最后修改日期。只读。 
  creator&nbsp;  string&nbsp;  
 创造者。只对 OS X 系统有效。 Windows &nbsp;下为 “????”。只读。 
  displayName &nbsp;&nbsp; string&nbsp;   
 显示文件名。本地显示的文件名，（不包括路径）。 只读。 
  encoding &nbsp;  string  
 读写编码设置。 
  eof&nbsp;  boolean  
 文件当前读写位置是否位于文件结束位置。只读。 
  error&nbsp;  string&nbsp;  
 文件系统错误记录。 

  exists &nbsp; boolean  
 文件是否存在。只读。 

  hidden&nbsp;  boolean  
 是否隐藏文件。 
  length&nbsp;  number  
 文件长度（字节）。可修改，修改长度会用填 0 字节或截断文件来处理。 
  lineFeed&nbsp;  string  
 换行类型。”Windows”、 “Macintosh”、 “Unix”。 
  readonly&nbsp;  boolean  

 文件只读。 
  type &nbsp; string  
 文件类型。 
  方法  
  changePath(&nbsp; 路径&nbsp;) 
 改变文件路径。 
 路径： string  
  close () 
 关闭文件。 
  copy ( 目的地 ) 
 复制当前文件到目的地，如果存在同名文件，则会覆盖。 
 目的地： string  

  createAlias ( 路径 ) 
 创建别名。 
 路径： string  

  execute ()  
 运行。在操作系统中打开文件，或运行程序。 

 open(读写模式，类型，创造者) 
 打开文件。类型和创造者是仅在 OS X 中使用的。Windows 下没用。 
 读写模式： string  
 
 
 
  
  
 
 
 r 
 仅读取。文件不存在会报错。 
 
 
 w 
 仅写入。如果文件存在会清空内容，不存在会创建新文件 
 
 
 e 
 编辑。读写一个已经存在的文件。 
 
 
 a 
 添加。在一个文件末尾读写。 
 
 
 
 类型： string  
 创造者： string  


  getRelativeURI ( 根目录&nbsp;) 
 取相对 URI 路径。以指定的根目录为参考，计算出相对 URI 路径。 

 根目录： string  

  File 或&nbsp;File 数组   openDialog(  提示文本, 过滤器, 允许多选&nbsp; )  
 弹出打开文件窗口。过滤器示例（windows）： "Javascript files:*.jsx;All files:*.*"。  

 提示文本： string  
过滤器： string 或 function  
允许多选 ：boolean  
   var a = File.openDialog("打开一个文件",);  
  查看图片  

   File  saveDialog( 提示文本, 过滤器 )  

 弹出保存文件窗口。过滤器示例（windows）：”Javascript files: .jsx;All files: .*”。 
 提示文本： string  
过滤器： string 或 function  
  string &nbsp;  read ( 字符数&nbsp;) 
 读取指定字符数文件。不提供字符数参数则读取全部内容。 

  string   readch () 
 读取当前位置一个字符。 
  string   readln () 
 读取当前位置一行。 

  boolean &nbsp;  write ( 文本 ) 
 在当前读写位置写入文本。 
 文本： string&nbsp;  

  boolean   writeln ( 文本 ) 
 在当前读写位置写入一行文本。会自动在末尾添加一个换行符。 
 文本：string 
  seek ( 偏移值, 模式 ) 
 移动当前读写位置到指定指定位置。模式  0 ：位置从 0 开始。模式  1 ：从当前位置开始。模式 2 ：从结束位置逆序。 
 偏移值： number  
模式： number  
  number &nbsp;  tell  () 
 查询当前读写位置。 

  string   toSource  () 
 转换为代码。把当前文件转换为一段代码文本，使用&nbsp;  eval() &nbsp;函数执行这段代码就能载入这个文件。 
 转换后的代码示例： 
  new File ("/d/DC_New_Hero_29K45.w3x")  
 File.toString (): string Core JavaScript Classes Converts this object to a string. 


  File &nbsp;  resolve  () 
 解析路径。如果当前文件是快捷方式或别名，返回一个其指向的实际文件的&nbsp;File 对象。 

  boolean   rename ( 新文件名 ) 
 重命名。 
 新文件名： string&nbsp;  
  remove ()  
 删除文件。 






    LayerComps  
 图层复合合集。 
  属性  
  length   number  
 图层复合数量。 
  方法  
  add ( 名称, 注释, 外观, 位置, 可视性) 
 创建一个图层复合。 
  removeAll () 
 移除全部。 
    LayerComp  
 图层复合。 
  属性  
  appearance   boolean  
 图层复合是否适用于内容：外观（图层样式）。 
  position   boolean  
 图层复合是否适用于内容：位置。 
  visibility   boolean  
 图层复合是否适用于内容：可见性。 
  comment   string  
 注释。 
  name   string  
 名称。 
  selected   boolean  
 是否被选择。 
  查看图片  
  方法  
  apply () 
 应用图层复合。 
  recapture () 
 更新图层复合。 
    ColorSampler  
 色彩采样点。 
  查看图片  
  属性  
 color  SolidColor  
 采集到的颜色。 
 position    UnitValue  数组  
 位置 [x,y]。 
  方法  
 move( [位置] ) 
 移动。 
 位置：   UnitValue  数组  
  remove () 
 移除此采样点。 
    UnitValue  
 单位值。 表示一个数值，此值的单位可以是 mm 、cm、px 等，在取得图层的相关数据的单位值时，其单位取决于首选项里的标尺单位设置。 
   Photoshop 首选项的单位设置  
 而使用  UnitValue(单位值字符串) &nbsp;可以创建一个单位值： 
  var a = UnitValue("22 px")
  
 单位名可以是： 
 
 
 
  
 
 
 像素 
 px 
 点 
 pt 
 
 
 英寸 
 in 
 派卡 
 pc 
 
 
 厘米 
 cm 
 百分比 
 % 
 
 
 毫米 
 mm 
  
  
 
 
 
 UnitValue 有用于转换的  as()  和  convert()  方法： 
 
  as(单位名)  可以返回一个指定单位的单位值，原变量单位不变。 
  convert(单位名)  把原单位值转换成指定单位，转换成功返回真。 
 
  var a = UnitValue("22 px")
a.convert ("cm") // true
a // 0.77611111111111 cm

var b = UnitValue("22 px")
b.as("cm") //0.77611111111111
b //22 px  

    SolidColor  
 通用颜色，存储和表示颜色，有  cmyk ,&nbsp; gray (灰度),  hsb ,  lab ,  rgb  的属性用来输入和输出色彩。 
 另外通过  nearestWebColor &nbsp;属性获得&nbsp;Web安全色，model 属性更改和获取 rgb 色彩空间。 
  //RGBColor
rgb.red =&nbsp;255 //[0~255]
rgb.green&nbsp;= 111&nbsp;//[0~255]
rgb.blue&nbsp;=&nbsp;200 //[0~255]
rgb.hexValue &nbsp;= "FFEEAA"

//CMYKColor
cmyk.black = 40 //[0.0~100.00]
cmyk.cyan&nbsp;= 20 //[0.0~100.00]
cmyk.magenta&nbsp;= 20 //[0.0~100.00]
cmyk.yellow&nbsp;= 10 //[0.0~100.00]

//GrayColor
gray.gray&nbsp;= 40 //[0.0~100.00]

//HSBColor
hsb.brightness&nbsp;= 12//[0.0~100.00]
hsb.hue&nbsp;= 120 //[0.0~360.00]
hsb.saturation&nbsp;= 100 //[0.0~100.00]

//LabColor
lab.l =&nbsp;20 //[0.0~100.0]
lab.a =&nbsp;20 //[-128.0~127.0]
lab.b= 30 //[-128.0~127.0]  
 可以通过  &nbsp;boolean   isEqual(  SolidColor  )  方法比较 2 个颜色是否相等： 
  var c = new SolidColor();
c.rgb.hexValue = "ffeeff";
var a = new SolidColor();
a.rgb.hexValue = "ffee2f";
c.isEqual(a); // false  

    AnchorPosition  
 锚点位置。 
 
 
 
  
  
 
 
 AnchorPosition.BOTTOMCENTER 
 正下 
 
 
 AnchorPosition.BOTTOMLEFT 
 左下 
 
 
 AnchorPosition.BOTTOMRIGHT 
 右下 
 
 
 AnchorPosition.MIDDLECENTER 
 正中 
 
 
 AnchorPosition.MIDDLELEFT 
 左中 
 
 
 AnchorPosition.MIDDLERIGHT 
 右中 
 
 
 AnchorPosition.TOPCENTER 
 正上 
 
 
 AnchorPosition.TOPLEFT 
 左上 
 
 
 AnchorPosition.TOPRIGHT 
 右下 
 
 
 

    BitmapConversionOptions  
 位图转换选项。 
  method   BitmapConversionType  
 转换方法。 
 
 
 
  
  
 
 
 BitmapConversionType.CUSTOMPATTERN 
 自定图案 
 
 
 BitmapConversionType.DIFFUSIONDITHER 
 扩散仿色 
 
 
 BitmapConversionType.HALFTHRESHOLD 
 50%阈值 
 
 
 BitmapConversionType.HALFTONESCREEN 
 半调网屏 
 
 
 BitmapConversionType.PATTERNDITHER 
 图案仿色 
 
 
 
  frequency   number  
 半调网屏方法时的频率。 
  查看图片  
  
  angle   number  
 半调网屏方法时的角度 (-180~180)。 
  shape   BitmapHalfToneType  
 半调网屏方法时的形状。 
 
 
 
  
  
 
 
 BitmapHalfToneType.CROSS 
 十字线 
 
 
 BitmapHalfToneType.DIAMOND 
 菱形 
 
 
 BitmapHalfToneType.ELLIPSE 
 椭圆 
 
 
 BitmapHalfToneType.LINE 
 直线 
 
 
 BitmapHalfToneType.ROUND 
 圆 
 
 
 BitmapHalfToneType.SQUARE 
 正形 
 
 
 
  patternName&nbsp;  string  
 自定义图案方法时的图案名称。 

    BMPSaveOptions  
  alphaChannels   boolean  
 为真保存 alpha 通道。 
  depth   BMPDepthType  
 深度。 
 
 
 
 BMPDepthType 
 
 
 BMPDepthType.BMP_A1R5G5B5 
  查看图片  
 
 
 BMPDepthType.BMP_A4R4G4B4 
 
 
 BMPDepthType.BMP_A8R8G8B8 
 
 
 BMPDepthType.BMP_R5G6B5 
 
 
 BMPDepthType.BMP_R8G8B8 
 
 
 BMPDepthType.BMP_X1R5G5B5 
 
 
 BMPDepthType.BMP_X4R4G4B4 
 
 
 BMPDepthType.BMP_X8R8G8B8 
 
 
 BMPDepthType.EIGHT 
 
 
 BMPDepthType.FOUR 
 
 
 BMPDepthType.ONE 
 
 
 BMPDepthType.SIXTEEN 
 
 
 BMPDepthType.THIRTYTWO 
 
 
 BMPDepthType.TWENTYFOUR 
 
 
 
  flipRowOrder   boolean  
 翻转行序。 
  osType   OperatingSystem  
 系统类型。 
 
 
 
 OperatingSystem 
 
 
 OperatingSystem.OS2 
 OS2 
 
 
 OperatingSystem.WINDOWS 
 Windows 
 
 
 
  rleCompression   boolean  
 使用 RLE 压缩，只在  osType  为  OperatingSystem.WINDOWS  时有效。 
    GIFSaveOptions  
  colors   number  
 色彩数。 
  dither   Dither  
 仿色算法。 
 
 
 
 Dither 
 
 
 Dither.NONE 
 无仿色 
 
 
 Dither.DIFFUSION 
 扩散 
 
 
 Dither.NOISE 
 杂色 
 
 
 Dither.PATTERN 
 图案 
 
 
 
  ditherAmount   number  
 仿色数量。 
  forced   ForcedColors  
 强制。 
 
 
 
  
  
 
 
 ForcedColors.BLACKWHITE 
 黑白 
 
 
 ForcedColors.NONE 
 无 
 
 
 ForcedColors.PRIMARIES 
 三原色 
 
 
 ForcedColors.WEB 
 Web 
 
 
 
  interlaced   boolean  
 交错。 
  matte   MatteType  
 杂边。 
 
 
 
  
  
 
 
 MatteType.BACKGROUND 
 背景色 
 
 
 MatteType.BLACK 
 黑色 
 
 
 MatteType.FOREGROUND 
 前景色 
 
 
 MatteType.NETSCAPE 
 Netscape 灰 
 
 
 MatteType.NONE 
 无 
 
 
 MatteType.SEMIGRAY 
 50% 灰 
 
 
 MatteType.WHITE 
 白 
 
 
 
  palette   PaletteType  
 调板。 
 
 
 
  
  
 
 
 PaletteType.EXACT 
 实际 
 
 
 PaletteType.LOCALADAPTIVE 
 局部（随样性） 
 
 
 PaletteType.LOCALPERCEPTUAL 
 局部（可感知） 
 
 
 PaletteType.LOCALSELECTIVE 
 局部（可选择） 
 
 
 PaletteType.MACOSPALETTE 
 系统（Mac OS） 
 
 
 PaletteType.MASTERADAPTIVE 
 全部（随样性） 
 
 
 PaletteType.MASTERPERCEPTUAL 
 全部（可感知） 
 
 
 PaletteType.MASTERSELECTIVE 
 全部（可选择） 
 
 
 PaletteType.PREVIOUSPALETTE 
 上一个 
 
 
 PaletteType.UNIFORM 
 平均 
 
 
 PaletteType.WEBPALETTE 
 Web 
 
 
 PaletteType.WINDOWSPALETTE 
 系统（Windows） 
 
 
 
  查看图片  
  preserveExactColors   boolean  
 保留实际颜色，当仿色为扩撒时有效。 
  transparency   boolean  
 透明度。 
    JPEGSaveOptions  
  查看图片  
  embedColorProfile   boolean  
 嵌入色彩配置文件。 
  formatOptions   FormatOptions  
 
 
 
 FormatOptions.OPTIMIZEDBASELINE 
 基线已优化 
 
 
 FormatOptions.PROGRESSIVE 
 连续 
 
 
 FormatOptions.STANDARDBASELINE 
 基线（”标准”） 
 
 
 
  scans   number  
 扫描。 
  matte   MatteType  
 杂边。 
  quality   number  
 品质（0~12）。 
  查看图片  
    PNGSaveOptions  
  compression   number  
 压缩 （0-9）。 
  interlaced   boolean  
 交错。 

    BlendMode  
 混合模式。 
 
 
 
  
 
 
 BlendMode.NORMAL 
 正常 
 
 
 BlendMode.DISSOLVE 
 溶解 
 
 
 BlendMode.DARKEN 
 变暗 
 
 
 BlendMode.MULTIPLY 
 正片叠底 
 
 
 BlendMode.COLORBURN 
 颜色加深 
 
 
 BlendMode.LINEARBURN 
 线性加深 
 
 
 BlendMode.COLORBLEND 
 颜色 
 
 
 BlendMode.COLORDODGE 
 颜色减淡 
 
 
 BlendMode.DIFFERENCE 
 差分 
 
 
 BlendMode.LIGHTEN 
 变亮 
 
 
 BlendMode.SCREEN 
 滤色 
 
 
 BlendMode.LINEARDODGE 
 线性减淡 
 
 
 BlendMode.DIVIDE 
 划分 
 
 
 BlendMode.EXCLUSION 
 排除 
 
 
 BlendMode.HARDLIGHT 
 强光 
 
 
 BlendMode.HARDMIX 
 实色混合 
 
 
 BlendMode.HUE 
 色调 
 
 
 BlendMode.LINEARLIGHT 
 线性光 
 
 
 BlendMode.LUMINOSITY 
 明度 
 
 
 BlendMode.OVERLAY 
 叠加 
 
 
 BlendMode.PASSTHROUGH 
 穿透 
 
 
 BlendMode.PINLIGHT 
 点光 
 
 
 BlendMode.SATURATION 
 饱和度 
 
 
 BlendMode.SOFTLIGHT 
 柔光 
 
 
 BlendMode.SUBTRACT 
 减去 
 
 
 BlendMode.VIVIDLIGHT 
 亮光 
 
 
 

    ExportOptionsSaveForWeb  
 存储为 Web 所用格式所用选项。 
  blur   number  
 模糊图像，默认 0.0 不模糊。 
  colorReduction   ColorReductionType  
 减低颜色深度算法。 
 
 
 
  
 
 
 olorReductionType.PERCEPTUAL 
 可感知 
 
 
 ColorReductionType.SELECTIVE 
 可选择 
 
 
 ColorReductionType.ADAPTIVE 
 随样性 
 
 
 ColorReductionType.RESTRICTIVE 
 受限 
 
 
 ColorReductionType.CUSTOM 
 自定义 
 
 
 ColorReductionType.BLACKWHITE 
 黑 – 白 
 
 
 ColorReductionType.GRAYSCALE 
 灰度 
 
 
 ColorReductionType.MACINTOSH 
 Mac OS 
 
 
 ColorReductionType.WINDOWS 
 Windows 
 
 
 
  查看图片  
  colors   number  
 颜色数。默认 256。 
  dither   Dither  
 仿色算法。 
 
 
 
 Dither 
 
 
 Dither.NONE 
 无仿色 
 
 
 Dither.DIFFUSION 
 扩散 
 
 
 Dither.NOISE 
 杂色 
 
 
 Dither.PATTERN 
 图案 
 
 
 
  查看图片  
  ditherAmount   number  
 仿色数量，当仿色设置为“Dither.DIFFUSION：扩散”的时候有效，指定扩散的大小。 
  format   SaveDocumentType  
 导出格式。可以使用下面 4 种。 
 
 
 
  
  
 
 
 SaveDocumentType.COMPUSERVEGIF 
 GIF 
 
 
 SaveDocumentType.BMP 
 BMP 
 
 
 SaveDocumentType.PNG 
 PNG 
 
 
 SaveDocumentType.JPEG 
 JPEG 
 
 
 

  includeProfile   boolean  
 嵌入颜色配置文件。 
  查看图片  
  interlaced   boolean  
 交错。 
  查看图片  
  lossy   number  
 损耗。允许数据丢失的数量，默认为 0。 
  matteColor   RGBColor  
 杂边。杂边颜色。 
  optimized&nbsp; boolean   
 优化，导出 JPEG 格式时可用。 
  查看图片  
  PNG8   boolean  
 为真保存为 PNG8 ，否则保存为 PNG24。 
  quality   number  
 品质 。（0~100）。 
  transparency   boolean  
 透明度。是否存储图像透明度，导出为 GIF 或 PNG 时有效。 
  transparencyDither   Dither  
 透明度仿色算法。 
 
 
 
 Dither 
 
 
 Dither.NONE 
 无仿色 
 
 
 Dither.DIFFUSION 
 扩散 
 
 
 Dither.NOISE 
 杂色 
 
 
 Dither.PATTERN 
 图案 
 
 
 
  transparencyAmount   number  
 透明度仿色数量。当透明度仿色设置为 Dither.DIFFUSION：扩撒 的时候有效，指定扩撒的大小。 

  webSnap   number  
 Web 靠色。 
  查看图片  
    ElementPlacement  
 相对位置。 
 
 
 
 
 
 ElementPlacement.INSIDE 
 插入图层组 
 
 
 ElementPlacement.PLACEATBEGINNING 
 图层组首位 
 
 
 ElementPlacement.PLACEATEND 
 图层组末位 
 
 
 ElementPlacement.PLACEBEFORE 
 之前 
 
 
 ElementPlacement.PLACEAFTER 
 之后 
 
 
 
 
 

    Direction  
 文本取向。 
 
 
 
  
  
 
 
 Direction.HORIZONTAL 
 水平 
 
 
 Direction.VERTICAL 
 垂直 
 
 
 

    RasterizeType  
 栅格化类型。 
 
 
 
  
  
 
 
 RasterizeType.ENTIRELAYER 
 栅格化图层 
 
 
 RasterizeType.FILLCONTENT 
 栅格化填充内容（生成矢量蒙版） 
 
 
 RasterizeType.LAYERCLIPPINGPATH 
 栅格化矢量蒙版 
 
 
 RasterizeType.TEXTCONTENTS 
 栅格化文字 
 
 
 RasterizeType.LINKEDLAYERS 
 栅格化链接的图层 
 
 
 RasterizeType.SHAPE 
 栅格化形状 
 
 
 
    Guide  
 参考线。 
  direction   Direction  
 参考线方向。 
 
 
 
 Direction 
  
 
 
 Direction.HORIZONTAL 
 水平 
 
 
 Direction.VERTICAL 
 垂直 
 
 
 
  coordinate     UnitValue   
 参考线方向。 
  activeDocument.guides.add (Direction.HORIZONTAL,UnitValue("333px"))  
 
 



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)