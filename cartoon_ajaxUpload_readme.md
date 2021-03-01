AjaxUpload
========
>
@author：yangjian102621@gmail.com 

插件描述:
--------
javascript异步上传插件，包含3个子项目BUpload, JUpload, TUpload.
* BUpload : 基于HTML5， UI仿百度编辑器的图片上传, 支持图片上传，浏览图片，和图片搜索，支持图片预览，有进度条
* TUpload : 基于HTML5， UI仿腾讯的QQ空间上传图片，支持图片预览，有进度条。
* JUpload : 基于iframe的异步上传。


插件依赖:
-------
* jQuery-1.7.1以上版本

在线预览
========
### 在线演示: http://d.r9it.com/ajaxupload/

版本更新记录
======
### v1.3.1
* 修复 BUpload 组件的文件管理默认文件后缀名的不显示图标的bug
* 删除 TUpload 组件，其功能和使用方法基本跟 BUpload 重复，只是UI不一样，这样导致需要维护两份代码，
所以就索性就移除它了，精简项目。
* 更新了 demo 和 API 介绍文档， 点击缩略图可以预览图片

### v1.3.0
* 修复BUpload组件，管理 API 的分页第一条数据获取不到的bug
* 分别给 JUpload, TUpload, BUpload 三个组件实现css的自动加载功能，不需要再手动引入css
* 修复了BUpload 删除全部添加图片的时候不显示添加按钮的bug
* JUpload 新增html5 上传支持，自动判断浏览器是否支持 H5, 如果支持自动使用 H5 API 上传，不支持就使用 iframe 上传 
* 新增了一些回调接口，onStart, onCompleted 
* 重构上传的后端php文件，使用统一的 JsonResult 数据结构返回

### v1.2.0
* 把项目拆分成三个 JUpload， TUpload， BUpload 三个组件，分别实现三种不同风格的文件上传 UI
* 修复BUpload的文件信息统计错误的bug
* 修复css兼容性问题


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)