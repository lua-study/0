# krpano
Krpano 可以方便快速的构建全景场景或全景视频([demo][demo])

## 目录

* [Krpano Droplet](#krpano-droplet)
	* [MAKE PANO (NORMAL)](#make-pano-normal)
	* [MAKE PANO (MULTIRES)](#make-pano-multires)
	* [MAKE PANO (SINGLESWF)](#make-pano-singleswf)
	* [MAKE PANO (FLAT)](#make-pano-flat)
	* [MAKE VTOUR (NORMAL)](#make-vtour-normal)
	* [MAKE VTOUR (MULTIRES)](#make-vtour-multires)
	* [MAKE OBJECT](#make-object)
	* [Convert SPHERE to CUBE](#convert-sphere-to-cube)
	* [Convert CUBE to SPHERE](#convert-cube-to-sphere)
	* [Encrypt XML](#encrypt-xml)
* [vtour 文件夹说明](#vtour-文件夹说明)
	* [vtour 文件夹结构](#vtour-文件夹结构)
	* [vtour 运作机制](#vtour-运作机制)
* [krpano XML结构](#krpano-xml结构)
	* [Krpano 内置元素说明](#krpano-内置元素说明)
* [常用设置](#常用设置)
	* [小行星开场](#小行星开场)
	* [加载动画](#加载动画)
	* [修改右键菜单](#修改右键菜单)
	* [自定义热点](#自定义热点)
	* [隐藏皮肤](#隐藏皮肤)
	* [添加动态热点](#动态热点)
	* [动态热点添加始终显示的文字](#动态热点添加始终显示的文字)
	* [热点和或图层在鼠标点击或鼠标悬停时进入动态模式](#热点和或图层在鼠标点击或鼠标悬停时进入动态模式)
	* [拖拽热点](#拖拽热点)
	* [添加简单的全景视频](#添加简单的全景视频)
	* [添加雨雪特效](#添加雨雪特效)
	* [自动旋转](#自动旋转)
	* [无按钮控制的自动旋转](#无按钮控制的自动旋转)
	* [按钮控制的自动旋转](#按钮控制的自动旋转)
	* [添加陀螺仪](#添加陀螺仪)
	* [场景过渡效果](#场景过渡效果)
	* [隐藏显示热点](#隐藏显示热点)
	* [获取全景视频进度](#获取全景视频进度)
	* [用js控制全景](#用js控制全景)

----------

原文链接：  
[https://krpano.milly.me/][link1]
[http://www.krpano360.com/][link2]

GitHub: [nodeKrpano][github]


## Krpano Droplet

### MAKE PANO (NORMAL)
**用法说明**

- 生成普通 (=单分辨率) 全景
- 制作典型的 360 度全景
- 全部全景图将会一次性载入. 默认下方块最大变长为 2048 像素(可以在配置文件中修改)
- 包括默认的导航皮肤
- 支持 ``Flash`` 和 ``HTML5``

**Droplet 说明**

- 配置文件: ``normal.config``
- 默认模版/皮肤配置文件: ``defaultbuttons.skin``


----------


### MAKE PANO (MULTIRES)
**用法说明**

- 生成多分辨率全景
- 制作所有类型的全景
- 只有特定的切片在需要时载入 没有尺寸/分辨率限制
- 包含默认的导航皮肤
- 支持 ``Flash`` 和 ``HTML5``

**Droplet 说明**

配置文件: ``multiresconfig``
默认模版/皮肤配置文件: ``defaultbuttonsskin``


----------


### MAKE PANO (SINGLESWF)
**用法说明**

- 生成普通 (=单分辨率) 全景同时将所有文件嵌在一个SWF文件中只输出一个SWF文件和一个HTML文件
- 制作典型的360度全景
- 全部全景图将会一次性载入 默认下方块最大变长为2048像素(可以在配置文件中修改)
- 包含默认的导航皮肤
- 仅支持 ``Flash``

**Droplet 说明**

配置文件: ``singleswfconfig``
默认模版/皮肤配置文件: ``defaultbuttonsskin``


----------


### MAKE PANO (FLAT)
**用法说明**

- 生成平面切片多分辨率图像
- 制作平面图像 输出时既定为平面图像
- 只有特定的切片在需要时载入 没有尺寸/分辨率限制
- 包含有默认导航按钮的皮肤，针对特定的视角
- 支持 ``Flash`` 与 ``HTML5``

**Droplet 说明**

- 配置文件: ``flatconfig``
- 默认模版/皮肤配置文件: ``flatxml / flatskinxml``


----------


### MAKE VTOUR (NORMAL)
**用法说明**

- 生成普通 (=单分辨率) 全景并将它们整合到一个虚拟漫游中
- 制作典型的 360 度全景
- 全部全景图将会一次性载入 默认下方块最大变长为 2048 像素(可以在配置文件中修改)
- 包含一个包括导航按钮、可滚动缩略图以及可选择必应地图以及重力感应插件的默认皮肤
- 支持 ``Flash`` 和 ``HTML5``

**Droplet 说明**

- 配置文件: ``vtour-normalconfig``
- 默认模版/皮肤配置文件: ``vtourskin-thumbnails-bingmaps-gyroskin``


----------


### MAKE VTOUR (MULTIRES)
**用法说明**

- 生成多分辨率全景并将它们整合到一个虚拟漫游中
- 制作所有类型全景图像
- 只有特定的切片在需要时载入 没有尺寸/分辨率限制
- 包含一个包括导航按钮、可滚动缩略图以及可选择必应地图以及重力感应插件的默认皮肤
- 支持 ``Flash`` 和 ``HTML5``

**Droplet 说明**

- 配置文件: ``vtour-multiresconfig``
- 默认模版/皮肤配置文件: ``vtourskin-thumbnails-bingmaps-gyroskin``


----------


### MAKE OBJECT
**用法说明**

- 生成若干个平面多分辨率图像并将它们整合到一个可缩放旋转的 360 物体影像中
- 制作平面图像物体 所有物体图片的尺寸必须一致
- 只有特定的切片在需要时载入 没有尺寸/分辨率限制
- 包含一个特定的控制物体的皮肤
- 仅支持 ``Flash``

**Droplet 说明**

- 配置文件: ``objectconfig``
- 默认模版/皮肤配置文件: ``objectxml / objectskinxml``
 

----------


### Convert SPHERE to CUBE
**用法说明**

- 将球面图像转换至立方体图
- 输出的立方体格式、尺寸以及图像尺寸可以在配置文件中修改

**Droplet 说明**

- 配置文件: ``convertdropletsconfig``


----------


### Convert CUBE to SPHERE
**用法说明**

- 将六张立方体图像转换成一张球面全景图
- 输出的图像尺寸和格式可以在配置文件中修改

**Droplet 说明**

- 配置文件: ``convertdropletsconfig``


----------


### Encrypt XML
**用法说明**

- 将 ``xml`` 文件拖放进 ``droplet`` 进行加密
- 加密过程中 ``xml`` 文件会自动被压缩


----------


### 自定义 droplet

如果内置 ``droplet`` 不能满足需求或者需要对一些参数进行自定义。只要复制并重命名一个配置文件与皮肤配置文件，然后复制并重命名一个 ``droplet ``，修改里面的配置路径即可。


----------


## vtour 文件夹说明

### vtour 文件夹结构

```
vtour/
| -- panos/             #存放全景切片图片的文件夹
| -- skin/              #存放皮肤相关文件
| -- plugins/           #用来存放插件
| -- tour.swf           #krpano flash viewer
| -- tour.js            #krpano HTML5 viewer
| -- tour.xml           #生成全景的相关配置
| -- tour.html          #用来浏览全景的页面，需要本地服务环境
| -- tour_editor.html   #添加热点（hotspot）与初始化视角的设置
```

### vtour 运作机制

```html
  
  
 
embedpano({
    swf: "tour.swf", //有则表示加载flash引擎，如果设置html5:only则不需要该值
    xml: "tour.xml", //启动时的配置文件
    target: "pano", //要渲染到的目标容器ID
    html5: "only", //如果有需要用到flash，可设置为auto
    //id: "krpanoSWFObject", //默认的krpano对象，每一个viewer对应唯一id，与JS交互时要用到
    mobilescale: 1.0, //移动设备缩放，1表示不缩放，默认0.5
    passQueryParameters: false //是否接受URL传参，例如：tour.html?html5=only&startscene=scene2
});
 
```

## krpano XML结构

```xml
 
     
     
     
     
     
     
     
     
     
     
     
     
     
     
     
     
     
     
     
     
     
     
     
     
 
```

### Krpano 内置元素说明

**01.krpano**

``krpano`` 元素是 ``krpano xml`` 文件的根元素。任何一个 ``krpano xml`` 文件内的其它元素都要被 ``krpano`` 元素所嵌套。

**02.include**

``include`` 元素可引入其它 ``xml`` 文件的内容，例如我们常要用到的 ``vtourskin.xml`` 就是使用 ``include`` 嵌入到主 ``xml`` 中。

**03.preview**

预览图设置，也就是全景图完全载入之前的模糊图像，但因为体积较小，因此载入速度较快，会在全景图之前先载入，避免黑屏。

**04.image**

image 元素控制全景图设置，包括全景图类型，渐进分辨率切片显示等。

**05.view**

view 元素控制全景的视野，例如起始视角、视角限制与缩放等等。当要设置限制视角或设定特定的初始视角时，需要自行设定或使用插件获取代码。

**06.area**

area 元素控制全景图在浏览器窗口中显示区域大小。

**07.display**

控制全景图的显示品质。

**08.control**

设置鼠标、键盘以及触摸设备对全景浏览的控制方式。

**09.cursors**

设置鼠标光标样式。

**10.autorotate**

控制自动旋转。

**11.plugin**

用来调用插件、插入图片或生成容器。

**12.layer**

与 ``plugin`` 作用相同，只是名称不同。

**13.hotspot**

热点，可在 3D 空间中插入图片，使之随着 3D 空间一同运动，可制作很多特效。

**14.style**

可以保存其它元素的属性子集。

**15.events**

可调用各类型事件，例如全景载入的不同阶段以及鼠标触发的不同行为等。

**16.action**

自定义动态代码。

**17.contextmenu**

定义右键菜单的内容。

**18.network**

控制图像的下载、缓存与解码。

**19.menory**

控制全景图在设备中的存储。

**20.security**

``Flashplayer`` 和 ``HTML5`` 相关的安全/跨域设置。

**21.lensflareset**

镜头眩光的设置（目前只能在 ``flash`` 下使用）。

**22.lensflare**

生成镜头眩光（目前只能在 ``flash`` 下使用）。

**23.data**

可放置任意的数据。

**24.scene**

可放置任意 ``krpano`` 元素。每个 ``scene`` 元素只有在被 ``loadscene`` 时才会被载入到浏览器进行解析。

## 常用设置
### 小行星开场
开启小行星，先找到 ``tour.xml`` ，然后搜索 ``littleplanetintro`` 将其值设置为 ``true`` 即可。

```xml
 
```

### 加载动画
在官方的案例文件夹中找到 ``loading-progress`` 这个文件夹，将需要的文件内容复制到项目中的 ``skin`` 文件夹，然后在 ``tour.xml`` 文件中引入该文件即可，这样重新打开就可以看到有动态的进度条了。

```xml
 
```

### 修改右键菜单
找到引入的皮肤文件，默认在 ``vtourskin.xml`` ，然后修改下面这些地方即可自定义右键菜单，但像版权、全屏菜单即使删除也会存在。

```xml
 
     
 
```
  
  


**contextmenu元素**

- ``caption`` 右键菜单显示的文字
- ``onclick`` 控制点击后执行的动作，动作由 ``action`` 定义
- ``showif`` 显示条目的条件
- ``devices`` 控制在 ``flash/webgl`` 哪个模式中出现
- ``separator`` 显示分隔符来分隔菜单

### 自定义热点

配置 `` `` 中 ``style`` 的属性对应的元素（``skin``对应的文件夹）

```xml
 
```

```xml
 
	 
```

### 隐藏皮肤

```xml
 
	 
	set(events[skin_events].name, null);
  	for(set(i,0), i LT layer.count, inc(i), 
	copy(layername, layer[get(i)].name);
	subtxt(namestart, get(layername), 0, 5);
	if(namestart == 'skin_', removelayer(get(layername)); dec(i); );
  );
 
```

### 动态热点

在 `tour.xml` 空白处的scene标签的外面，添加动作代码

```xml
 
	 
	registerattribute(xframes, calc((imagewidth / %1) BOR 0));
	registerattribute(yframes, calc((imageheight / %2) BOR 0));
	registerattribute(frames, calc(xframes * yframes));
	registerattribute(frame, 0);
 
	set(crop, '0|0|%1|%2');
 
	setinterval(calc('crop_anim_' + name), calc(1.0 / %3),
		if(loaded,
			inc(frame);
			if(frame GE frames, if(onlastframe !== null, onlastframe() ); set(frame,0); );
			mod(xpos, frame, xframes);
			div(ypos, frame, xframes);
			Math.floor(ypos);
			mul(xpos, %1);
			mul(ypos, %2);
			calc(crop, xpos + '|' + ypos + '|%1|%2');
		  ,
			clearinterval(calc('crop_anim_' + name));
		  );
	  );
 
```

在 `hotspot` 或 `layer` 的代码添加代码， `do_crop_animation(每帧宽,每帧高,fps)`

```xml
url="explosion.png"  onloaded="do_crop_animation(100,100, 60)"
```

### 动态热点添加始终显示的文字

显示 `  title` 中的文字

```xml
 
```

或者在 `  text` 中添加显示自定义的文字

```xml
 
```

在热点的 `onload` 事件中加上 `add_all_the_time_tooltip()`

```xml
onloaded="do_crop_animation(64,64, 60);add_all_the_time_tooltip()"
```

空白处加上 `action`

```xml
 
	    txtadd(tooltipname, 'tooltip_', get(name));
	    addplugin(get(tooltipname));
	    txtadd(plugin[get(tooltipname)].parent, 'hotspot[', get(name), ']');
	    set(plugin[get(tooltipname)].url,'%SWFPATH%/plugins/textfield.swf');
	    set(plugin[get(tooltipname)].align,top);
	    set(plugin[get(tooltipname)].edge,bottom);
	    set(plugin[get(tooltipname)].x,0);
	    set(plugin[get(tooltipname)].y,0);
	    set(plugin[get(tooltipname)].autowidth,true);
	    set(plugin[get(tooltipname)].autoheight,true);
	    set(plugin[get(tooltipname)].vcenter,true);
	    set(plugin[get(tooltipname)].background,true);
	    set(plugin[get(tooltipname)].backgroundcolor,0x000000);
	    set(plugin[get(tooltipname)].roundedge,5);
	    set(plugin[get(tooltipname)].backgroundalpha,0.65);
	    set(plugin[get(tooltipname)].padding,5);
	    set(plugin[get(tooltipname)].border,false);
	    set(plugin[get(tooltipname)].glow,0);
	    set(plugin[get(tooltipname)].glowcolor,0xFFFFFF);
	    set(plugin[get(tooltipname)].css,'text-align:center; color:#FFFFFF; font-family:MicrosoftYahei;  font-size:24px;');
	    if(device.mobile,set(plugin[get(tooltipname)].css,'text-align:center; color:#FFFFFF; font-family:MicrosoftYahei; font-weight:bold; font-size:24px;');
	    	);
	    set(plugin[get(tooltipname)].textshadow,0);
	    set(plugin[get(tooltipname)].textshadowrange,6.0);
	    set(plugin[get(tooltipname)].textshadowangle,90);
	    if(text == '' OR text === null,
	    copy(plugin[get(tooltipname)].html,scene[get(linkedscene)].title),
	    copy(plugin[get(tooltipname)].html,text)
	    );    
	    set(plugin[get(tooltipname)].enabled,false);	
 
```
### 热点和或图层在鼠标点击或鼠标悬停时进入动态模式

```xml
 	
		if(hotspot[get(name)].animated === null OR hotspot[get(name)].animated == false,
		    set(hotspot[get(name)].animated,true);
			setinterval(calc('crop_anim_' + name), calc(1.0 / %3),			
					inc(frame);
					if(frame GE frames, if(onlastframe !== null, onlastframe() ); set(frame,0); );
					mod(xpos, frame, xframes);
					div(ypos, frame, xframes);
					Math.floor(ypos);
					mul(xpos, %1);
					mul(ypos, %2);
					calc(crop, xpos + '|' + ypos + '|%1|%2');			  				
			  );
			  ,
            set(hotspot[get(name)].animated,false);  
			clearinterval(calc('crop_anim_' + name));
			set(crop, '0|0|%1|%2');	
		  );
 
 
 
		registerattribute(xframes, calc((imagewidth / %1) BOR 0));
		registerattribute(yframes, calc((imageheight / %2) BOR 0));
		registerattribute(frames, calc(xframes * yframes));
		registerattribute(frame, 0);
		set(crop, '0|0|%1|%2');	
 
 
 
 
 
 
 
 
```

以上代码执行了一次动态循环后，序列图停留在第一帧，如果只是需要执行一次动态循环，并且序列图停留在最后一帧的话，那么 `do_crop_animation_onclick` 需更改（区别就是 `frame` 这个变量没有重置为 0 ，并且没有重新设置 `crop` ）

```xml
  
    if(hotspot[get(name)].animated === null OR hotspot[get(name)].animated == false,
        set(hotspot[get(name)].animated,true);
      setinterval(calc('crop_anim_' + name), calc(1.0 / %3),  
 
          inc(frame);
          if(frame GE frames, if(onlastframe !== null, onlastframe() ); add(frame,frames,-1); );
          mod(xpos, frame, xframes);
          div(ypos, frame, xframes);
          Math.floor(ypos);
          mul(xpos, %1);
          mul(ypos, %2);
          calc(crop, xpos + '|' + ypos + '|%1|%2');               
        );
        ,
        set(hotspot[get(name)].animated,false);  
      clearinterval(calc('crop_anim_' + name));
     
      );
 
```

### 拖拽热点

在 ` ` 中添加代码

```xml
	ondown="draghotspot();"
```

添加 action 代码

```xml
	 
		spheretoscreen(ath, atv, hotspotcenterx, hotspotcentery, 'l');
		sub(drag_adjustx, mouse.stagex, hotspotcenterx);
		sub(drag_adjusty, mouse.stagey, hotspotcentery);
		asyncloop(pressed,
			sub(dx, mouse.stagex, drag_adjustx);
			sub(dy, mouse.stagey, drag_adjusty);
			screentosphere(dx, dy, ath, atv);
		  );
	 
```

### 添加简单的全景视频

从 `viewer/examples/videopano` 中复制 `vtourskin.xml`，在主xml 添加代码

```xml
	 
		 
		 

		 
		 

		 
		 
			 
		 

		 
		 

		 
		 
			videointerface_addsource('1024x512', '%CURRENTXML%/video/video-1024x512.mp4|%CURRENTXML%/video/video-1024x512.webm|%CURRENTXML%/video/iphone-audio.m4a', '%CURRENTXML%/video/video-1024x512-poster.jpg');
			videointerface_addsource('1920x960', '%CURRENTXML%/video/video-1920x960.mp4|%CURRENTXML%/video/video-1920x960.webm|%CURRENTXML%/video/iphone-audio.m4a', '%CURRENTXML%/video/video-1920x960-poster.jpg');
			
			if(device.ios,
				 
				videointerface_play('1024x512');
			  ,
				videointerface_play('1920x960');
			  );
		 
	 
```
 
### 添加雨雪特效

1. 添加文件 [http://pan.baidu.com/s/1gfLTx6N][snow] 密码：6shh  
  
2. 在 `viewer\plugins` 拷贝 `snow.swf` 和 `snow.js`  

3. 添加  ` `  
	
	目前可选的特效
	- 默认雪 `onstart='defaultsnow();'`
	- 雪球 `onstart='snowball();'`
	- 雪花 `onstart='snowflakes();'`
	- 银色星星 `onstart='silverstars();'`
	- 金色星星 `onstart='goldenstars();'`
	- 心形 `onstart='hearts();'`
	- 笑脸 `onstart='smileys();'`
	- 钱 `onstart='money();'`
	- 雨 `onstart='rain();'`
	- 大雨 `onstart='heavyrain();'`

4. 在 ` ` 添加代码

```xml
 
``` 

### 自动旋转

添加代码

```xml
 
```
- `waittime` 代表在最近一次用户交互行为之后要开始自动旋转之前的等待时间。以秒为单位。  
- `speed` 为旋转速度。当该数值为正值时向右旋转，为负值时向左旋转。
- `horizon` 为场景在自动旋转时将达到的水平位置。
- `tofov` 为旋转中要达到的视场角。


### 无按钮控制的自动旋转
自动旋转场景，场景旋转一圈后自动进入下一个场景，最后一个场景浏览结束后，进入第一个场景。需添加如下代码：

```xml
 
```

修改 ` ` 中的代码

```xml
 
if(startscene === null, copy(startscene,scene[0].name));
loadscene(get(startscene), null, MERGE);
if(autorotate.enabled,bombtimer(0));
 
```

在 `xml` 文件中加入下面的代码

```xml
 
 
set(autorotate.enabled,true);
set(bt,%1);
add(bt,1);
delayedcall(1, bombtimer(get(bt)));
copy(bt_1,autorotate.speed);
Math.abs(bt_1);
div(bt_2,360,bt_1);
add(bt_2,autorotate.waittime);
if(bt GE bt_2, set(bt,0); nextscene(););
 
 
set(ns, get(scene[get(xml.scene)].index));
set(maxs, get(scene.count));
add(ns,1);
if(ns == maxs, set(ns,0));
loadscene(get(scene[get(ns)].name), null, MERGE, BLEND(1.5));
 
```

### 按钮控制的自动旋转
添加代码

```xml
 
```

在对应的按钮，通常为 ` ` 标签中找到 `onclick` 属性替换，如果没有则直接添加

```xml
 
```

### 添加陀螺仪

加载插件（此方法与上述隐藏皮肤的方法冲突）

```xml
 
 
 
		set(layer[gyrobutton].visible, true);
 
```

控制按钮

```xml
 
```

默认皮肤开启陀螺仪功能（在 `tour.xml` 的 `skin_settings`中设置）

```
gyro="true"
```

在 `tour.xml` 的 `include` 的下一行添加

```xml
 
```

### 场景过渡效果

修改全部过渡效果，只需修改 ` `中以下代码

```xml
loadscene_blend="OPENBLEND(0.5, 0.0, 0.75, 0.05, linear)"
loadscene_blend_prev="SLIDEBLEND(0.5, 180, 0.75, linear)"
loadscene_blend_next="SLIDEBLEND(0.5,   0, 0.75, linear)"
```
如果想为某个特殊的 `loadscene` 动作加上不一样的过渡效果，在主 `xml` 的 `scene` 外加入以下代码

```xml
 
 
 
 
 
 
 
 
 
 
 
 
```

修改 `loadscene(scenename, null, MERGE, get(blendmodes[black-out].blend));`

```xml
 
```

### 隐藏显示热点
添加 ` `

```xml
 
  tween(%1.alpha,0,0.5);
  wait(1);
  set(%1.visible,false);
 

 
  set(%1.alpha,0);
  set(%1.visible,true);
  tween(%1.alpha,1,0.5);
  tween(%1.scale,1,0.5,easeOutBack);
 
```

使用
```xml
 
 
	hideBox(hotspot[spot1]);
 
```

### 获取全景视频进度

```xml
 
 
  setinterval(skin_video_seek_updates0, 0.1, skin_video_updatetime0())
 

 
  setStop(4,video_pause_events(););
 
		
 
  copy(t1, plugin[video].time);
  if(t1 GT %1,%2);
 
 
 
 
  plugin[video].pause();
  clearinterval(skin_video_seek_updates0);
 
```

### 用js控制全景

js控制场景跳转

```javascript
// 场景跳转 index:0,1,2
function krpanoTo(index){
	var krpano = document.getElementById("krpanoSWFObject");
	// 跳转到场景1
	if(index == 0){ krpano.call("to0"); }
	// 跳转到场景2
	if(index == 1){ krpano.call("to1"); }
	// 跳转到场景3
	if(index == 2){ krpano.call("to2"); }
}
```

```xml
 
	loadscene("scene_index1", null, MERGE);
 

 
	loadscene("scene_index2", null, MERGE);
 

 
	loadscene("scene_index3", null, MERGE);
 
```


[link1]:https://krpano.milly.me/
[link2]:http://www.krpano360.com/
[github]:https://github.com/NalvyBoo/nodeKrpano/
[snow]:http://pan.baidu.com/s/1gfLTx6N
[demo]:http://test.go.163.com/go/2015/public/team/ningbo/krpano/comn01/


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)