# someTest
## 本项目测试范围
这个是我搭建第一个测试的项目，修改成了maven，本来修改springmvc的，但是有个问题没解决，放下了。springmvc的web方面的测试
就放到dinner和springmvc这两个测试项目去。
本项目主要测试java的基础。    

dinner:https://github.com/chenxing12/dinner
springmvc:https://github.com/chenxing12/springmvc

## My learning  git
在工作中遇到一些问题，然后进行的一些测试    
 1. 从远程库clone到本地，本地会新建一个git库，主分支为master.
 2. 主分支是master,要稳定，安全。所以平时都去dev开发？  
>创建了dev之后，开发，提交。但是master忘记合并了。   
>然后，用户1:checkout master, merge dev, and then  push. thus, master is 2.0    
>用户2： first pull dev，then push dev, then  checkout master,pull,push, thus,master is 3.0   
>实验了几次，当冲突的时候不知所措，稀里糊涂的弄好。最后，反正主代码没问题。大概也搞清楚了用法。    
>注意几点：  
> *  先pull,保证你的版本不会落后    
> *  pull之后有冲突修改好      
> *  add  -> commit ->push     
    
 3. 刚开接触遇到的最大问题：master比dev先进    
> 是说，经常不知不觉在master分支下修改东西。然后提交，反而dev进度落后了。这个问题肯定要改，但是问题怎么办？     
> 好吧，解决。checkout dev -> pull -> merge master -> resolve conflict -> push   
> 这次问题解决后养成如下习惯：在dev下开发，dev提交后，转master，先pull，再解决冲突，再merge dev,解决冲突，再push 

 4.关于merge合并的问题
 > 后来使用idea开发，尽管添加了gitignore,但每次提交还是会提交workspace.xml,然后就是从master merge dev的时候会起冲突，这时候我会选择accepte 最先进的一个。后来干脆删除了dev。
 
                     
 -------------------------------------
## git中的read.md文件编辑语言：Markdown    
###  **标题：** 
用\#表示,数量表示标题的档次，类似h1,h2,h3 
###  **换行：**
用br标签，或者至少两个空格后回车   
###  **代码：**
制表符或至少四个空格缩进的行（前提是前面空一行）或用esc下的反引号括起来：    
>
>            this is code 表示单行或多行被深色括起来，只要在行前缩进4个空格以上即可拥有
> or  `this code` ,语法高亮要用三个反引号+语言  代码  三个反引号： 
>  \`\`\`java    
> public static void main   
> \`\`\`
> ```java   
> public static void main
> ```    

###  **强调：** 
>\*强调\* 或者 \_强调\_ (示例：_斜体_)    
>\*\*加重强调\*\* 或者 \_\_加重强调\_\_ (示例：__粗体__)    
>\*\*\*特别强调\*\*\* 或者 \_\_\_特别强调\_\_\_ (示例：___粗斜体___)     

###  **列表：**      
>#### 用"*"+空格----圆点      
> * 昵称：果冻虾仁    
> * 别名：隔壁老王    
> * 英文名：Jelly    

> #### 用"1."+空格---数字列表,就是在数字后面加一个点，再加一个空格。
> 面向对象的三个基本特征：    
> 1. 封装    
> 2. 继承    
> 3. 多态    

> #### 数字列表自动排序
>在第一行指定`1. `，而接下来的几行用星号`*`（或者继续用数字1. ）就可以了，它会自动显示成2、3、4……。        
>面向对象的七大原则：   
>  1. 开闭原则   
>  1. 里氏转换原则   
>  * 依赖倒转原则   
>  * 接口隔离原则   
>  * 组合/聚合复用原则   
>  * “迪米特”法则   
>  * 单一直则原则    






 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)