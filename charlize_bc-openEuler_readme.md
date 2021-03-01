# bc RPM package for openEuler
    
[bc](https://www.gnu.org/software/bc/) is an arbitrary precision numeric processing language. Syntax is similar to C, but differs in many substantial areas. It supports interactive execution of statements.

# Build Package
 
To build a RPM package, create packaging scaffold with `rpmdev-setuptree`
if it doesn't exist.
Then copy bc-1.07.1.tar.gz ([upstream URL](http://ftp.gnu.org/gnu/bc/bc-1.07.1.tar.gz))
to ~/rpmbuild/SOURCES, bc.spec to ~/rpmbuild/SPECS, and run:
```
rpmlint bc.spec
rpmbuild -bs bc.spec
rpmbuild -bb bc.spec
```

To be verified on openEuler 20.03 (LTS).



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)