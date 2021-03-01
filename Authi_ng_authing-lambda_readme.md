# authing-lambda

Using Authing in AWS Lambda.

[Live Demo](https://sample.authing.cn/aws)

## Deploy lambda

### Install serverless

``` shell
$ npm install serverless -g
```

## Test Lambda

* `cd serverless-authorizer`
* `serverless deploy`
* Notice the displayed endpoint after deployment
* `curl --header "Authorization: allow"  ` - Should work! Authorized!
* `curl --header "Authorization: deny"  ` - Should not work
* `curl --header "Authorization: unauthorized"  ` - Should not work
* `curl --header "Authorization: blabla"  ` - Should not work
* `curl  ` - Should not work

## Run front-end

``` shell
$ npm install
$ npm run serve
```

## Build front-end

``` shell
$ npm install
$ npm run build
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)