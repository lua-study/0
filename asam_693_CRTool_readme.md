#CRTool

##概述
Unity3D Cubemap渲染 插件

##问题
- 有时，发现一些Unity3D资源包中的场景的环境效果不错，希望将其渲染成Cubemap供天空盒使用。
- Unity3D场景中需要制作一些反射效果的材质，例如玻璃，金属等，需要将场景渲染成Cubemap，
  结合反射Shader表现效果。

##条件
- Unity3D提供ScriptableWizard类快速创建简易扩展编辑器窗口。
- Unity3D提供Camera.RenderToCubemap方法渲染Cubemap。

##方案
- 编写扩展编辑器窗口，指定场景中心位置，渲染层级，目标Cubemap文件。
- 设置摄像机参数，渲染场景到Cubemap文件。

##实现
- CREditor.cs 绘制扩展编辑器窗口，渲染场景到Cubemap中。﻿

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)