 
   
     
   
 

 
    the missing golang data admin builder tool.
 

 
     Documentation  | 
     中文文档  |
     DEMO 
 

 
     
     
     
     
     
     
     
  

 
    Inspired by  laravel-admin 
 

## Preface

goAdmin is a toolkit help you to build a data visualization and manage platform for your golang app.

 Now is the beta version. It means that you may meet some unpredictable bugs. The v1.0 will be released about October 8th. 

demo: [http://demo.go-admin.cn/admin](http://demo.go-admin.cn/admin)
account: admin  password: admin

demo source code: https://github.com/GoAdminGroup/demo

![](http://www.go-admin.cn/assets/imgs/interface.jpg)

## Feature

- beautiful admin interface builder powerd by adminlte
- many plugins to use(working on it)
- powerful auth manage system
- support most of the go web framework

## How to

see the [docs](http://www.go-admin.cn/en) for detail

[a super simple example here](https://github.com/GoAdminGroup/example)

### Step 1: import sql

[https://github.com/chenhg5/go-admin/blob/master/examples/datamodel/admin.sql](https://github.com/chenhg5/go-admin/blob/master/examples/datamodel/admin.sql)

### Step 2: create main.go

  main.go 
 

```go
package main

import (
	"github.com/gin-gonic/gin"
	_ "github.com/chenhg5/go-admin/adapter/gin"
	"github.com/chenhg5/go-admin/engine"
	"github.com/chenhg5/go-admin/plugins/admin"
	"github.com/chenhg5/go-admin/modules/config"
	"github.com/chenhg5/go-admin/examples/datamodel"
	"github.com/chenhg5/go-admin/modules/language"
)

func main() {
	r := gin.Default()

	eng := engine.Default()

	// global config
	cfg := config.Config{
		Databases: config.DatabaseList{
			"default": {
				Host:         "127.0.0.1",
				Port:         "3306",
				User:         "root",
				Pwd:          "root",
				Name:         "godmin",
				MaxIdleCon: 50,
				MaxOpenCon: 150,
				Driver:       "mysql",
			},
        	},
		UrlPrefix: "admin",
		// STORE is important. And the directory should has permission to write.
		Store: config.Store{
		    Path:   "./uploads", 
		    Prefix: "uploads",
		},
		Language: language.EN,
		// debug mode
		Debug: true,
		// log file absolute path
		InfoLogPath: "/var/logs/info.log",
		AccessLogPath: "/var/logs/access.log",
		ErrorLogPath: "/var/logs/error.log",
	}

    	// Generators: see https://github.com/chenhg5/go-admin/blob/master/examples/datamodel/tables.go 
	adminPlugin := admin.NewAdmin(datamodel.Generators)
	
	// add generator, first parameter is the url prefix of table when visit.
    	// example:
    	//
    	// "user" => http://localhost:9033/admin/info/user
    	//
    	adminPlugin.AddGenerator("user", datamodel.GetUserTable)

	_ = eng.AddConfig(cfg).AddPlugins(adminPlugin).Use(r)

	_ = r.Run(":9033")
}
```

 
 


More Examples: [https://github.com/chenhg5/go-admin/tree/master/examples](https://github.com/chenhg5/go-admin/tree/master/examples)

### Step 3: run

```shell
GO111MODULE=on go run main.go
```

## Powered by

- [adminlte](https://adminlte.io/themes/AdminLTE/index2.html)

## Contribution

very welcome to pr

 here to join into the develop team 

[join slack](https://app.slack.com/client/T029RQSE6/CME0MBX38/thread/C3MSAFD40-1565569187.323500)

## Special thanks

inspired by [laravel-admin](https://github.com/z-song/laravel-admin)

## Buy me a coffee

leave your github account name and we will put it on the [donation list](DONATION.md).

 


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)