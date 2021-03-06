﻿## 滑块式验证码

用户通过拖动滑块行为来完成校验，支持PC端及移动端。可以将用户拖动行为的时间、精度，滑动轨迹等信息到服务器，然后进行后台算法验证。

## 在线演示
单页面演示：http://longbowenterprise.gitee.io/slidercaptcha/  
项目内演示：http://argo.zylweb.cn/ (本项目为开源后台管理框架 [[BootstrapAdmin](https://gitee.com/LongbowEnterprise/BootstrapAdmin)])  
**输入三次错误密码后第四次出现滑块式行为验证码**  

## 效果图
![输入图片说明](https://images.gitee.com/uploads/images/2019/0316/003740_c5175e6b_554725.png "SliderCaptcha.png")
![输入图片说明](https://gitee.com/uploads/images/2019/0410/124955_f9b6d54c_554725.png "Untitled.png")

## 快速开始

### 组件依赖 jQuery bootstrap font-awesome

### CSS

```html
 
 
 
```
将引入样式表的 &lt;link&gt; 标签复制并粘贴到 &lt;head&gt; 中，并放在所有其他样式表之前。

### JS

```html
  
  
```

将引入脚本的 &lt;script&gt; 标签复制并粘贴到 &lt;body&gt; 最后面。

## 用法

添加网页Html元素

```html
  
```

## API

### 通过 javascript 初始化控件

```html
  
 
    $('#captcha').sliderCaptcha();
    
```

### Options

可以根据自己需要设置宽度与高度等配置

```html
  
 
    $('#captcha').sliderCaptcha({
        width: 280,
        height: 150,
        sliderL: 42,
        sliderR: 9,
        loadingText: '正在加载中...',
        failedText: '再试一次',
        barText: '向右滑动填充拼图',
        repeatIcon: 'fa fa-redo'
        setSrc: function () {
            
        },
        onSuccess: function () {
            
        },
        onFail: function () {

        },
        onRefresh: function () {
        
        }
    });
    
```

名称 | 类型 | 默认值 | 说明 |
---|---|---|---
width | integer | 280 | 背景图片宽度
height | integer | 150 | 背景图标高度
sliderL | integer | 42 | 拼图宽度
sliderR | integer | 9 | 拼图突出半径
loadingText | string | "正在加载中..." | 图片加载时显示的文本信息
failedText | string | "再试一次" | 验证失败时显示的文本信息
barText | integer | "向右滑动填充拼图" | 拖动滑块准备拖动时显示的文本信息
repeatIcon | string | "fa fa-redo" | 重新加载图标 需引用 font-awesome
setSrc | function | "https://picsum.photos/?image=random" | 设置图片加载路径
onSuccess | function | *null* | 验证通过时回调此函数
onFail | function | *null* | 验证失败时回调此函数
onRefresh | function | *null* | 点击重新加载图标时回调此函数

### 方法

```html
  
 
    $('#captcha').sliderCaptcha();
    $('#captcha').sliderCaptcha('reset');
    
```

Method | Example | Description
---|---|---
init | $('#captcha').sliderCaptcha('init') | 重新初始化控件
reset | $('#captcha').sliderCaptcha('reset') | 重置控件
verify | $('#captcha').sliderCaptcha('verify') | 验证结果

## 事件
无

## Issue
请前往 [Issue](../../issues) 页面添加问题

## 参与贡献

1. Fork 本项目
2. 新建 Feat_xxx 分支
3. 提交代码
4. 新建 Pull Request

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)