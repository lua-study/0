WeUI 为微信 Web 服务量身设计  ![](https://travis-ci.org/weui/weui.svg?branch=master)
====

## 概述

WeUI是一套同微信原生视觉体验一致的基础样式库，为微信 Web 开发量身设计，可以令用户的使用感知更加统一。包含`button`、`cell`、`dialog`、`toast`、`article`、`icon`等各式元素。

## 使用

#### 方法一：
使用`bower`进行安装
```
bower install --save weui
```

#### 方法二：
使用`npm`进行安装
```
npm install --save weui
```

## 开发

```
git clone https://github.com/weui/weui.git
cd weui
npm install -g gulp
npm install
gulp -ws
```
运行`gulp -ws`命令，会监听`src`目录下所有文件的变更，并且默认会在`8080`端口启动服务器，然后在浏览器打开 `http://localhost:8080/example`。


## 手机预览

请用微信扫码

![](./dist/example/snapshot/qrcode.png)

[http://weui.github.io/weui/](http://weui.github.io/weui)

## Button

按钮可以使用`a`或者`button`标签。wap上要触发按钮的active态，必须触发ontouchstart事件，可以在`body`上加上`ontouchstart=""`全局触发。

按钮常见的操作场景：确定、取消、警示，分别对应class：`weui_btn_primary`、`weui_btn_default`、`weui_btn_warn`，每种场景都有自己的置灰态`weui_btn_disabled`，除此外还有一种镂空按钮`weui_btn_plain_xxx`，客户端webview里的按钮尺寸有两类，默认宽度100%，小型按钮宽度自适应，两边边框与文本间距0.75em：

![](./dist/example/snapshot/button.png)

```html
 按钮 
 按钮 
 确认 
 确认 
 按钮 
 按钮 
 
     按钮 
     按钮 

     按钮 
     按钮 
 
```


## Cell

`Cell`，列表视图，用于将信息以列表的结构显示在页面上，是wap上最常用的内容结构。`Cell`由多个section组成，每个section包括section header`weui_cells_title`以及cells`weui_cells`。

`cell`由thumnail`weui_cell_hd`、body`weui_cell_bd`、accessory`weui_cell_ft`三部分组成，`cell`采用自适应布局，在需要自适应的部分加上class`weui_cell_primary`即可：

![](./dist/example/snapshot/cell.png)

带说明的列表项

```html
 带说明的列表项 
 
     
         
             标题文字 
         
         
            说明文字
         
     
 
```

`Cell`可根据需要进行各种自定义扩展，包括辅助说明、跳转、单选、复选等。下面以带图标、说明、跳转的列表项，其他情况可以直接参考`example`下的代码：

```html
 带图标、说明、跳转的列表项 
 

     
         
             
         
         
             cell standard 
         
         
            说明文字
         
     
     
         
             
         
         
             cell standard 
         
         
            说明文字
         
     
 
```


## Dialog

若系统的alert窗体无法满足网页的临时视图内容需求，则可以自定义实现与alert形式相似的dialog，并且在dialog中可以自定义地使用各种控件，来满足需求。

![](./dist/example/snapshot/dialog1.png)

```html
 
      
     
          弹窗标题  
         自定义弹窗内容 ... 
         
             取消 
             确定 
         
     
 
```

![](./dist/example/snapshot/dialog2.png)
```html
 
      
     
          弹窗标题  
         弹窗内容，告知当前页面信息等 
         
             确定 
         
     
 
```


## Toast

toast用于临时显示某些信息，并且会在数秒后自动消失。这些信息通常是轻量级操作的成功、失败或等待状态信息。

![](./dist/example/snapshot/toast1.png)

```html
 
      
     
          
         已完成 
     
 
```

![](./dist/example/snapshot/toast2.png)

```html
 
      
     
         
             
              
              
              
              
              
              
              
              
              
              
              
              
         
         数据加载中 
     
 
```

## Msg Page

结果页通常来说可以认为进行一系列操作步骤后，作为流程结束的总结性页面。结果页的作用主要是告知用户操作处理结果以及必要的相关细节（可用于确认之前的操作是否有误）等信息；若该流程用于开启或关闭某些重要功能，可在结果页增加与该功能相关的描述性内容；除此之外，结果页也可以承载一些附加价值操作，例如提供抽奖、关注公众号等功能入口。

![](./dist/example/snapshot/result.png)

```html
 
        
     
         操作成功 
         内容详情，可根据实际需要安排 
     
     
         
             确定 
             取消 
         
     
     
         查看详情 
     
 
```

## Article

文字视图显示大段文字，这些文字通常是页面上的主体内容。`Article`支持分段、多层标题、引用、内嵌图片、有/无序列表等富文本样式，并可响应用户的选择操作。

在微信客户端webview中使用`Article`，必须保证文字有足够的可读性和可辨识性、使用规范字体、保证足够的段间距、段首无缩进。

![](./dist/example/snapshot/text.png)

```html
 
     大标题 
     
         章标题 
         
             1.1 节标题 
             Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
                tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam,
                quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo
                consequat. Duis aute 
         
         
             1.2 节标题 
             Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
                tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam,
                cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non
                proident, sunt in culpa qui officia deserunt mollit anim id est laborum. 
         
     
 
```

## Icon

![](./dist/example/snapshot/icons.png)
```html
  
  
  
  
  
  
 
      
      
      
      
      
      
      
      
      
 
```

## TODO

- 更多的组件
- react-weui

## License
The MIT License(http://opensource.org/licenses/MIT)
请自由地享受和参与开源

## 贡献

如果你有好的意见或建议，欢迎给我们提issue或pull request，为提升微信web体验贡献力量


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)