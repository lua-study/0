# 前端教学项目 
# ——基于HTML5、CSS3及原生javascript的博客网站前端的设计与实现
## 项目介绍
该项目是基于HTML5、CSS3及原生javascript的教学项目，该项目将适配chrome66+或firefox61+版本的浏览器。
不兼容早期的浏览器版本和IE等浏览器。该项目将以任务细分的方式，逐个完成。

## 软件架构
HTML5、CSS3及原生javascript

## 使用说明
可以根据以下的任务列表，同时依据源代码，追溯项目一步一步完成的过程。

## 前置任务列表
### 1，学习使用VSCode IDE
### 2，下载并使用live-server

下载并安装node.js，npm是node.js的包管理器。

利用npm下载live-sever，如下：

```
npm install -g live-server
```

在VS Code中下载live-sever的插件，搜索关键字为：live-server

### 3，git与giteen
git是一个从linux中移植过来的版本控制软件。

giteen是以gitLab为核心的类github网站。

####git的安装和使用

在windows中安装git，掌握利用VS Code的图形界面或DOS命令行进行git操作。

下载已经存在的项目

git clone url	#克隆网站上的源代码

上传源代码的三个步骤

将修改后源代码加入临时区（add）

将临时区中的源代码加入本地仓库（commit）

将本地仓库中的源代上传到giteen（push）

### 4，建立基本的文档结构
```
frontEndProject
    img目录
    css目录
    js目录
    views目录
    index.html文件
```

## HTML+CSS部分项目细分任务列表
### 1，创建cssSelector.html文件
在学习中将所有的例子应用全部放入cssSelector.html文件中，使该文件包含大量的标签。以备之后建立标签选择器之用。
### 2，创建login.html文件
1，在index.html文件中建立向login.html文件的转向。

2，利用原型绘制软件，绘制登录页面的大致原型，对要完成的界面做到心中有数。

![登录页面原型设计图](/projImg/loginPage_prototype.png)

3，login.html文件的基本需求：
​    创建块级元素，并在其中建立用户名、密码文本以其对应的文本框，建立按钮（建议使用button标签）
​    使用CSS对登录块进行美化
​    建立水平、垂直居中
​    创建登录失败信息显示框

### 3，login.html文件进阶

1，利用background属性为login.html文件增角标
2，为居中的盒子增加阴影；为盒子添加圆角。
3，为盒子新增cookie选择，并且设置cookie选择为可隐藏。也需要精灵图。

login.html页面的具体完成情况如下：

![](projImg/loginPage.png)

### 4，main主页面布局任务

1，使用float、flex或grid布局技术，给blog网站的主页面（main.html）布局。

2，布局要求：

	要包含一个完整的logo界面。
	要包含一个横向菜单组件，菜单项目包括：主页、写博客、文章分类、设置。
	要包含一个竖向菜单组件，包含一二级的文章分类列表
	要包含一个用户登录/用户信息介绍组件。	
	要包含一个主面显示组件。
	还包含一些杂项，比如：点击排行榜、点赞排行榜...
	具体的布局可以自己掌握。总之，我们需要的是一张网页类的主页页面。

3，以上布局要求，以原型图和html页面的的形式提交到远程仓库。

主页面布局可以按自己的想法进行，以下给出参考布局。

![](/projImg/mainPage_prototype.png)

### 5，设计标准的表格页面

任务1，使用table相关标签和相应的CSS属性，设计通过用的标准表格。要求：

1，要包括CRUD操作按钮。

2，专门的查询界面（必要时可以升级为即席查询）。

3，要包括分页组件。

注意：table标签不能设置任何属性，所有表格的外观全部由CSS设置。

如图：

![](projImg/simpleTable.png)

任务2，利用新学的CSS伪类，为表格进行美化。主要包括：隔行变色、悬浮变色等。

### 6，支线任务

对CSS选择器列表中的每一行的选择器都进行代码验证，代码全部集中到cssSelector.html文件中备用。

### 7，main.html页面的菜单任务

完成顶部主菜单和左侧文章类型菜单。

#### 1，顶部主菜单任务

1，利用ul-li标签组合完成基本架构搭建

2，利用float属性将列表方向由竖向改为横向

3，利用选择器伪类完成菜单分隔线、鼠标悬浮效果。

4，利用background-position属性给每个菜单一个前置图片。

完成图如下：

![](projImg/topMenu.png)

#### 2，左侧文章类型菜单任务

###8，在已经完成的页面加入语义标签

加入语义标签的目的，是增强搜索引擎有好性

任务1，在login.html页面中，为form表单及表单中的文本框、密码框和复选框追加语义标签，并根据需要修改原有设计。

