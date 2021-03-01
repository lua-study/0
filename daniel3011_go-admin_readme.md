 
   
     
   
 

 
    the missing golang data admin panel builder tool.
 

 
     Documentation  | 
     中文介绍  |
     DEMO  |
     中文DEMO  |
     Forum 
 

 
     
     
     
     
     
     
     
  

 
    Inspired by  laravel-admin 
 

## Preface

GoAdmin is a toolkit to help you build a data visualization admin panel for your golang app.

Online demo: [https://demo.go-admin.com](https://demo.go-admin.com)

Quick follow up example: [https://github.com/GoAdminGroup/example](https://github.com/GoAdminGroup/example)

GoAdmin+vue example: [https://github.com/GoAdminGroup/goadmin-vue-example](https://github.com/GoAdminGroup/goadmin-vue-example)

![interface](http://file.go-admin.cn/introduction/interface_en_3.png)

## Features

- 🚀 **Fast**: build a production admin panel app in **ten** minutes.
- 🎨 **Theming**: beautiful ui themes supported(default adminlte, more themes are coming.)
- 🔢 **Plugins**: many plugins to use(more useful and powerful plugins are coming.)
- ✅ **Rbac**: out of box rbac auth system.
- ⚙️ **Frameworks**: support most of the go web frameworks.

## Translation
We need your help: [https://github.com/GoAdminGroup/docs/issues/1](https://github.com/GoAdminGroup/docs/issues/1)

## Who is using

[Comment the issue to tell us](https://github.com/GoAdminGroup/go-admin/issues/71).

## How to

Following three steps to run it.

### Step 1: import sql

- [mysql](https://raw.githubusercontent.com/GoAdminGroup/go-admin/master/data/admin.sql)
- [mssql](https://raw.githubusercontent.com/GoAdminGroup/go-admin/master/data/admin.mssql)
- [postgresql](https://raw.githubusercontent.com/GoAdminGroup/go-admin/master/data/admin.pgsql)
- [sqlite](https://raw.githubusercontent.com/GoAdminGroup/go-admin/master/data/admin.db)

### Step 2: create main.go

  main.go 
 

```go
package main

import (
	"github.com/gin-gonic/gin"
	_ "github.com/GoAdminGroup/go-admin/adapter/gin"
	_ "github.com/GoAdminGroup/go-admin/modules/db/drivers/mysql"
	"github.com/GoAdminGroup/go-admin/engine"
	"github.com/GoAdminGroup/go-admin/plugins/admin"
	"github.com/GoAdminGroup/go-admin/modules/config"
	"github.com/GoAdminGroup/themes/adminlte"
	"github.com/GoAdminGroup/go-admin/template"
	"github.com/GoAdminGroup/go-admin/template/chartjs"
	"github.com/GoAdminGroup/go-admin/template/types"
	"github.com/GoAdminGroup/go-admin/examples/datamodel"
	"github.com/GoAdminGroup/go-admin/modules/language"
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
				Name:         "goadmin",
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
		ColorScheme: adminlte.ColorschemeSkinBlack,
	}

	// add component chartjs
	template.AddComp(chartjs.NewChart())

	_ = eng.AddConfig(cfg).
		AddGenerators(datamodel.Generators).
	        // add generator, first parameter is the url prefix of table when visit.
    	        // example:
    	        //
    	        // "user" => http://localhost:9033/admin/info/user
    	        //		
		AddGenerator("user", datamodel.GetUserTable).
		Use(r)
	
	// customize your pages
	eng.HTML("GET", "/admin", datamodel.GetContent)

	_ = r.Run(":9033")
}
```

 
 

More framework examples: [https://github.com/GoAdminGroup/go-admin/tree/master/examples](https://github.com/GoAdminGroup/go-admin/tree/master/examples)

### Step 3: run

```shell
GO111MODULE=on go run main.go
```

visit: [http://localhost:9033/admin](http://localhost:9033/admin)

account: admin password: admin

[A super simple example here](https://github.com/GoAdminGroup/example)

See the [docs](https://book.go-admin.cn) for more details.

## Backers

 Your support will help me do better! [[Become a backer](https://opencollective.com/go-admin#backer)]
    

## Contribution

[here for contribution guide](CONTRIBUTING.md)

 here to join into the develop team 

[join telegram](https://t.me/joinchat/NlyH6Bch2QARZkArithKvg)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)