# php screw plus  

github https://github.com/del-xiong/screw-plus  
oschina http://git.oschina.net/splot/php-screw-plus  

详细配置教程 http://www.jianshu.com/p/f6425e2f8643 (使用screw plus来保护php代码安全)

**交流QQ群 530887505**  

### 简述
- 2016/08/13更新:给screw增加批量解密功能
- 2016/06/27更新:增加了STRICT_MODE,如果只允许服务器执行加过密的php文件,设置php_screw_plus.h STRICT_MODE为1(set STRICT_MODE to 1 if you only want the crypted php files to be executed),此举可防止黑客或其他人执行任意php文件。  
- 2016/06/24更新:改进了加密算法 使用高强度的AES256 CBC模式进行加密  


基于php screw  
主要做了以下改进：  
 **增加了批量加密 更加方便**  
 **原生加密算法太弱易被破解,升级了加密算法，更加安全可靠**  
加密的优点：  
 **可防止源码泄露，本程序是php扩展加密运行，只能在vps上运行，由于需要扩展进行动态解密，加密后被别人全部下载也无法被破解**  
 **商业源码可加密核心功能，只开放接口给客户**  
 **部分公司需要团队开发的，可防止源码泄露**  
 **其他。。。我编不出来了**  
### 效果演示  
原生代码:  
```
 cケ:嬺郠椦TＹ魷	FJ??觺杠B`9€X]┚呿4?k娤?豯v?9??\螐廱鲟`漬\F?#假
?S阮??8邂璟襹B跷沯僯{￢UI憤
```
### 使用方法：  
1. 下载本程序并解压到某个目录
2. 在screw plus目录中执行php bin中的phpize自动生成扩展所需文件（如果你的php里没有可以去官网下载）
3. 执行./configure --with-php=config=[php config path] 进行配置，[php config path]是你的php-config的绝对路径
4. 修改php_screw_plus.h中的CAKEY，改为一个你认为安全的字符串
5. 执行make生成扩展 modules/php_screw_plus.so
6. 把扩展路径加入php.ini中 重启php
7. 进入tools文件夹 执行make
8. 执行./screw [目录或文件] ，后面带上你要加密的目录或文件即可自动开始加密

执行./screw [path] 是加密 后面加-d参数则是解密 例如
```
./screw /home/web/ -d
```
表示解密web目录的所有php文件

现在可以访问php文件，如果前面没有发生错误，应该可以正常执行了。

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)