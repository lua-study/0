hi,

This project is fork from [branch](https://github.com/NetEaseGame/ATX) ,I customized specifically for my rom.

**I do not recommend you to use this project.**

But if you want to know how to customize `UI test for android` ,I may be able to provide some help.

This branch is doc-less. For help , check my [blog](http://blog.csdn.net/yeshennet) or send an email to me `me@yeshen.org` .

This project used `adb shell input` to handle all input event,base in [atx](https://github.com/NetEaseGame/ATX) , but delete ios&&window part of that project.

To be better perform in my rom. 
- Less CPU&IO in my control machine.
- More robust in terms of input.
- More suitable for my system.

### start

```bash
# pip install virtualenv
virtualenv venv && . venv/bin/activate

pip install aircv==1.4.5&& pip install appnope==0.1.0 \
&& pip install AxmlParserPY==0.0.2&& pip install backports-abc==0.5 \
&& pip install backports.shutil-get-terminal-size==1.0.0 \
&& pip install bottle==0.12.13&& pip install certifi==2017.7.27.1 \
&& pip install chardet==3.0.4&& pip install colorama==0.3.7 \
&& pip install decorator==4.1.2&& pip install enum34==1.1.6 \
&& pip install facebook-wda==0.1.1.dev1&& pip install fire==0.1.2 \
&& pip install futures==3.0.5&& pip install geeteventbus==1.0 \
&& pip install humanize==0.5.1&& pip install idna==2.6 \
&& pip install imageio==1.5&& pip install ipython==5.5.0 \
&& pip install ipython-genutils==0.2.0&& pip install maproxy==0.0.12 \
&& pip install numpy==1.13.1&& pip install olefile==0.44 \
&& pip install opencv-contrib-python==3.3.0.10 \
&& pip install pathlib2==2.3.0&& pip install pexpect==4.2.1 \
&& pip install pickleshare==0.7.4&& pip install Pillow==4.2.1 \
&& pip install progress==1.3&& pip install prompt-toolkit==1.0.15 \
&& pip install protobuf==3.4.0&& pip install ptyprocess==0.5.2 \
&& pip install pyasn1==0.3.5&& pip install pycrypto==2.6.1 \
&& pip install Pygments==2.2.0&& pip install PyYAML==3.11 \
&& pip install requests==2.18.4&& pip install rsa==3.4.2 \
&& pip install scandir==1.5&& pip install setuptools==36.5.0 \
&& pip install simplegeneric==0.8.1&& pip install singledispatch==3.4.0.3 \
&& pip install six==1.11.0&& pip install subprocess32==3.2.7 \
&& pip install tornado==4.5.2&& pip install tqdm==4.5.0 \
&& pip install traitlets==4.3.2&& pip install urllib3==1.22 \
&& pip install wcwidth==0.1.7&& pip install wheel==0.30.0)
```

```bash
# attach phone via usb or http(adb connect ip)
python -m atx gui
```

### API

```python
import atx
d=atx.connect()
d.attach(package=None, activity=None, resource_path=None, instance=None, display_id=None, identity=None)

d.swipe(startx,starty,endx,endy)
d.type(u"文字") 
d.clear_type() 
d.click(x,y,delay) 
d.tap(x,y,delay)

d.try_tap_image(key=None, local_object_path=None, timeout=0.6, frequency=0.3, delay=0) 
d.tap_image() 
d.exists(key=None, local_object_path=None, delay=0)
d.wait_image(key=None)
d.try_tap_text(text="", timeout=0.6, frequency=0.3, delay=0, full_match=True)
d.tap_text(text="", timeout=15, frequency=0.3, delay=0, full_match=True)
d.find_text(text="")
d.exists_text(text="")
d.stop()
d.back()
d.double_back()
d.home()
d.current_activity()
d.assert_activity(activity, delay=2)
d.current_app()
d.current_instance()
d.exists_id(identity)
d.exists_cover()
d.top_window_count()
d.su(["pm","list"])
d.throw(error="message")
d.info("message")

```

```python
@report(level=consts.LEVEL_DEFAULT)
def template(d, ctx):
    pass
```

- LEVEL_NONE 
- LEVEL_DEFAULT 
- LEVEL_HTML 

[wiki](https://github.com/wuyisheng/ATX/wiki/API)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)