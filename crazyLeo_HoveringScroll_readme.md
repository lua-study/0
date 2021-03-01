##[滑动到顶部悬浮功能条](https://git.oschina.net/steve/HoveringScroll.git "滑动到顶部悬浮功能条")

**上滑停靠顶端悬浮框,下滑恢复原有位置**

滑动时，监听`ScrollView`的滚动Y值和悬浮区域以上的高度进行比较计算，对两个控件(布局)的显示隐藏来实现控件的顶部悬浮，通过`addView`和`removeView`来实现。



###具体实现步骤：

**1.让`ScrollView`实现滚动监听**
	
具体参见`HoveringScrollview`


**2.布局实现**

	 
	 

	 
     

         

             

                 
             

			 
             

                 

                     

                     
                 
             

             
         
     

     
     

	 


**3.监听变化，实现悬停效果**

通过search01和search02的`addView`和`removeView`来实现


###效果展示
![上滑停靠顶端悬浮框效果展示](http://git.oschina.net/uploads/images/2015/0703/172855_d2daf32f_9145.gif "上滑停靠顶端悬浮框效果展示")






 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)