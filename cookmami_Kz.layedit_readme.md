# Kz.layedit

### 已更新项目配置使用说明 [Kz.layedit使用说明](https://knifez.gitee.io/articles/kz.layedit/)

#### 在线预览 [码云Gitee Pages](http://knifez.gitee.io/kz.layedit/index.html)

### 存在缺陷--由于本人是职业后端，前端水平有限，故存在一些bug短期内无法修复
- ##### word粘贴的图片只能获取本机temp路径，且无法判别是否是图片，无法以file形式上传后台，故后续不继续考虑和实现word图片粘贴问题 ，参照ueditor后发现也没有实现该功能，仅仅是过滤了标签多余样式
- ##### 修改字体/字体大小 会清除选中文本段落格式，短期内可能无法修复
- ##### 插入视频 默认以div包裹，前后插入一个```&nbsp;```来实现选中居中和删除操作。
- ##### 关于getRangeAt(0)报错，由于我个人使用时无论弹窗还是直接使用或在form表单中均未能复现，请遇到该问题的人附上详细错误和调用环境、操作过程等可能导致该问题或有助于解决该问题的信息
- ##### 撤销重做仅仅是简单实现，无法满足正常需求，不推荐使用，后续优化概率较小，除非我找到能很好解决这个问题的办法
- ##### 虽然对移动端做了适配,但是使用体验不咋的,已经放弃治疗.以后估计只会优化界面,避免出现宽,高溢出的情况。不建议移动端做富文本编辑.

##### 下一步的精力主要用于解决插入图片没有闭合标签问题=.= 以及寻求解决方案解决修改字体和字体大小的bug。

#### 其他问题可先查看issues有没有类似问题，如果没有可直接提issues，也方便其他人查看，不再翻评论 :smile: 

#### 更新日志
##### v19.03.22
1. [修复] 多图上传设置宽高报错问题
##### V19.03.20
1. [修复] 当p标签内存在多张图片时back键调用callDel删除时始终获取的是第一张图片src的bug
2. [新增] del键删除图片调用callDel回调方法
##### V19.03.18
1. [修复] 粘贴图片时错误的粘贴到编辑器顶部而不是鼠标光标处
##### V19.03.02
1. [修复] 全屏下查看源代码内容过长时最后几行看不到问题
2. [优化] 全屏模式下背景色改为白色
##### V19.01.26
1. [修复] 监听事件container.tagName为undefined错误  感谢 yianyao 的反馈
##### V19.01.25
1. [优化] ctrl+b 加粗使用strong标签替换原版b标签
2. [修复] 段落格式 和 字体大小 可能出现点击后即自动关闭的问题
##### V19.01.24
1. [优化] 支持从word粘贴内容保留格式，去除多余标签
##### V19.01.23
1. [移除] V19.01.22-beta-[3] 报 无法获取图片路径 的提示，，不过原先会提示的图片依旧无法从服务器删除
2. [修复]  编辑器内容为空时回车换行添加的标签为div，昨天更新时不小心覆盖掉了、已修复为追加p标签
3. [修复] 图片上传宽高兼容%后设置无效问题 --感谢不愿意透露姓名的网友反馈 :smile: 
##### V19.01.22-beta
1. [优化] 图片上传宽高兼容%设置
2. [修复] 编辑器内容为空时回车换行添加的标签为div
3. [测试] back退格键删除图片时调用callDel配置参数回调服务器删除附件,需配置参数 backDelImg:true （待删除），目前不支持没有p标签或其他元素包裹的img图片删除，会报无法获取图片路径的弹出层，这是正常提示、、
##### V19.01.19 （感谢 biancangming 的反馈）
1. [修复] 粘贴图片不调用uploadImage.done方法
2. [新增] 插入代码配置codeConfig新增参数 class,可根据需要自定义样式，不填默认为layui-code
##### V19.01.18
1. [修复]  IR5LC 火狐浏览器菜单宽度异常问题 
2. [新增] preview预览样式设置参数 previewAttr,支出对预览弹出层的area,offset参数设置，修改默认值为area:['50%','100%'],offset:'r'。 
3. [修复] 空编辑器插入视频出现getRangeAt错误和同步textarea异常问题
##### V19.01.16-beta
1. [优化] 插入图片时如果不填写描述属性和宽高时，不再添加style="" alt="" 空属性
2. [修复] 附件上传没有添加data和headers参数，由于我个人不使用这两个参数且测试时都时拿上传图片测试、、、所以未能测试出该问题，对因此造成困扰的人感到抱歉=.=
##### V19.01.10-beta
1. [修复] 取消回车/插入元素自动加p标签包裹，防止特殊情况下的段落异常，ul->li标签内文字需p标签或span等包裹，否则回车会新建ul标签导致段落错乱
##### V19.01.05
1. [新增] 附件上传自动插入编辑器设置 autoInsert, 添加设置参数 uploadFiles{autoInsert:true} 即可选中文件上传完之后自动插入编辑器，无需点确认按钮

