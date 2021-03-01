# py-scratch

下载项目->导入项目->运行项目

导入项目：下载项目后导入到pycharm中，然后需要下载requirements.txt中的包，如果发现pycharm没有自动下载包的话可以手动下载
，先安装pip，然后在命令行中敲：pip install bs4 pymongo requests json。当然也可以用：pip install -r requirements.txt直接下载。

运行项目：在pycharm中直接右击scratch_flight_number.py然后点Run就可以，命令行下用 python scratch_flight_number.py

项目说明：项目是根据某个固定的url去爬取网页或json，然后使用bs4做解析。获取到了想要的数据之后和原来的数据作比较，判断原数
据中是否包含新数据，如果不包含则添加到新的数组中返回，返回后将新数据追加到文件中同时插入到mongodb中

注意事项：
1，随着时间的推移url可能会过期
2，第一次运行项目可能会等待时间较长
3，注意这里插入到数据库中的数据是每次爬取到的新数据，如果没有新数据则不会插入
4，对项目有疑问可在微信公众号中与我交流，微信公众号：裸睡的猪



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)