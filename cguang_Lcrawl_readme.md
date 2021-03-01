#框架简介：


使用PHP+MySQL实现正方教务系统爬虫功能。


目前已经实现通过模拟登陆来获取成绩、课表、选课、考试、等级考试、补考、成绩统计等数据的爬取并过滤存储。


使用简单！注释完整！！！

#项目地址：

http://lcrawl.lzjtuhand.com

http://www.luoning.me/lcrawl.html

#框架详情：

 classes 为框架核心类文件； temp 为缓存文件夹，存储临时cookie,可定期清除；
 autoloader.php 框架自动载入文件； run.php 框架入口文件，使用时直接 include 'run.php'; 即可。

#使用方法：

```php

 getGrade($jwid,$jwpwd);

//获取考试安排数据
$Lcrawl->getExam($jwid,$jwpwd);

//获取选课安排数据
$Lcrawl->getChooseCourses($jwid,$jwpwd);

//获取等级考试数据
$Lcrawl->getGradeExam($jwid,$jwpwd);

//获取补考安排数据
$Lcrawl->getMakeupExam($jwid,$jwpwd);

//获取课表数据
$Lcrawl->getSchedule($jwid,$jwpwd);

//获取成绩统计数据
$Lcrawl->getGradeCount($jwid,$jwpwd);
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)