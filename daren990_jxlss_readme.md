## jxls 简介

`jxls` 是一个导出excel文件的库，在原excel文件上加入jxls指令做成模板文件，然后几乎可以原样生成excel文件。   
官网[http://jxls.sourceforge.net/index.html](http://jxls.sourceforge.net/index.html)

## jxlss 简介

本工程 `jxlss` 是基于 `jxls2`（当前版本2.4.3） 的基础上增加了一些功能和修改一些问题，具体改动内容请看下面改动章节。

## 生成excel文件

### 生成效果

- 模板文件   
![excel模板](https://images.gitee.com/uploads/images/2018/1207/183157_861d4ce9_1424806.png "模板.png")   

- jxls指令，注意指令`jx:area(lastCell="H20")`，这个是一定要的，并指定生成内容的区域`lastCell="H20"`，超出这个区域的内容则不生成   
![jxls指令](https://images.gitee.com/uploads/images/2018/1207/183835_2d34d17c_1424806.png "指令.png")

- 最终生成的excel文件   
![生成的excel](https://gitee.com/uploads/images/2018/0125/181030_d4a2ba5c_1424806.png "生成文件.png")

### 生成步骤

1. 添加本库jar包或源码到项目中。
2. 准备excel模板，在模板中加入需要填充数据的指令。
3. 调用下面代码生成excel文件：

``` java
            JxlsBuilder
                /* -- 加载模板方式 -- */
                // 使用文件流加载模板
                // .getBuilder(inputStream)
                // 使用文件加载模板
                // .getBuilder(file)
                // 使用路径加载模板，可以是相对路径，也可以绝对路径
                .getBuilder("dome/employee.xlsx")

                /* -- 输出文件方式 -- */
                // 指定输出的文件流
                // .out(outputStream)
                // 指定输出的文件
                // .out(file)
                // 指定输出的路径
                .out(outPath)

                /* 添加生成的数据 */
                .putVar("name", data)
                // 设置图片路径的根目录
                .imageRoot("imgRoot")
                // 设置如果图片缺失不抛异常继续生成文件
                .ignoreImageMiss(true)
                // 添加自定工具类
                // .addFunction("jx", new JxlsUtil())
                .build();
```

## 设置模板文件目录和图片路径根目录

设置代码，建议在工程启动时设置：
``` java
        JxlsConfig.config()
                // 锁住配置，本次修改之后不能再修改配置
                // .lock()
                // 设置模板文件根目录
                .templateRoot("模板文件目录路径")
                // 设置图片路径根目录
                .imageRoot("图片文件目录路径")
                // 忽略warn警告
                .silent(true);
```

### 模板文件目录

模板文件目录默认为：`classpath:jxls_templates`。

``` java
// 加载模板文件时可以使用文件绝对路径，也可以相对路径。如果是相对路径则为模板文件目录下的路径
JxlsBuilder.getBuilder("dome/employee.xlsx");
```

### 图片路径根目录

使用指令 `jx:image` 插入图片时，的`src`属性支持图片路径（原jxls只支持byte[]数据）。
`src` 支持绝对路径和相对路径。如果使用相对路径则需要设置图片路径根目录，设置方式有两种：

``` java
// 1. 全局设置
JxlsConfig.config().imageRoot("图片文件目录路径");
// 2. 生成文件的时候设置（本次生成文件有效）
JxlsBuilder.getBuilder("dome/employee.xlsx").imageRoot("图片文件目录路径")...
```

## 基于 jxls 2.4.3 上的改动

- 指令 `jx:image` 的`src`属性支持图片路径，原jxls只支持byte[]数据。
- 新增指令 `jx:merge`，用于合并单元格。
- 新增指令 `jx:keep`，如果生成的单元格样式被改变了，可以试用该指定恢复单元格样式。
- 新增自定义工具 [JxlsUtil](https://gitee.com/lnkToKing/jxlss/blob/master/src/main/java/pres/lnk/jxlss/JxlsUtil.java)， 在表达式中使用 `jxu:method()` 调用工具的方法。
- 优化指令 `jx:grid`，props支持String[]类型和可以通过参数传进来

## 指令使用说明

### `jxls`的指令形式：
```
jx: (attr1='val1' attr2='val2' ... attrN='valN' lastCell=  areas=[" ", " "])
```
指令写在单元格批注里，以`jx:`开头，包含有指令名称`command_name`、自定义属性`attr`、`lastCell`和`areas`。需要注意一点，每条指令都不能换行。   
其中`lastCell`为必填属性，作用是指定当前指令的作用区域，超出区域的单元格不处理。   
如`jx:area`指令，这个指令很重要，每个excel模板都需要添加该指令，这个指令是指定这个模板生成时填充数据的单元格范围，超出该范围的指令和表达式则不处理。

### 指令列表

- [jx:area](https://gitee.com/lnkToKing/jxlss/wikis/pages?title=area%E6%8C%87%E4%BB%A4&parent=%E6%8C%87%E4%BB%A4)
- [jx:each](https://gitee.com/lnkToKing/jxlss/wikis/pages?title=each%E6%8C%87%E4%BB%A4&parent=%E6%8C%87%E4%BB%A4)
- [jx:if](https://gitee.com/lnkToKing/jxlss/wikis/pages?title=if%E6%8C%87%E4%BB%A4&parent=%E6%8C%87%E4%BB%A4)
- [jx:image](https://gitee.com/lnkToKing/jxlss/wikis/pages?title=image%E6%8C%87%E4%BB%A4(jxlss%E6%9C%89%E5%A2%9E%E5%BC%BA)&parent=%E6%8C%87%E4%BB%A4) （`jxlss`增强）
- [jx:updateCell](http://jxls.sourceforge.net/reference/updatecell_command.html)
- [jx:grid](https://gitee.com/lnkToKing/jxlss/wikis/pages?title=grid%E6%8C%87%E4%BB%A4(jxlss%E6%9C%89%E4%BC%98%E5%8C%96)&parent=%E6%8C%87%E4%BB%A4)
- [jx:merge](https://gitee.com/lnkToKing/jxlss/wikis/pages?title=merge%E6%8C%87%E4%BB%A4(jxlss%E6%B7%BB%E5%8A%A0)&parent=%E6%8C%87%E4%BB%A4) （`jxlss`增加）
- [jx:keep](https://gitee.com/lnkToKing/jxlss/wikis/pages?title=keep%E6%8C%87%E4%BB%A4(jxlss%E6%B7%BB%E5%8A%A0)&parent=%E6%8C%87%E4%BB%A4) （`jxlss`增加）
- [自定义指令](https://gitee.com/lnkToKing/jxlss/wikis/pages?title=%E8%87%AA%E5%AE%9A%E4%B9%89%E6%8C%87%E4%BB%A4&parent=%E6%8C%87%E4%BB%A4)

### 更新日志
- jxlss 1.0.4 2018年12月7日   
修复：merge指令lastCell属性指定合并区域优先级比minCols和minRows属性高问题（应该是minCols和minRows属性比lastCell属性的优化级要高）

- jxlss 1.0.3（略）   
- jxlss 1.0.2（略）   

- jxlss 1.0.1 2018年5月2日   
优化Grid指令。   
解决项目打包成jar运行时默认模板目录和默认图片目录设置无法读取jar内部文件问题，同时新增支持默认目录可放在jar包同一个目录下。

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)