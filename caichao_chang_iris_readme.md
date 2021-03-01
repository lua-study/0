# News

> This is the under-development branch. Stay tuned for the upcoming release [v12.2.0](HISTORY.md#Next).

![](https://iris-go.com/images/release.png) Iris version **12.1.8** has been [released](HISTORY.md#su-16-february-2020--v1218)!

![](https://iris-go.com/images/cli.png) The official [Iris Command Line Interface](https://github.com/kataras/iris-cli) will soon be near you in 2020!

![](https://iris-go.com/images/sponsor.png) Support your favorite web framework through [Github Sponsors Program](https://github.com/sponsors/kataras)!

# Iris Web Framework                            

[![build status](https://img.shields.io/travis/kataras/iris/master.svg?style=for-the-badge&logo=travis)](https://travis-ci.org/kataras/iris) [![FOSSA Status](https://img.shields.io/badge/LICENSE%20SCAN-PASSING❤️-CD2956?style=for-the-badge&logo=fossa)](https://app.fossa.io/projects/git%2Bgithub.com%2Fkataras%2Firis?ref=badge_shield)   [![view examples](https://img.shields.io/badge/learn%20by-examples-0C8EC5.svg?style=for-the-badge&logo=go)](https://github.com/kataras/iris/tree/master/_examples) [![chat](https://img.shields.io/gitter/room/iris_go/community.svg?color=7E18DD&logo=gitter&style=for-the-badge)](https://gitter.im/iris_go/community)  

    

Iris is a fast, simple yet fully featured and very efficient web framework for Go.

It provides a beautifully expressive and easy to use foundation for your next website or API.

Learn what [others saying about Iris](https://iris-go.com/testimonials/) and **[star](https://github.com/kataras/iris/stargazers)** this open-source project to support its potentials.

[![](https://media.giphy.com/media/j5WLmtvwn98VPrm7li/giphy.gif)](https://iris-go.com/testimonials/)

[![Benchmarks: Apr 2, 2020 at 12:13pm (UTC)](https://iris-go.com/images/benchmarks.svg)](https://github.com/kataras/server-benchmarks)

## 📖 Learning Iris

 
 Quick start 

```sh
# https://github.com/kataras/iris/wiki/Installation
$ go get github.com/kataras/iris/v12@latest
# assume the following code in example.go file
$ cat example.go
```

```go
package main

import "github.com/kataras/iris/v12"

func main() {
    app := iris.New()
    app.Get("/ping", func(ctx iris.Context) {
        ctx.JSON(iris.Map{
            "message": "pong",
        })
    })

    app.Listen(":8080")
}
```

```sh
# run example.go and
# visit http://localhost:8080/ping on browser
$ go run example.go
```

> Routing is powered by [muxie](https://github.com/kataras/muxie), the most powerful and fastest trie-based software written in Go.

 

Iris contains extensive and thorough **[wiki](https://github.com/kataras/iris/wiki)** making it easy to get started with the framework.

 

For a more detailed technical documentation you can head over to our [godocs](https://godoc.org/github.com/kataras/iris). And for executable code you can always visit the [\_examples](_examples/) repository's subdirectory.

### Do you like to read while traveling?

     

[![follow author](https://img.shields.io/twitter/follow/makismaropoulos.svg?style=for-the-badge)](https://twitter.com/intent/follow?screen_name=makismaropoulos)

You can [request](https://bit.ly/iris-req-book) a PDF version and online access of the **E-Book** today and be participated in the development of Iris.

## 🙌 Contributing

We'd love to see your contribution to the Iris Web Framework! For more information about contributing to the Iris project please check the [CONTRIBUTING.md](CONTRIBUTING.md) file.

[List of all Contributors](https://github.com/kataras/iris/graphs/contributors)

## 🛡 Security Vulnerabilities

If you discover a security vulnerability within Iris, please send an e-mail to [iris-go@outlook.com](mailto:iris-go@outlook.com). All security vulnerabilities will be promptly addressed.

## 📝 License

This project is licensed under the [BSD 3-clause license](LICENSE), just like the Go project itself.

The project name "Iris" was inspired by the Greek mythology.
 


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)