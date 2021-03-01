#SemanticAnalysis  

使用mmseg4j进行分词，情感词库丰富中，期待广大用户测试  

#使用方式：
1.自行编译src 或者直接下载[dist](http://git.oschina.net/www.feit.com/SemanticAnalysis/tree/master/dist?dir=1&filepath=dist&oid=d4ab10805e8e2fc6d4cb40b9ad48de1bf409eab0&sha=3befd9656f625a2bf6778ce2fe52ebd382f0c191)中的zg-sa.jar  
2.需要引用的第三方的包位于[lib](http://git.oschina.net/www.feit.com/SemanticAnalysis/tree/master/lib?dir=1&filepath=lib&oid=5ca9dfcacd10783bf22ccc9a71f4836a218d77bf&sha=3befd9656f625a2bf6778ce2fe52ebd382f0c191)文件夹中  

DEMO:  
```
Analysis analysis = new Analysis();
System.out.println("1: " + analysis.parse("这是一个普通评论").getCode());
System.out.println("2: " + analysis.parse("中国加油!").getDisplay());	
```
	    
输出： 

1: 0  
2: 正面  


正面：1  
负面：-1  
中性：0  

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)