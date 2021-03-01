### 介绍
* 爬取`https://swapi.co/`页面的所有数据
  * `people`
  * `films`
  * `species`
  * `films`
  * `planets`
  * `starships`

* `Version 1 BoltDB`
  * `data/bolt/data.db`    为生成的相应的`BoltDB`数据库
    * `show/db.txt`     数据库存储的内容显示
  * `dbOp/dbOp.go`    提供一系列数据库获取数据封装好的的方法
    * 返回样例展示
      * `show/people.json` 
      * `show/film.json`     
      * `show/planet.json`    
      * `show/specie.json`    
      * `show/starship.json` 
      * `show/vehicle.json`   


* `Version 2 MySQL`
  * `data/mysql/`    为导出的`MySQL`数据库



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)