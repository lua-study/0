# vue-flow-editor

[TOC]

## 简介

vue-flow-editor 是基于 Vue2.0 以及 G6@3.1.10 实现的流程编辑器。在线操作地址：
[example](http://martsforever-pot.gitee.io/vue-flow-editor/)

## 特点

- 兼容ie；
- 轻量级依赖
    - 依赖于 Vue2.0、vue-composition-api、g6、element-ui，但是打包的 vue-flow-editor 中是不包含这些依赖的，
    由开发者手动引入，方便管理依赖；
    - 对G6的连接线进行了简单封装，对节点无影响。开发者可以使用G6的默认节点以实现自定义的样式；
    - 操作丰富，请见操作手册；
- 界面简洁，左侧菜单栏以及顶部工具栏都有插槽供开发者自定义内容；
- 内置一个右侧弹出框，开发者可以通过插槽，以及手动打开这个弹出框以编辑节点内容；

## 安装

### 静态引入

- [vue-flow-editor.js](http://martsforever-pot.gitee.io/vue-flow-editor/dist/vue-flow-editor.js)
- [vue-flow-editor.css](http://martsforever-pot.gitee.io/vue-flow-editor/dist/vue-flow-editor.css)

```html
 
 
     
     vue-flow-editor demo 
     
     

     
        html, body {
            padding: 0;
            margin: 0;
        }
     
 
 
 

 
  
  
  
  
  
 

    console.log(window)
    Vue.use(vueCompositionApi.default)
    Vue.use(window.VueFlowEditor)

    const reactive = vueCompositionApi.reactive

    const AppData = {
        nodes: [
            {"data": {"isStart": true}, "id": "n123", "label": "开始", "shape": "rect", "size": [120, 40], "x": 260, "y": 60},
            {"data": {"isEnd": true}, "id": "n234", "label": "结束", "shape": "rect", "size": [120, 40], "x": 260, "y": 380},
            {"data": {"selectValue": "1"}, "id": "n345", "label": "填写表单", "shape": "rect", "size": [120, 40], "x": 260, "y": 140},
            {"data": {"selectValue": "2"}, "id": "n456", "label": "部门负责人审批", "shape": "rect", "size": [120, 40], "x": 260, "y": 220},
            {"data": {"selectValue": "3"}, "id": "n678", "label": "总经理审批", "shape": "rect", "size": [120, 40], "x": 260, "y": 300}
        ],
        edges: [
            {source: "n123", target: "n345"},
            {source: "n345", target: "n456"},
            {source: "n456", target: "n678"},
            {source: "n678", target: "n234"}
        ]
    }

    new Vue({
        el: '#app',
        template: `
         
             
                 
                     
                         
                         
                         
                     
                     
                         
                         
                         
                         
                         
                         
                     
                 
                 
                     
                         
                             
                         

                         
                             
                                 
                                     
                                 
                             
                         
                     
                 
                 
                     保存 
                     取消 
                 
             
         
        `,
        setup() {
            const state = reactive({
                data: AppData,
                detailModel: null,

                selectOptions: [
                    {label: '待确认', value: '0'},
                    {label: '填写表单', value: '1'},
                    {label: '部门负责人审批', value: '2'},
                    {label: '总经理审批', value: '3'},
                ]
            })

            let editor;

            function onDblclickNode(e) {
                state.detailModel = {...e.item.get('model')}
                editor.openModel()
            }

            function cancel() {
                editor.closeModel()
            }

            function save() {
                const model = state.detailModel

                if (!model.data.isStart && !model.data.isEnd) {

                    if (model.data.selectValue == null) {
                        model.data.selectValue = '0'
                    }
                    let selectLabel;
                    state.selectOptions.forEach((item) => {
                        if (item.value == model.data.selectValue) {
                            selectLabel = item.label
                        }
                    })

                    if (!!selectLabel) {
                        model.label = selectLabel
                    }

                    state.detailModel = model
                }

                editor.updateModel(state.detailModel)
                editor.closeModel()
            }

            return {
                state,

                showGrid: true,
                showMiniMap: false,

                log: () => {
                    console.log({...state.data})
                },
                onDblclickNode,
                cancel,
                save,

                onRef: e => editor = e,
            }
        },
    }).$mount()


 
 
 
```

如果你希望在ie浏览器下查看这个demo的效果，请看地址：[demo.html](http://martsforever-pot.gitee.io/vue-flow-editor/demo.html)

### npm安装

```bash
npm i vue-flow-editor -D
```

```js
import Vue from 'vue'
import vca from '@vue/composition-api'
import VueFlowEditor from 'vue-flow-editor'
import 'vue-flow-editor/docs/dist/vue-flow-editor.css'

Vue.use(vca)
Vue.use(VueFlowEditor)
```

## vue-flow-editor 属性说明

|属性名称|类型|默认值|可选值|说明|
| --- | --- | --- | --- | --- |
| height| number,string | 100%| --- | 画布高度 |
| toolbarHeight | string,number | 50px | --- | 工具栏高度 |
| menuWidth | string,number | 250px | --- | 菜单栏宽度 |
| modelWidth | string,number | 500px | --- | 右侧弹框宽度 |
| data | object | --- | --- | 渲染的数据，数据格式参考G6文档 |
| grid | boolean | true | --- | 是否开启网格 |
| miniMap | boolean | false | --- | 是否开启缩略图 |
| onRef | Function | --- | --- | 获取组件的引用时，传递的函数，参数为组件暴露的函数以及响应式变量 |

## 通过 onRef 得到的对象

|属性名称|类型|说明|
| --- | --- | --- |
| editorState | object | 编辑器组件内部状态变量 |
| commander | object | 命令对象，画布中所有操作都是通过commander进行的，以便实现撤销以及重做 |
| openModel | function | 打开右侧弹框 |
| closeModel | function | 关闭右侧弹框 |
| updateModel | function | 更新model |
| openPreview | function | 打开预览对话框 |


## 操作手册

### 工具栏

从左至右依次为：
- 开启/关闭网格；
- 开启/关闭缩略图；
- 适应画布（画布缩放适应界面大小）；
- 实际尺寸（画布中元素大小为实际像素大小）；
- 撤销；
- 重做；
- 放大；
- 缩小；
- 删除（选中节点之后删除）；
- 预览（在弹框中以适应画布的模式展示画布内容）；

### 选择

- 单击 节点/边 可以选中，选中的时候样式会有变化；
- 摁住 shift单击 可以选中多个 节点/边；
- 摁住 shift可以拖拽生成一个选择框，框内的 节点/边 会被选中；
- 鼠标在画布内快捷键 CTRL+A 可以全选；
- 多选的时候拖拽节点，会拖拽所有的节点；

### 新建节点/边

- 从左侧选项菜单列表中拖拽菜单到画布可以添加节点；
- 悬浮在节点内，会显示用来连接线的指示节点，点击拖拽连接其他节点的指示节点可以新建连线（这个不是特别灵敏，拖拽指示节点的时候稍微慢一点）；
- 右侧选项菜单中有各种形状的节点供拖拽展示；

### 编辑

- 双击节点会弹出编辑器右侧的编辑框（这个动作是开发者自定义的，可以自定义弹框编辑节点内容）；
- 编辑器右侧的编辑框内的内容是自定义的，可以根据节点内容动态变化，显示不同的表单内容；比如实例中，【开始】以及【结束】节点就只能编辑节点名称；而【审批节点】可以从下拉选项中选择【节点任务内容】；

# 后续待完成的功能

- 节点增加宽度以及高度的功能；
- 节点复制；

# 其他

- vue-flow-editor是基于 Vue2.0 + vue-composition-api（Vue3.0的内容） + typescript 实现的库，如果要在项目生产环境中使用 vue-flow-editor，请确保 vue-composition-api 不会对项目造成影响；
- 拖拽节点以及拖拽边的时候并不是特别灵敏，所以拖拽节点以及拖拽边的时候，操作稍微慢一点；    

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)