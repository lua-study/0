
## Android解析Excel(xls/xlsx)

### xls与xlsx的区别：

- .xls是03版Office Microsoft Office Excel 工作表的格式,能被所有的office程序打开
- .xlsx是07版Office Microsoft Office Excel 工作表的格式，只能用2007office以上的版本打开。基于XML的压缩文件格式取代了其目前专有的默认文件格式，在传统的文件名扩展名后面添加了字母x（即.docx取代.doc、.xlsx取代.xls，等等），使其占用空间更小。

### 说明

>1.对于 .xls 格式 sheet1 的第1行、第1列命名为 s1_row1_col1_xls
>
>2.代码中存储Excel数据的格式为 的形式


**本文使用到的Jar包、Excel文件以及源码:[传送门]( )**
[个人博客](https://www.kitto.fun/)


#### 一、**[jxl]( )** 解析xls格式Excel

由于是直接调用API所以这里直接上代码

部分代码:

```kotlin
fun xlsJxl(file: File): Map >> {
    val result = ArrayMap >>()
    Workbook.getWorkbook(file).sheets.forEach { sheet ->
        val rowsList = ArrayList >()//列数据
        val sheetName = sheet.name
        for (i in 0 until sheet.rows) {
            rowsList.add(
                sheet.getRow(i).map { it.contents }
            )
        }
        result[sheetName] = rowsList
    }
    return result
}

```
xls格式Excel文件sheet1内容:

![xls格式Excel文件sheet1内容](https://images.gitee.com/uploads/images/2019/1216/151756_b30cb8cf_1216119.png)

xls格式Excel文件sheet2内容:

![xls格式Excel文件sheet2内容](https://images.gitee.com/uploads/images/2019/1216/151756_540aa161_1216119.png)

xls格式Excel文件sheet3内容:

![xls格式Excel文件sheet3内容](https://images.gitee.com/uploads/images/2019/1216/151756_357fd88d_1216119.png)

运行结果：

![jxl_xls_result.png](https://images.gitee.com/uploads/images/2019/1216/151756_f8279ded_1216119.png)


#### 二、个人理解分析xlsx格式Excel(无法在项目中使用)

由于jxl无法解析xlsx，所以必须另辟蹊径，在开头提过，xlsx格式是基于XML文件来生成的，所以我们将`.xls`的后缀改为`.zip`并将其进行解压。我们将会看到以下的目录结构:

xlsx解压的根目录:

![xlsx解压的根目录](https://images.gitee.com/uploads/images/2019/1216/151756_5e2f1e2c_1216119.png)

xlsx解压根目录下的xl:

![xlsx解压根目录下的xl](https://images.gitee.com/uploads/images/2019/1216/151756_e2b06403_1216119.png)

xlsx解压根目录下的xl/worksheets:

![xlsx解压根目录下的xl/worksheets](https://images.gitee.com/uploads/images/2019/1216/151756_d2253950_1216119.png)

我们要使用的文件是`sharedStrings.xml`文件(里面存在Excel中的数据)、`sheet1.xml`、`sheet2.xml`、`sheet3.xml`。下面通过分析sheet文件与sharedStrings的找到它们的对应关系:

xlsx格式Excel文件sheet1内容:

![xlsx格式Excel文件sheet1内容](https://images.gitee.com/uploads/images/2019/1216/151756_9759bfe2_1216119.png)

xlsx格式Excel文件sheet2内容:

![xlsx格式Excel文件sheet2内容](https://images.gitee.com/uploads/images/2019/1216/151756_a55e9042_1216119.png)

xlsx格式Excel文件sheet3内容:

![xlsx格式Excel文件sheet3内容](https://images.gitee.com/uploads/images/2019/1216/151756_84d3ef27_1216119.png)

sharedStrings.xml内容:

![sharedStrings.xml内容](https://images.gitee.com/uploads/images/2019/1216/151756_27015e8a_1216119.png)

sheet1.xml内容:

![sheet1.xml内容](https://images.gitee.com/uploads/images/2019/1216/151756_5aeefc1c_1216119.png)

对应关系:

![对应关系](https://images.gitee.com/uploads/images/2019/1216/151756_f1baf425_1216119.png)

 注意在`sharedString.xml`上面截图做记号的红色框框（从0-35的序号只是为了好理解补充的，实际上里面是不存在的）。从 最后一张图中可以很好的看出 `sheet1.xml`与`sharedString.xml`的对应关系，即sheet1中 **" v "** 标签里的数字为sharedString中的索引， **" row "** 标签为行。所以我们只要解析xml读取出sharedString中的数据，每个sheet按行读取索引来整理数据

部分代码:
```kotlin
fun xlsxSelf(file: File): Map >> {
    val result = ArrayMap >>()
    //获取所有元素
    val zipFile = ZipFile(file)
    val cellsList = ArrayList ()
    val xmlPullParser = Xml.newPullParser()
    zipFile.getInputStream(zipFile.getEntry("xl/sharedStrings.xml"))
        .use { inputStream ->
            xmlPullParser.setInput(inputStream, "utf-8")
            var eventType = xmlPullParser.eventType
            while (eventType != XmlPullParser.END_DOCUMENT) {
                if (eventType == XmlPullParser.START_TAG && xmlPullParser.name == "t") {
                    cellsList.add(xmlPullParser.nextText())
                }
                eventType = xmlPullParser.next()
            }
        }
    //获取cell对应的index,并添加到Map中保存
    file.inputStream().use { inputStream ->
        ZipInputStream(inputStream).use { zis ->
            var zipDir: ZipEntry? = null
            while ({ zipDir = zis.nextEntry;zipDir }() != null) {
                if (zipDir!!.name.startsWith("xl/worksheets/", true) &&
                    zipDir!!.name.endsWith("xml", true)
                ) {
                    val rowsList = ArrayList >()
                    zipFile.getInputStream(zipFile.getEntry(zipDir!!.name))
                        .use { inputStream ->
                            xmlPullParser.setInput(inputStream, "utf-8")
                            val itemList: ArrayList  = ArrayList()//用于保存每行的数据
                            var eventType = xmlPullParser.eventType
                            while (eventType != XmlPullParser.END_DOCUMENT) {
                                when (eventType) {
                                    XmlPullParser.START_TAG -> {
                                        if (xmlPullParser.name == "row") {
                                            itemList.clear()//每行数据开始清空容器
                                        } else if (xmlPullParser.name == "v") {
                                            val index = xmlPullParser.nextText()
                                            itemList.add(cellsList[index.toInt()])
                                        }
                                    }
                                    XmlPullParser.END_TAG -> {
                                        if (xmlPullParser.name == "row") {
                                            //将行数据保存
                                            rowsList.add(itemList.toList())
                                        }
                                    }
                                }
                                eventType = xmlPullParser.next()
                            }
                            //
                            result[zipDir!!.name.sheetName()] = rowsList
                        }
                }
            }
        }
    }
    return result
}
```
运行结果:

![运行结果](https://images.gitee.com/uploads/images/2019/1216/151756_4353430a_1216119.png)


问题：这只实现了简单解析 .xlsx 格式的 Excel。其中还存在一些问题未解决，无法获得到重命名的sheet的名字，即，解压得到sheet都是按sheet1,sheet2,sheet3命名的。我分析解压的xml后，还无法找到sheet名字的对应关系。还有一些关于格式不同也会导致解析问题，总的来说还需要对文件进行进一步的分析。所以上面的方法无法使用在正式项目中。

#### 三、[POI]( )解析xls/xlsx格式Excel(可应用于项目中)

> The Apache POI distribution consists of support for many document file formats. This support is provided in several Jar files. Not all of the Jars are needed for every format. The following tables show the relationships between POI components, Maven repository tags, and the project's Jar files. 
>
> Apache POI发行版支持多种文档文件格式。这种支持是在几个Jar文件中提供的。并不是每种格式都需要所有的jar。下表显示了POI组件、Maven存储库标记和项目Jar文件之间的关系。

![POI_components](https://images.gitee.com/uploads/images/2019/1216/151756_0c94b054_1216119.png)


- HSSF是我们将Microsoft Excel 97（-2003）文件格式（BIFF8）移植到纯Java的端口 -> xls格式
- XSSF是Microsoft Excel XML（2007+）文件格式（OOXML）到纯Java的移植 -> xlsx格式

从上面[表格]( )中可以看出我们要解析Excel的xls、xlsx需要导入`poi`与`poi-ooxml`的jar包，但是由于Android直接引用**POI**的jar在解析xlsx格式Excel时会出现错误，这里我使用之前在**Github**找到的经过修改后的jar包(但是过挺久的了所以找不到原项目了。详情请查看[源码]( ))

部分代码:
```kotlin
    fun excelPOI(file: File): Map >> {
        val result = ArrayMap >>()
        WorkbookFactory.create(file).use { workBook ->
            for (sheetIndex in 0 until workBook.numberOfSheets) {
                val rowsList = ArrayList >()
                val sheet = workBook.getSheetAt(sheetIndex)
                sheet.rowIterator()
                    .forEach { row ->
                        val itemList: ArrayList  = ArrayList()//用于保存每行的数据
                        row.cellIterator().forEach { cell ->
                            itemList.add(cell.stringCellValue)
                        }
                        rowsList.add(itemList)
                    }
                result[sheet.sheetName] = rowsList
            }
        }
        return result
    }
```

**POI**不仅可以操作Excel，也可以操作其他Office文档，而且功能特别强大。本文只展示了**POI**解析Excel中内容的功能，更多功能请查看官方文档。
















 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)