### 运行命令
go run main.go -orm gorm -orm xorm -orm zorm > mysql.txt

beego-orm 更新速度快是因为在连接对象内做了stmt缓存,db_alias.go 148行 stmt, err := d.getStmt(query)  
实际环境exec都是有事务的,也就是不同的orm对象,压测需要去掉这个缓存,这样比较公平


### 

```
gorm
                   Insert:   2000     9.60s      4800617 ns/op    5407 B/op    119 allocs/op
       BulkInsert 100 row:   2000     Don't support bulk insert - https://github.com/jinzhu/gorm/issues/255
                   Update:   2000     0.73s       366905 ns/op    9157 B/op    226 allocs/op
                     Read:   2000     0.45s       223720 ns/op    5931 B/op    138 allocs/op
     MultiRead limit 1000:   2000    26.40s     13201878 ns/op 2392826 B/op  57031 allocs/op
xorm
                   Insert:   2000    12.63s      6315205 ns/op    2365 B/op     56 allocs/op
       BulkInsert 100 row:   2000    23.89s     11945333 ns/op  253812 B/op   4250 allocs/op
                   Update:   2000     0.39s       195846 ns/op    2529 B/op     87 allocs/op
                     Read:   2000     0.55s       276055 ns/op    8648 B/op    227 allocs/op
     MultiRead limit 1000:   2000    30.77s     15382967 ns/op 1637098 B/op  72088 allocs/op
zorm
                   Insert:   2000     9.05s      4524909 ns/op    2146 B/op     33 allocs/op
       BulkInsert 100 row:   2000     Don't support bulk insert
                   Update:   2000     0.51s       253577 ns/op    2232 B/op     32 allocs/op
                     Read:   2000     0.28s       141890 ns/op    1616 B/op     43 allocs/op
     MultiRead limit 1000:   2000    13.93s      6967146 ns/op  694286 B/op  23054 allocs/op

Reports: 

  2000 times - Insert
      zorm:     9.05s      4524909 ns/op    2146 B/op     33 allocs/op
      gorm:     9.60s      4800617 ns/op    5407 B/op    119 allocs/op
      xorm:    12.63s      6315205 ns/op    2365 B/op     56 allocs/op

  2000 times - BulkInsert 100 row
      xorm:    23.89s     11945333 ns/op  253812 B/op   4250 allocs/op
      gorm:     Don't support bulk insert - https://github.com/jinzhu/gorm/issues/255
      zorm:     Don't support bulk insert

  2000 times - Update
      xorm:     0.39s       195846 ns/op    2529 B/op     87 allocs/op
      zorm:     0.51s       253577 ns/op    2232 B/op     32 allocs/op
      gorm:     0.73s       366905 ns/op    9157 B/op    226 allocs/op

  2000 times - Read
      zorm:     0.28s       141890 ns/op    1616 B/op     43 allocs/op
      gorm:     0.45s       223720 ns/op    5931 B/op    138 allocs/op
      xorm:     0.55s       276055 ns/op    8648 B/op    227 allocs/op

  2000 times - MultiRead limit 1000
      zorm:    13.93s      6967146 ns/op  694286 B/op  23054 allocs/op
      gorm:    26.40s     13201878 ns/op 2392826 B/op  57031 allocs/op
      xorm:    30.77s     15382967 ns/op 1637098 B/op  72088 allocs/op

```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)