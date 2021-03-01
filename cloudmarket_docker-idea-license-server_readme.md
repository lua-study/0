# docker-idea-license-server

idea 激活服务器 docker 版本

## Build image locally

```bash
docker build -t yyjazsf/jetbrains-license-server:1.6 .
```

## Run

### link

```bash
# http://[your IP]:/7788
```

### Run with default user name: `yyj`

```bash
docker run -d --rm --name="idea-license" -p 7788:1017 yyjazsf/jetbrains-license-server:1.6
```

### Run with custom user name

```bash
docker run -d --rm --name="idea-license" -p 1017:1017 -u "[YOUR NAME]" yyjazsf/jetbrains-license-server:1.6
```

### Run with custom user name and port

```bash
docker run -d --rm --name="ansonliao" -p [YOUR PORT]:1017 -u "[YOUR NAME]" yyjazsf/jetbrains-license-server:1.6
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)