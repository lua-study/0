# xsel RPM package for openEuler
    
[xsel](https://github.com/kfish/xsel) is a tool to manipulate the X selection on Linux/Unix.

# Build Package
 
To build a RPM package, create packaging scaffold with `rpmdev-setuptree`
if it doesn't exist.
Then copy xsel-1.2.0.tar.gz ([upstream URL](http://hisham.hm/htop/releases/2.2.0/htop-2.2.0.tar.gz))
to ~/rpmbuild/SOURCES, xsel.spec to ~/rpmbuild/SPECS, and run:
```
rpmlint xsel.spec
rpmbuild -bs xsel.spec
rpmbuild -bb xsel.spec
```

To be verified on openEuler 20.03 (LTS).



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)