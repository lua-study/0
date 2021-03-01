# WeChatEditor

![输入图片说明](https://images.gitee.com/uploads/images/2020/0229/123431_9c8fc920_773060.png "TIM图片20200229115251.png")


#### 介绍
最近要用小程序实现新闻的发布,需要用到富文本编辑器,到官方看了下,文档写的太差劲...最主要的是demo居然跑不通,我也是醉了....论坛上一片骂声,很多人都用不了这个东西....很是坑人...

没办法只能自己埋头研究,现在弄出来了...本着开源的精神把这个组件开源,只需导入项目,修改几个字段即可正常使用




###注意
导入时不能使用测试appid 一定要用正式的appid,因为这个编辑器我用了云存储,如果使用测试appid,则会导致上传图片失败


#### 软件架构
基础库版本2.9.5


#### 安装教程

1.  下载源代码,导入到工具里面
2.  不要选择测试appid

#### 使用说明

1.  提交后调用 formSubmit()函数
2.  上传图片调用 insertImage()函数,注意这里有个云上传的动作如果不要云上传请执行修改
3.  其他的无需修改

#### 其他事项

施正2020.02.29


#### 码云特技

1.  使用 Readme\_XXX.md 来支持不同的语言，例如 Readme\_en.md, Readme\_zh.md
2.  码云官方博客 [blog.gitee.com](https://blog.gitee.com)
3.  你可以 [https://gitee.com/explore](https://gitee.com/explore) 这个地址来了解码云上的优秀开源项目
4.  [GVP](https://gitee.com/gvp) 全称是码云最有价值开源项目，是码云综合评定出的优秀开源项目
5.  码云官方提供的使用手册 [https://gitee.com/help](https://gitee.com/help)
6.  码云封面人物是一档用来展示码云会员风采的栏目 [https://gitee.com/gitee-stars/](https://gitee.com/gitee-stars/)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)