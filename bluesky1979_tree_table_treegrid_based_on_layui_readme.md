插件js地址：tree_table_treegrid_based_on_layui/testTreeGrid/web/design/extend/treeGrid.js

例子地址：

        1、树状表格：tree_table_treegrid_based_on_layui /  testTreeGrid  /  web/ index.html

        2、普通表格：tree_table_treegrid_based_on_layui /  testTreeGrid  /  web/ index_list.html

在线demo： **在线[demo](http://demo.beijiyi.com/)【此服务器配置不是一般低，请耐心等待片刻，谢谢！】** 

**
###  版本更新说明：
** 

20180919

        1、定义srot排序方式，不再支持前端排序，排序只能是服务器端，点击可排序列，会触发查询语句重新请求后，并将排序字段发到后端
        格式：sort:[{"field":"id","sort":"desc"},{"field":"pId","sort":"desc"}]
        
        2、开启分页使用isPage:true，开启分页后，必须在后端自行排序每页的记录

20180913

        1、增加table级别的heightRemove参数，用法在例子上面有，可自行查看
            ,heightRemove:[".calss","#id",10]//不计算的高度,表格设定的是固定高度，此项不生效

201800912

        1、当前版本定为v0.1
        2、只依赖treeGrid.js（去掉dltable.js和treeGrid.css依赖）

20180830

        1、规范内部表格级参数与列级参数（全部列级别的参数需以lay_开头，请务必注意）

----------------------------------------------------------------------------------


**
### 基于layui的树表格-treeGrid  
** 

 **效果图：** 
![输入图片说明](https://images.gitee.com/uploads/images/2018/0828/202603_1fa14869_1613602.png "屏幕截图.png")

折叠记忆

![折叠记忆](https://images.gitee.com/uploads/images/2018/0829/235912_ac99c8dd_1613602.gif "折叠记忆：.gif")

新增节点- 

![新增节点](https://images.gitee.com/uploads/images/2018/0829/235943_e2a0991e_1613602.gif "新增节点：.gif")

删除节点

![删除节点](https://images.gitee.com/uploads/images/2018/0829/235954_65ee1063_1613602.gif "删除节点：.gif")

删除多个节点

![删除多个节点](https://images.gitee.com/uploads/images/2018/0830/000003_0697a33b_1613602.gif "删除多个节点：.gif")

节点初始化隐藏、显示控制1

    1设置
        {"id":"111", "pId":"1", "name":"苹果","lay_is_open":false}        

节点初始化隐藏、显示控制2

![节点初始化隐藏、显示控制2](https://images.gitee.com/uploads/images/2018/0830/000022_438dc749_1613602.jpeg "节点初始化隐藏、显示控制2.jpg")

多选操作（选中父节点，子节点被选中；全部子节点被选中，父节点也被选中；自己看效果）

![多选操作](https://images.gitee.com/uploads/images/2018/0830/000031_fa1c48c1_1613602.gif "多选操作（选中父节点，子节点被选中；全部子节点被选中，父节点也被选中；自己看效果）.gif")


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)