# composer

国内互联网某种神秘的力量让Composer变得越来越不稳定。 如果此种情况已经严重影响您的心情，请尝试在您的composer.json添加以下代码

``` js
{
    "repositories": [
        {   
            "packagist": false
        },  
        {   
            "type": "composer", 
            "url": "https://packagist.phpcomposer.com"
        }   
    ]
}
```
通过下面的命令，您可以观察速度提升的效果
```
$ composer update -vvv
```
但是Composer我也安装不了啊喂～

我们为composer installer也做了镜像，您可以尝试：

```
$ curl -sS https://github.com/52fhy/composer/raw/master/bin/installer | php
```
如果没有安装curl，尝试以下命令（PHP你总得装吧喂～）

```
$ php -r "readfile('https://github.com/52fhy/composer/raw/master/bin/installer');" | php
```

当然，如果您不需要检查运行环境，也可以直接下载（一般来说直接下载就可以用）:

https://github.com/52fhy/composer/raw/master/bin/Composer-Setup.exe  
https://github.com/52fhy/composer/raw/master/bin/composer.phar  

官网地址：
https://getcomposer.org/Composer-Setup.exe  
https://getcomposer.org/composer.phar  

或者
http://pan.baidu.com/s/1gfmSIbD 密码: f4vr

安装完毕，可以查看命令帮助：
``` shell
$ composer
   ______
  / ____/___  ____ ___  ____  ____  ________  _____
 / /   / __ \/ __ `__ \/ __ \/ __ \/ ___/ _ \/ ___/
/ /___/ /_/ / / / / / / /_/ / /_/ (__  )  __/ /
\____/\____/_/ /_/ /_/ .___/\____/____/\___/_/
                    /_/
Composer version 1.2.0 2016-07-19 01:28:52

Usage:
  command [options] [arguments]

Options:
  -h, --help                     Display this help message
  -q, --quiet                    Do not output any message
  -V, --version                  Display this application version
      --ansi                     Force ANSI output
      --no-ansi                  Disable ANSI output
  -n, --no-interaction           Do not ask any interactive question
      --profile                  Display timing and memory usage information
      --no-plugins               Whether to disable plugins.
  -d, --working-dir=WORKING-DIR  If specified, use the given directory as working directory.
  -v|vv|vvv, --verbose           Increase the verbosity of messages: 1 for normal output, 2 for more verbose output and 3 for debug

Available commands:
  about           Short information about Composer
  archive         Create an archive of this composer package
  browse          Opens the package's repository URL or homepage in your browser.
  clear-cache     Clears composer's internal package cache.
  clearcache      Clears composer's internal package cache.
  config          Set config options
  create-project  Create new project from a package into given directory.
  depends         Shows which packages cause the given package to be installed
  diagnose        Diagnoses the system to identify common errors.
  dump-autoload   Dumps the autoloader
  dumpautoload    Dumps the autoloader
  exec            Execute a vendored binary/script
  global          Allows running commands in the global composer dir ($COMPOSER_HOME).
  help            Displays help for a command
  home            Opens the package's repository URL or homepage in your browser.
  info            Show information about packages
  init            Creates a basic composer.json file in current directory.
  install         Installs the project dependencies from the composer.lock file if present, or falls back on the composer.json.
  licenses        Show information about licenses of dependencies
  list            Lists commands
  outdated        Shows a list of installed packages that have updates available, including their latest version.
  prohibits       Shows which packages prevent the given package from being installed
  remove          Removes a package from the require or require-dev
  require         Adds required packages to your composer.json and installs them
  run-script      Run the scripts defined in composer.json.
  search          Search for packages
  self-update     Updates composer.phar to the latest version.
  selfupdate      Updates composer.phar to the latest version.
  show            Show information about packages
  status          Show a list of locally modified packages
  suggests        Show package suggestions
  update          Updates your dependencies to the latest version according to composer.json, and updates the composer.lock file.
  validate        Validates a composer.json and composer.lock
  why             Shows which packages cause the given package to be installed
  why-not         Shows which packages prevent the given package from being installed

```

文档：http://www.cnblogs.com/52fhy/p/5246013.html  
Composer：https://getcomposer.org/  
Composer Doc：https://getcomposer.org/doc  
Composer 中文网：http://www.phpcomposer.com/  
Packagist：https://packagist.org/  

Composer快速入门 - icyfire - SegmentFault
https://segmentfault.com/a/1190000005624202  

Composer进阶使用 —— 常用命令和版本约束 - icyfire - SegmentFault
https://segmentfault.com/a/1190000005898222  




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)