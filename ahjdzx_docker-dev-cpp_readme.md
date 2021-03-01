# Init

```bash
git clone git@gitee.com:ahjdzx/docker-dev-cpp.git
cd docker-dev-cpp
prjHome=`pwd`
cppVer=latest
centosVer=7
```

## Build pkg

```bash
docker run -i -t -v $prjHome/:/build --name=build-centos-${centosVer} ahjdzx/centos:${centosVer} /bin/bash
/build/script/build_pkg.sh
```

## Build image

```bash
docker build -t ahjdzx/dev-cpp:${cppVer} ./
```

# Run container

```bash
docker run -d --name=dev-cpp-${cppVer} --volumes-from=data-home --net=host ahjdzx/dev-cpp:${cppVer}
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)