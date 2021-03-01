[![Build Status](https://secure.travis-ci.org/progit/progit.png?branch=master)](https://travis-ci.org/progit/progit)

# Pro Git Book Contents

This is the source code for the Pro Git book contents.  It is licensed under
the Creative Commons Attribution-Non Commercial-Share Alike 3.0 license.  I
hope you enjoy it, I hope it helps you learn Git, and I hope you'll support
Apress and me by purchasing a print copy of the book at Amazon:

http://tinyurl.com/amazonprogit

It is also available online at:

http://git-scm.com/book/

and fully translated in 10 languages.

# Making Ebooks

On Fedora (16 and later) you can run something like this::

    $ yum install ruby calibre rubygems ruby-devel rubygem-ruby-debug rubygem-rdiscount
    $ makeebooks en  # will produce a mobi

On MacOS you can do like this::
	
1. INSTALL ruby and rubygems
2. `$ gem install rdiscount`
3. DOWNLOAD Calibre for MacOS and install command line tools
4. `$ makeebooks zh` #will produce a mobi

# Errata

If you see anything that is technically wrong or otherwise in need of
correction, please [open an issue](https://github.com/progit/progit/issues/new) and one of the maintainers will take a look.


# Translation

If you wish to translate the book, your work will be put up on the 
git-scm.com site.  Please put your translation into the appropriate
subdirectory of this project, using the 
[ISO 639](http://en.wikipedia.org/wiki/List_of_ISO_639-1_codes) 
and send a pull request.

# Sending a pull request

* Be careful to use UTF-8 encoding in your files.
* Do not mix changes to the original english with translations in a single pull request.
* If your pull request changes a translation, prefix your pull request and commits'messages with the ISO 639 code, e.g. `[de] Update chapter 2`.
* Make sure the translation changes can be automatically merged. The maintainers can not make the merge manually if there are some conflicts.
* Make as sure as possible that the changes work correctly for publishing to pdf, ebooks and the git-scm.com website

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)