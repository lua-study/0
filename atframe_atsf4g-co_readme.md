# atsf4g-co
service framework for game server using libatbus, libatapp, libcopp and etc.


# Dependency
1. [libuv](http://libuv.org/)  -- libuv is a multi-platform support library with a focus on asynchronous I/O.
2. [msgpack-c](https://github.com/msgpack/msgpack-c)  -- [MessagePack](http://msgpack.org/) is an efficient binary serialization format, and [msgpack-c](https://github.com/msgpack/msgpack-c) is a c and c++ driver for it.
3. [libiniloader](https://github.com/owt5008137/libiniloader) -- a small and lightweight ini loader code.
4. [libcurl](https://curl.haxx.se/libcurl/) -- libcurl is a free and easy-to-use client-side URL transfer library
5. [libcopp](https://github.com/owt5008137/libcopp) -- Cross-platform coroutine library written in c++.
6. [rapidjson](https://github.com/miloyip/rapidjson) -- A fast and header only json library.
7. [flatbuffer](https://github.com/google/flatbuffers) -- A simple pack/unpack library. It's used in atgateway's inner protocol.


# Prepare
1. Install [etcd](https://github.com/coreos/etcd). (It's used for atproxy to connect to each other.)
2. *[opional]* Install [redis](http://redis.io/). (DB services.install it if used)


# Extern Dependency
1. libuuid-devel(uuid-dev)
2. *[opional]* hiredis, redis (if using redis, full_sample branch has use redis)


# Developer

## Tools
1. [cmake](https://cmake.org) 3.4 and above 
2. gcc/clang/msvc
3. gdb/lldb/windb
4. git
5. unzip
6. tar
7. autoconf
8. automake
9. p7zip
10. etc.

## Framework Code Tree

+ 3rd_party: all dependency 3rd_party libraries
+ atframework: atframework projects and libraries
> * export: exported libraries, used by client
> * libatframe_utils: framework utility codes
> * libatbus: communication library used between servers
> * libatapp: server application framework, used to build a specified server type
> * services: inner services of atframework
>> 1. component: inner services common codes
>> 2. atproxy: proxy server, used to connect difference service group to each other
>> 3. atgateway: gateway server, used to manage client connections

+ doc: documents
+ install: all resources and configure templates
+ project: project script, used to detect build environment and generate build scripts
+ sample: sample codes to show usage of some libraries
+ src: all real projects
> * echosvr: the simplest server instance, just send back all data receive from client
> * [others]: other services

## Logic Code Tree

+ src: all real projects
> * server_frame: server common library
>> 1. config: server configure defines and excel configure data structures
>> 2. data: game data layer
>> 3. dispatcher: decide how to deal with each type of messages and manage coroutine tasks
>> 4. logic: game logic layer
>> 5. rpc: all remote procedure call APIs, include server to server message, DB message and so on
>> 6. utility: all shared utility codes

> * tools: tool projects


## Basic Usage

### Windows
You need to prebuilt all dependency libraries such as openssl/mbedtls, libcurl, libuv and so on.
Then run
``` 
cmake [SOURCE PATH] -G "Visual Studio ... Win64" -DLIBUV_ROOT=[LIBUV INSTALL PATH] -DOPENSSL_ROOT=[OPENSSL INSTALL PATH] ...
```  
Please see [3rd_party](3rd_party) to see which libraries is required.

### Unix like system
```bash
sh cmake_dev.sh [options] ...
```
Such as sh cmake_dev.sh -su to enable all unit test and samples, or sh cmake_dev.sh -a to use clang-analysis.
You can also directly run cmake [SOURCE PATH] [options...] just like in windows, use your own prebuilt libraries or not.
It depends to you.

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)