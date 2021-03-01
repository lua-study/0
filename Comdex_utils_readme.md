#utils

包装一些常用的函数 golang


### iputil


ip地址转换为整型和整型转换为ip地址


```go
println(iputil.IP2Long("192.168.60.155"))

println(iputil.Long2IP(iputil.IP2Long("192.168.60.155")))
```


### sqlutil

golang的默认数据库查询接口，只支持单个元素扫描，不能通过结构体传值

`sqlutil`可以通过直接把结果复制给接口体，或者结构体数组

`github.com/go-sql-driver/mysql`库需要开启parseTime=true


```go

type User struct {
    id          int64
    username    string
    password    string
}

db, _ := sql.Open("mysql", "root:root@/tl_album?charset=utf8&parseTime=true")
defer db.Close()

rows, _  := db.Query("select * from user where id = ?", 1)
var one User
sqlutil.One(&one, rows)

fmt.Println(one)


rows, _ := db.Query("select * from user where id < 20")
var users []User
sqlutils.All(&users, rows)

fmt.Println(users)
```


### strutil

golang里面字符串转换为整型库，默认返回错误，有两个返回值，影响操作

所以忽略了错误处理，有`Int`, `Int64`, `Int32`三个函数


```go
println(Int64("1234555"))
println(Int("1234555"))
println(Int32("1234555"))
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)