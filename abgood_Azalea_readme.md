# Azalea #


 
	 
		 linux 
		 windows 
		 coverity 
		 cmake 
	 
	 
		 
			 
				 
			 
		 
		 
			 
				 
			 
		 
		 
			 
				 
			 
		 
		 
			 
				 
			 2.8
		 
	 
 


a chatting server

# design #

![design](https://rawgithub.com/duguying/Azalea/master/docs/design.svg)

# core #
![core](https://rawgithub.com/duguying/Azalea/master/docs/core.svg)

# build #

**linux**

```shell
mkdir build
cd build
cmake ..
make
```

**windows (MSVC 9+ build)**

```shell
mkdir build
cd build
cmake -G"NMake Makefiles" ..
nmake
```

# let's have a try #

start Azalea server in 1st terminal
>
```shell
./ichat
```

connect the server from the tcper in 2nd terminal
>
```shell
./bin/tcper
$lijun
```

open another connection in 3rd terminal
>
```shell
./tcper
$rex
*lijun
hello, this is a message send to lijun from rex
```

and then, the 2nd terminal will received the message `hello, this is a message send to lijun from rex`.

:smile:



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)