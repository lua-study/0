# flowable-diagram
使用snap.svg生成flowable工作流流程图

# 使用
引入脚本文件
```
  
  
```

# 定义流程图并渲染

流程图包含节点(开始节点, 任务节点, 判断节点和结束节点), 线条(直线和折线)和表格布局
```
  
 

    var data = {

        "cellPadding" : 15,
        "tableMargin" : 10,

        "nodes": [
            {
                "type": "start",
                "cell" : "0,0"
            },
            {
                "type" : "task",
                "cell" : "1,0",
                "id" : "manager",
                "name" : "直属上司审批"
            },
            {
                "type" : "decision",
                "id" : "decision",
                "name" : "请假天数是否大于3",
                "cell" : "2,0",
                "w" : 180
            },
            {
                "type" : "task",
                "cell" : "3,1",
                "id" : "director",
                "name" : "总监审批",
                "highlight" : true
            },
            {
                "type": "end",
                "cell" : "4,0"
            }
        ],
        "lines": [
            {
                "from": "start",
                "to": "manager"
            },
            {
                "from": "manager",
                "to": "decision"
            },
            {
                "from": "decision",
                "to": "director",
                "direction" : "x",
                "text" : "是"
            },
            {
                "from": "decision",
                "to": "end",
                "text" : "否"
            },
            {
                "from": "director",
                "to": "end",
                "direction" : "y"
            }
        ]
    };

    var flow = new Flow("svg", data);
    flow.renderByTableLayout();

 
```

# 示例
![multisources](img/demo.jpg)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)