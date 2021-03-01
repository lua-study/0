# formSelects

#### 项目介绍
基于 https://github.com/hnzzmsf/layui-formSelects 的支持layui的多选下拉表单控件：新增了分页异步加载数据的功能
更多详情使用文档可参考原作者的文档。

这里只说明添加的功能。



#### 安装教程

1. 引用formSelects-v4.css与formSelects-v4.modify.css（聪明的你注意改下css里面引用的图片路径哦。）
2. 引用formSelects-v4.1.js

#### 使用说明

1. 分页加载功能：

![输入图片说明](https://images.gitee.com/uploads/images/2018/0807/142701_d96e11a7_432156.png "QQ截图20180807142634.png")

```

 
   请选择行业类别 
 
						    
 
layui.formSelects.data('industry_select',"server", {
    url: '/industryList',
    showPage: true,
    size: 6,
    paramMap: {
        page: "page",
        size: "rows",
        keyword: "room_name_like"
    },
    initValues: '#(detail.room_id)'?['#(detail.room_id)']:null,
    beforeSuccess: function(id, searchUrl, inputValue, res){
        // 转义成formSelects识别的数据结构
        let data = [];
        if(res&&res.success){
            for(var i=0;i 
```

2.级联异步加载功能

![输入图片说明](https://images.gitee.com/uploads/images/2018/0807/142733_677c24e7_432156.png "QQ截图20180807142558.png")



```
 
     请选择单位所在省市区 
 

 
layui.formSelects.data('orgArea', 'server', {
    url: '/city',
    linkage: true,
    linkageWidth: 130
});
 
```



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)