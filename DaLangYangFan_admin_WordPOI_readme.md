# WordPOI

[![Download](https://img.shields.io/badge/download-jar-blue.svg)](https://raw.githubusercontent.com/jenly1314/WordPOI/master/libs/word-poi-1.0.1.jar)
[![JitPack](https://jitpack.io/v/jenly1314/WordPOI.svg)](https://jitpack.io/#jenly1314/WordPOI)
[![CI](https://travis-ci.org/jenly1314/WordPOI.svg?branch=master)](https://travis-ci.org/jenly1314/WordPOI)
[![CircleCI](https://circleci.com/gh/jenly1314/WordPOI.svg?style=svg)](https://circleci.com/gh/jenly1314/WordPOI)
[![License](https://img.shields.io/badge/license-Apche%202.0-blue.svg)](http://www.apache.org/licenses/LICENSE-2.0)
[![Blog](https://img.shields.io/badge/blog-Jenly-9933CC.svg)](https://jenly1314.github.io)
[![QQGroup](https://img.shields.io/badge/QQGroup-20867961-blue.svg)](http://shang.qq.com/wpa/qunwpa?idkey=8fcc6a2f88552ea44b1411582c94fd124f7bb3ec227e2a400dbbfaad3dc2f5ad)

WordPOI是一个将Word接口文档转换成JavaBean的工具库，主要目的是减少部分无脑的开发工作。

> 核心功能：将文档中表格定义的实体转换成Java实体对象
 
## WordPOI特性说明  
 1. 支持解析doc格式和docx格式的Word文档
 2. 支持批量解析Word文档并转换成实体
 3. 解析配置支持自定义，详情请查看{@link ParseConfig}相关配置
 4. 虽然解析可配置，但因文档内容的不可控，解析转换也具有一定的局限性

> 只要在文档上定义实体对象时，尽量满足示例文档的规则，就可以规避解析转换时的局限性。

## ParseConfig属性说明
| 属性 | 值类型 | 默认值 | 说明 |
| :------| :------ | :------ | :------ |
| startTable | int |0| 开始表格 |
| startRow | int |1| 开始行 |
| startColumn | int |0| 开始列 |
| fieldNameColumn | int | 0 | 字段名称所在列 |
| fieldTypeColumn | int | 1 | 字段类型所在列 |
| fieldDescColumn | int | 2 | 字段注释说明所在列 |
| charsetName | String | UTF-8 | 字符集编码 |
| genGetterAndSetter | boolean | true | 是否生成get和set方法 |
| genToString | boolean | true | 是否生成toString方法 |
| useLombok | boolean |false| 是否使用Lombok |
| parseEntityName | boolean |false| 是否解析实体名称 |
| entityNameRow | int | 0 | 实体名称所在行 |
| entityNameColumn | int | 0 | 实体名称所在列 |
| serializable | boolean | false | 是否实现Serializable序列化 |
| showHeader | boolean | true | 是否显示头注释 |
| header | String | Created by WordPOI | 头注释内容 |
| transformations | Map&lt;String,String&gt; |  | 需要转型的集合（自定义转型配置） |


## 引入

### Maven：
```maven
 
   com.king.poi 
   word-poi 
   1.0.1 
   pom 
 
```
### Gradle:
```gradle
compile 'com.king.poi:word-poi:1.0.1'
```

### Lvy:
```lvy
 
    
 
```

###### 如果Gradle出现compile失败的情况，可以在Project的build.gradle里面添加如下：（也可以使用上面的GitPack来complie）
```gradle
allprojects {
    repositories {
        maven { url 'https://dl.bintray.com/jenly/maven' }
    }
}
```

## 引入的库：
```gradle
compile 'org.apache.poi:poi:4.1.0'
compile 'org.apache.poi:poi-ooxml:4.1.0'
compile 'org.apache.poi:poi-scratchpad:4.1.0'
```

如想直接引入jar包可直接点击左上角的Download下载最新的jar，然后引入到你的工程即可。

## 示例

代码示例 (直接在main方法中调用即可)
```Java
        try {

            /**
             * 解析文档中的表格实体，表格包含了实体名称，只需配置 {@link ParseConfig#parseEntityName} 为 true 和相关对应行，即可开启自动解析实体名称，自动解析实体名称
             * {@link ParseConfig}中包含解析时需要的各种配置，方便灵活的支持文档中更多的表格样式
             */
            ParseConfig config  = new ParseConfig.Builder().startRow(2).parseEntityName(true).build();
            WordPOI.wordToEntity(Test.class.getResourceAsStream("Api3.docx"),false,"C:/bean/","com.king.poi.bean",config);
            //解析文档docx格式  需要传生成的对象实体名称
//            WordPOI.wordToEntity(Test.class.getResourceAsStream("Api1.docx"),false,"C:/bean/","com.king.poi.bean","Result","PageInfo");
            //解析文档docx格式  需要传生成的对象实体名称
//            WordPOI.wordToEntity(Test.class.getResourceAsStream("Api2.doc"),true,"C:/bean/","com.king.poi.bean","TestBean");
        } catch (Exception e) {
            e.printStackTrace();
        }

```


* 文档实体示例一（默认格式，见文档 Api1.docx）

1.1.	Result （响应结果实体）

| 字段    | 字段类型  |   说明  |
| :------| :------ | :------ |
|code    |  String | 0-代表成功，其它代表失败 |
|desc    |  String |	操作失败时的说明信息 |
|data    |	T	   |   返回对应的泛型 实体对象 |


1.2.	PageInfo （页码信息实体）

| 字段     |   字段类型    |   说明  |
| :------ | :------ | :------ |
| curPage   | Integer   |	当前页码 |
| pageSize  | Integer   |	页码大小，每一页的记录条数 |
| totalPage | Integer	| 总页数 | 
| hasNext   | Boolean	|  是否有下一页 | 
| data	    | List&lt;T&gt; | 	泛型T为对应的数据记录实体 | 


* 文档实体示例二（自动解析实体名称格式，见文档 Api3.docx）

1.1.    响应结果实体

 
     
    	 Result     
    
    
         字段  
         字段类型  
         说明  
    
    
         code  
         String  
         0-代表成功，其它代表失败  
    
    
         desc  
         String  
         操作失败时的说明信息  
    
    
         data  
         T  
         返回对应的泛型&lt;T&gt;实体对象  
    

 


1.2.    页码信息实体

 
     
    	 PageInfo     
    
    
         字段  
         字段类型  
         说明  
    
    
         curPage  
         Integer  
         当前页码  
    
    
         curPage  
         Integer  
         当前页码  
    
    
         pageSize  
         Integer  
         页码大小，每一页的记录条数  
    
    
         totalPage  
         Integer  
         总页数  
    
    
         hasNext  
         Boolean  
         是否有下一页  
    
    
         data  
         List&lt;T&gt;  
         泛型T为对应的数据记录实体  
    

 


更多使用详情，请查看[Test](src/test/java/Test.java)中的源码使用示例或直接查看[API帮助文档](https://jenly1314.github.io/projects/WordPOI/doc/)

## 版本记录

#### v1.0.1：2019-9-17
*  支持自动解析实体名称
*  支持添加自定义转型配置

#### v1.0.0：2019-6-12
*  WordPOI初始版本

## 赞赏
如果您喜欢WordPOI，或感觉WordPOI帮助到了您，可以点右上角“Star”支持一下，您的支持就是我的动力，谢谢 :smiley: 
您也可以扫描下面的二维码，请作者喝杯咖啡 :coffee:
     
         
         
         
         
     

## 关于我
   Name:  Jenly 

   Email:  jenly1314#gmail.com  /  jenly1314#vip.qq.com 

   CSDN:  jenly121 

   博客园:  jenly 

   Github:  jenly1314 

   加入QQ群:  20867961 
    
        
        
    



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)