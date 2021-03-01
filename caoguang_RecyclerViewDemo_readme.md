#RecyclerViewDemo

Android 利用RecyclerView仿淘宝订单页面实现 

问题：
	由于每个订单项中可能会包含多个具体的项目，要想实现这种效果，
	一般来说需要在RecyclerView中嵌套RecyclerView，
	这样做会导致，如果订单项中的具体项目过多，超过一屏，展示效果
	会有卡顿现象，原因就是由于两个RecyclerView的存在，使得滑动的
	view滑出当前屏幕的释放存在冲突
思路：
	参照http://blog.csdn.net/Ideaqjjl/article/details/51043644
	
解决方式：
	根据RecyclerView的分组设置，将每一行都作为一个Item，就相当于
	在一个RecyclerView中添加item，这样就可以很好的解决问题

博客地址
http://blog.csdn.net/feiyangbahu1/article/details/52305769

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)