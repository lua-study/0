 
        ____  __  ______     ____  _________   ___________
       / __ \/ / / / __ \   / __ )/ ____/   | / ___/_  __/
      / /_/ / /_/ / /_/ /  / __  / __/ / /| | \__ \ / /
     / ____/ __  / ____/  / /_/ / /___/ ___ |___/ // /
    /_/   /_/ /_/_/      /_____/_____/_/  |_/____//_/

贡献者名字：
@imaben (windows版本提供者)  https://github.com/imaben
@pinguo-niulingyun (PHP7版本提供者) https://github.com/pinguo-niulingyun

QQ交流群：239243332
 

 Windows DLL： 下载地址  

 php-beast可以自定义加密模块，加密模块编写教程:  点击  

 编译安装如下: 
  
$ wget https://github.com/liexusong/php-beast/archive/master.zip
$ unzip master.zip
$ cd php-beast-master
$ phpize
$ ./configure
$ sudo make && make install

编译好之后修改php.ini配置文件, 加入配置项: extension=beast.so, 重启php-fpm
  

 温馨提示: 可以设置较大的缓存提高效率 

  使用php-beast的性能：   
  

  不使用php-beast的性能：   
  

配置项:
  
 beast.cache_size = size
 beast.log_file = "path_to_log"
 beast.log_user = "user"
 beast.log_level = "debug"
 beast.enable = On
  

beast.log_level支持参数：
 
 1. DEBUG
 2. NOTICE
 3. ERROR
 

支持的模块有：
 
 1. AES
 2. DES
 3. Base64
 

通过测试环境:
  
 Nginx + Fastcgi + (PHP-5.2.x ~ PHP-7.1.x)
  

------------------------------

## 怎么加密项目
**加密方案1**

安装完 `php-beast` 后可以使用 `tools` 目录下的 `encode_files.php` 来加密你的项目。使用 `encode_files.php` 之前先修改 `tools` 目录下的 `configure.ini` 文件，如下：
```ini
; source path
src_path = ""

; destination path
dst_path = ""

; expire time
expire = ""

; encrypt type (selection: DES, AES, BASE64)
encrypt_type = "DES"
```
`src_path` 是要加密项目的路径，`dst_path` 是保存加密后项目的路径，`expire` 是设置项目可使用的时间 (`expire` 的格式是：`YYYY-mm-dd HH:ii:ss`)。`encrypt_type`是加密的方式，选择项有：DES、AES、BASE64。
修改完 `configure.ini` 文件后就可以使用命令 `php encode_files.php` 开始加密项目。

**加密方案2**

使用`beast_encode_file()`函数加密文件，函数原型如下： 
`beast_encode_file(string $input_file, string $output_file, int expire_timestamp, int encrypt_type)`。
 
1. $input_file: 要加密的文件
2. $output_file: 输出的加密文件路径
3. $expire_timestamp: 文件过期时间戳
4. $encrypt_type: 加密使用的算法（支持：BEAST_ENCRYPT_TYPE_DES、BEAST_ENCRYPT_TYPE_AES）
 

------------------------------

## 制定自己的php-beast

`php-beast` 有多个地方可以定制的，以下一一列出：

*1.* 使用 `header.c` 文件可以修改 `php-beast` 加密后的文件头结构，这样网上的解密软件就不能认识我们的加密文件，就不能进行解密，增加加密的安全性。

*2.* `php-beast` 提供只能在指定的机器上运行的功能。要使用此功能可以在 `networkcards.c` 文件添加能够运行机器的网卡号，例如：
```c
char *allow_networkcards[] = {
	"fa:16:3e:08:88:01",
    NULL,
};
```
这样设置之后，`php-beast` 扩展就只能在 `fa:16:3e:08:88:01` 这台机器上运行。另外要注意的是，由于有些机器网卡名可能不一样，所以如果你的网卡名不是 `eth0` 的话，可以在 `php.ini` 中添加配置项： `beast.networkcard = "xxx"` 其中 `xxx` 就是你的网卡名，也可以配置多张网卡，如：`beast.networkcard = "eth0,eth1,eth2"`。

*3.* 使用 `php-beast` 时最好不要使用默认的加密key，因为扩展是开源的，如果使用默认加密key的话，很容易被人发现。所以最好编译的时候修改加密的key，`aes模块` 可以在 `aes_algo_handler.c` 文件修改，而 `des模块` 可以在 `des_algo_handler.c` 文件修改。

------------------------------

## 开启debug模式
可以在configure时加入 `--enable-beast-debug` 选项来开启debug模式。开启debug模式后需要在php.ini配置文件中加入配置项：`beast.debug_path` 和 `beast.debug_mode`。`beast.debug_mode` 用于指定是否使用debug模式，而 `beast.debug_path` 用于输出解密后的php脚本源码。这样就可以在 `beast.debug_path` 目录中看到php-beast解密后的源代码，可以方便知道扩展解密是否正确。

------------------------------

## 函数列表
*1.* beast_encode_file(): 用于加密一个文件

*2.* beast_avail_cache(): 获取可以缓存大小

*3.* beast_support_filesize(): 获取beast支持的最大可加密文件大小

*4.* beast_file_expire(): 获取一个文件的过期时间

*5.* beast_clean_cache(): 清空beast的所有缓存(如果有文件更新, 可以使用此函数清空缓存)

------------------------------

## 常见问题

*1.* linux：如果出现502错误，一般是由于GCC版本太低导致，请先升级GCC再安装本模块。

*2.* Windows：IIS环境下FastCGI进程异常退出：尝试将IIS的运行用户从ApplicationPoolIdentity改为LocalSystem

------------------------------

作者: 列旭松(280259971@qq.com)。

 my book:《 PHP核心技术与最佳实践(第二版) 》 此书有详细的PHP扩展编写教程 
## 如果本项目能够帮到你的话请支持一下:
 
支付宝： 
  
 
微信： 
 
 

------------------------------


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)