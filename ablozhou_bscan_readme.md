# BScan
a python3 tool which scan files and paths for a web backend.

# install
```
pip install -r requirements.txt

```

# useage
```
   python bscan.py [options] -h host[:port]
        host: the target host to scan
        port: the port of the web. default is 80.
        options:
            -s seconds: timeout seconds. default is 5 sec.
            -t threads: threads count. default is 20.
            -o ofile, --output=ofile: output log file
            -l lang: program language of the web server. default is all. 
                new language must set in the conf directory.
            --help: print this message.
        example:
            python biscan.py -l php -l java -h 192.168.2.3

```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)