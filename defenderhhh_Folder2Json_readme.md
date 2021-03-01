#Folder2Json

### Contact

Eran : `iamzealotwang@126.com`  

QQ  :  `66840053`

### 概述

Folder2Json 用来扫描某个文件夹下的所有文件,并生成一个相对于扫描文件夹根目录的JSON描述文件

### How to use

```
java -jar folder2json.jar 要扫描的目录 导出的Json文件位置

比如:
java -jar folder2json.jar E:\WorkSpace\Tools\Folder2Json\example E:\WorkSpace\Tools\Folder2Json\example\result.json

```

### 示例

文件夹结构:

![01](img/01.jpg)

导出文件的文件结构: 

```
{
  "rootFolderName": "example",
  "allFileInfoList": [
    {
      "name": "c.xml",
      "size": 0,
      "path": "example/A/C/c.xml"
    },
    {
      "name": "a.txt",
      "size": 0,
      "path": "example/A/C/D/F/a.txt"
    },
    {
      "name": "b.png",
      "size": 0,
      "path": "example/A/C/E/b.png"
    },
    {
      "name": "d.jpg",
      "size": 0,
      "path": "example/B/d.jpg"
    },
    {
      "name": "result.json",
      "size": 327,
      "path": "example/result.json"
    }
  ]
}
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)