fastexcel
=========

作者:peiyu 
[我的微博](http://weibo.com/1728407960) 
QQ:125331682 

快速简单读取excel数据，将Apache POI进行了薄封装，基于注解，更加易于使用 

#使用样例
```java
FastExcel fastExcel = new FastExcel("E:/data.xlsx");
        fastExcel.setSheetName("活动信息数据");
        List  tests = fastExcel.parse(MyTest.class);
        if(null != tests && !tests.isEmpty()) {
            for(MyTest myTest : tests) {
                LOG.debug("记录:{}", myTest.toString());
            }
        } else {
            LOG.debug("没有结果");
        }
```

映射类

```java
 public class MyTest {

    @MapperCell(cellName = "名称")
    private String name;

    @MapperCell(cellName = "联系电话")
    private String phone;

    @MapperCell(cellName = "地址")
    private String address;

    @MapperCell(cellName = "一级分类ID")
    private int type;

    @MapperCell(cellName = "经度")
    private double lat;

}
```

Maven 项目引入
==========
```xml
 
     com.github.sd4324530 
     fastexcel 
     0.0.2 
 
```

开源协议
==========
[Apache License](http://www.apache.org/licenses/LICENSE-2.0)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)