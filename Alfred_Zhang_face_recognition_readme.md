# face_recognition

## 项目的目录结构为： 

* Root
    *  Fac.exe
    * Data
        * Train
            * image\\*.jpg
            * index.txt
            * name.txt
        * Model
            * *.xml （自带的模型）
        * Temp(运行时生成)
            * index.txt
            * name.txt
            * image\\*.jpg (剪切后的图片)
            * output.xml （训练的模型）

## 程序运行逻辑
1. 程序自带Data文件夹,其中Temp文件夹中只含有images文件夹，其余为空。
2. 主办方给定peoplelist.txt以及videolist.txt，程序会根据peoplelist.txt生成temp文件夹下的index.txt和name.txt。
这里的index.txt是在自带的index.txt后面添加新内容生成的，同理name.txt也是。
3. 例如：
    1. peoplelist.txt
    
        ```
        ...
        ..\Data\Temp\InputImages\yangyang_1.jpeg yangyang
        ..\Data\Temp\InputImages\yangyang_2.jpg yangyang
        ..\Data\Temp\InputImages\yangyang_3.png yangyang
        ..\Data\Temp\InputImages\yangyang_4.jpeg yangyang
        ..\Data\Temp\InputImages\yangyang_5.jpg yangyang
        ..\Data\Temp\InputImages\yangyang_6.png yangyang
        ..\Data\Temp\InputImages\yangyang_7.jpeg yangyang
        ...
        ```

    这说明上述的几张图片是yangyang的图，程序会读取这些图，剪切并将其存入Temp/images/中。

    2. 假设自带的index.txt内容如下：
    
        ```
        ...
        ..\Data\Train\trainingdata\FERET-205\5.jpg;205
        ..\Data\Train\trainingdata\FERET-205\6.jpg;205
        ..\Data\Train\trainingdata\FERET-205\7.jpg;205
        ..\Data\Train\trainingdata\FERET-206\1.jpg;206
        ..\Data\Train\trainingdata\FERET-206\2.jpg;206
        ..\Data\Train\trainingdata\FERET-206\3.jpg;206
        ..\Data\Train\trainingdata\FERET-206\4.jpg;206
        ···
        ```

    3. 则新生成的index.txt为:

        ```
        ...
        ..\Data\Train\trainingdata\FERET-205\5.jpg;205
        ..\Data\Train\trainingdata\FERET-205\6.jpg;205
        ..\Data\Train\trainingdata\FERET-205\7.jpg;205
        ..\Data\Train\trainingdata\FERET-206\1.jpg;206
        ..\Data\Train\trainingdata\FERET-206\2.jpg;206
        ..\Data\Train\trainingdata\FERET-206\3.jpg;206
        ..\Data\Train\trainingdata\FERET-206\4.jpg;206
        ..\Data\Temp\images\yangyang_1.jpeg;207
        ..\Data\Temp\images\yangyang_2.jpg;207
        ..\Data\Temp\images\yangyang_3.png;207
        ..\Data\Temp\images\yangyang_4.jpeg;207
        ···
        ```

    注意，训练所用的图片是自带的加上已裁剪的图片（存储在Data/Temp/images/中）

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)