####   历史日志--V18.* 

#### 项目介绍
对layui.layedit的拓展，基于layui v2.4.3.
- 增加了HTML源码模式，
- 图片插入功能添加alt属性（layupload），
- 视频插入功能，
- 全屏功能，
- 段落格式，
- 字体颜色设置功能。
- 所有拓展功能菜单按钮图标均引用自layui自带图标
#### 软件架构
软件架构说明
1. HTML源码模式 引用第三方插件ace,优化源码展示样式。
2. 引用ace编辑器仅保留了html源码样式和tomorrow主题，如有需要可自行更换
#### 安装教程
1. index.html下为示例文件，可供查看演示功能
2. 将dist下文件layedit.js替换掉layui/lay/modules/layedit.js
3. 正常调用layedit即可

#### 使用说明
配置信息(具体查看示例文件)

```
     layui.use(['layedit','layer','jquery'],function() {
         var $=layui.jquery;
         var layedit = layui.layedit;
 		 layedit.set({
                //暴露layupload参数设置接口 --详细查看layupload参数说明
                uploadImage: {
                    url: 'your url',
                    field: 'file',//上传时的文件参数字段名
                    accept: 'image',
                    acceptMime: 'image/*',
                    exts: 'jpg|png|gif|bmp|jpeg',
                    size: 1024 * 10,
                    done: function (data) {//文件上传接口返回code为0时的回调
                    }
                }
                , uploadVideo: {
                    url: 'your url',
                    field: 'file',//上传时的文件参数字段名
                    accept: 'video',
                    acceptMime: 'video/*',
                    exts: 'mp4|flv|avi|rm|rmvb',
                    size: 1024 * 2 * 10,
                    done: function (data) {//文件上传接口返回code为0时的回调
                    }
                }
                //右键删除图片/视频时的回调参数，post到后台删除服务器文件等操作，
                //传递参数：
                //图片： imgpath --图片路径
                //视频： filepath --视频路径 imgpath --封面路径
                , calldel: {
                    url: 'your url',
                    done: function (data) {//data删除文件接口返回返回的数据
                    }
                }
                //开发者模式 --默认为false
                , devmode: true
                //插入代码设置
                , codeConfig: {
                    hide: false,  //是否显示编码语言选择框
                    default: 'javascript' //hide为true时的默认语言格式
                }           
                //新增iframe外置样式和js
                , quote:{
                    style: ['/Content/Layui-KnifeZ/css/layui.css','/others'],
                    js: ['/Content/Layui-KnifeZ/lay/modules/jquery.js']
                }
                 , //fontFomatt:["p","span"]  //自定义段落格式 ，如不填，默认为 ["p", "h1", "h2", "h3", "h4", "h5", "h6", "div"]~~
                 , tool: [
                     'html','undo','redo','code'
 					, 'strong', 'italic', 'underline', 'del', 
					,'addhr' //添加水平线
					,'|', 'fontFomatt','colorpicker' //段落格式，字体颜色
 					, 'face', '|', 'left', 'center', 'right', '|', 'link', 'unlink'
 					, 'image_alt', 'altEdit', 'video' 
					,'anchors' //锚点
                     , '|'
					 , 'table'//插入表格
					 ,'customlink'//插入自定义链接
					 ,'fullScreen'
                 ]
         });
         var ieditor = layedit.build('layeditDemo');
		 layedit.setContent(ieditor,"hello layedit",false);
     })
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)