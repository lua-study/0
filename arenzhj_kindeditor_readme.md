# NKeditor
NKedtior是基于 kindeditor 进行二次开发的项目
kindeditor 是一款优秀的开源在线编辑器。轻量级且功能强大，代码量却不到百度的ueditor编辑器的一半。可惜已经4年没有更新了，由于业务的需求我们在kindeditor的基础上开发了 NKeditor, 主要做了一下工作：
1. 调整编辑器和弹出 dialog 的样式，美化了UI
2. 重写图片上传和批量图片上传插件，使用 html5 上传代替了 flash,实现了待上传图片预览，优化用户体验
3. 修复一些已知的bug，如 ajax 提交无法获取内容等
4. 新增涂鸦等功能

再次感谢 kindeditor 的开发者，为我们提供了如此优秀的在线编辑器，让我们能在前人的基础上继续贡献自己的微薄之力。

# 关于版本号
NKeditor 沿用了 kindeditor 最后发布的版本号 v4.1.11，所以NKeditor 发布的第一个稳定版本是 v4.2.0, 以后的版本都是在 v4.2.0 版本的基础上发布的。

# 在线演示

### http://d.r9it.com/nkeditor/

# 使用说明
1. 批量图片上传的插件依赖 jQuery-1.7 以上的版本，jquery需要自己手动引入，编辑器没有默认引入的，这样避免加载了你不需要的脚本库导致页面加载变慢
2. 文件上传实现了 php 传统方式和七牛云图片上传，默认推荐使用七牛云，使用很简单，而且免费（企业版收费）。demo 上使用的是我的个人空间，多人测试的时候上传速度和并发都有很大的限制，如果大家测试的时候觉得慢，可以改成自己的七牛空间或者使用本地上传。
5. 七牛云的 SDK 依赖 composer 构建，所以如果使用七牛云上传的话请在 php/qiniu 目录下执行 __composer install__
4. 还有就是 demo 中我的七牛存储空间仅供大家测试使用，请不要上传有违法律法规和道德规范的图片和文件资源，你懂的 O(∩_∩)O~。
3. 后端上传和文件管理代码我只是写了简单的 demo, 没有做安全处理之类，请谨慎使用，仅做参考。



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)