```html
 
     用户登录 
     
         用户名： 
          
         密&nbsp;&nbsp;&nbsp;码： 
          
          
         
             
             
                 一周之内不需要登录 
             
         
         登录 
     
 
```

### 9，register.htm页面

任务1，构建注册页面，完成基本元素的添加和设计工作。

基本注册页面如下图：

![](projImg/registerPage.png)

任务2，调整美化注册页面，使其与登录页面特色相同。

## Javascript部分项目细分任务列表

### 1，为login.html、register.html添加动作

#### 为login.html添加动作

1，图片旋转

```css
.change{
    transform: rotate(-90deg);
}
```

2，document.getElementsByClassName()函数获得当前文档中拥有某个class的所有元素，返回值是一个数组。

3，element.classList属性存储着元素中的class列表。classList.add("...");是往列表中追加一个新的class。

####为register.html添加动作

丢失焦点后，对文本框内容进行检测。以下分别是错误和正确时的CSS样式。

```css
.okMessage{
    color:green;
}
.errorMessage{
    color:red;
}
.errorImg{
    background:url(../img/small_icons.jpg) no-repeat -80px -8px/300px 300px;
}
.okImg{
    background:url(../img/small_icons.jpg) no-repeat -182px -240px/300px 300px;
}
```



### 2，升级cssSelector.html文件

####相关的基础知识讲解

1，`document.querySelector("#cssSelectorText").value;`代码含义

document.querySelector("...");代码获取一个具体的元素，之后加上`.value`，指的是获取这个元素中的值。因为当前元素是一个input元素，所以`.value`获取的是input中的文本值。

1，Array.from(类数组)函数，是ES6提供的类数组转化函数。在JS中类数组内部没有迭代子，所以不能使用forEach()函数。必须将类数组转化成真正的数组才行。使用[...类数组]也可以使得相同的效果。

2，forEach()函数是函数式编程的写法，其中的参数是lambda表达式。

```js
let nodes=[1,2,3,4];
//函数式编程+lambda表代式的写法
Array.from(nodes).forEach((item)=>{
	console.log(item);
});
//函数式编程的写法
Array.from(nodes).forEach(function(item){
    console.log(item);
});
//ES5中的写法
for(let i=0,len=nodes.length;i {
    item.classList.remove("selected");
});
Array.from(nodes).forEach((item)=>{
    item.classList.add("selected");
});
```

4，给文本框一个回车操作。该回车操作相当于点击查询按钮。

### 3，升级tableDemo.html文件

主任务1：将tableDemo.html中的表格升级为可编辑表格。该任务涉及到事件冒泡、节点创建、节点追加等操作。还会接触到不会发生事件冒泡的事件。

实现效果如下：

![](projImg/editTable.png)

双击某个Cell时，变化如下：

![](projImg/editTable1.png)

主任务2：表格左侧复选框全选功能；单击表格中任意行的任意位置，该行复选框靠选中功能。

主任务3：单击新增按钮，隐藏表格，显示用户新增界面。

### 4，基础SPA应用

1，添加hashchangeDemo.html文件，完成基于hashchange事件和location.hash的单页无刷新操作。

2，添加pushstateDemo.html文件，完成基于pushstate()函数的单页无刷新操作。

### 5，setTimeout()和setInterval()函数应用

1，升级dateTimeDemo.html文件，使用其中的时间内容可以随着时间的变化而变化。

2，提高任务：秒杀倒计时设计。

### 6，继续升级tableDemo.html文件

完成纯JS的表格增删操作。可以直接使用DOM操作，也可以是使用DOM Table操作。
1，选择具体的行（可以选择多行）后，点击删除按钮，相应的行被删除。

2，点新增按钮，显示新增组件，隐藏table组件。输入要新增的用户信息后，点击提交按钮。显示table组件，隐藏新增组件，同时将新的数据以表中新行的形式追加到tbody的尾部。

3，更高级的任务（选做）：完成修改流程。

思路：选择具体行（只能选择一行）后，点击修改按钮，显示出新增组件，其中的文本框中显示相应内容。修改后，点击提交，回到table组件，页面信息被修改。

注意：由于已经使用了可编程技术，所以修改任务是附加任务，而且本身难度较大。有余力的同学可以尝试一下。

###7，升级register.html文件

任务1，丢失焦点校验email字段，利用正则表达式。（已经完成）

任务2，注册页面中的所有文本框都要进行丢失焦点校验：

​	用户名校验：用户名是否为空；用户名必是英文、数字、下划线组成；用户名不能重复（该功能暂时不做）。

​	昵称校验：不能为空。

​	密码校验：不能为空；长度不能小于8，不能大于20个字符。

​	重复密码校验：不能为空；必须和密码相同。

​	手机号校验：按正则表达式校验。



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)