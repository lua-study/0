# ASCIIFlow Infinity

## Dockerized Setup

The easiest way to get AsciiFlow running locally is with a recent version of Docker.

```
make
```

Then open your browser to the url that it outputs.

## Manual Setup

Compile the JavaScript (requires Java):

```powershell
asciiflow2> compile.bat
```
windows 

```
~/asciiflow2> ./compile.sh
```

If you get a permissions error:
~/asciiflow2$ chmod a+x closure-compiler.jar

### Run a simple web server in Python 3:


```python
~/asciiflow2$ python -m http.server
```

Goto: http://localhost:8000/index.html

When developing, use the Google JS linter, gjslint.


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)