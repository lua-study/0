php7 Nightly Builds
================================

Build your own php7 Nightly Builds Docker container based on an Ubuntu Trusty every day.

To build run either:
```
docker build -t zend/php:7.0 .
```
from within the cloned directory (please note the trailing dot).

Or: make build.sh executable and run it.

After a successful build, a container can be ran by the following command:
```
docker run -d -P zend/php:7.0
```
If you have built the container with the build.sh script, please note, that a date string has been attached to the version number. Please call 'docker ps' to see the full name of the created container).

The command above exposes port 80 of the container, so that a request to http://  will be responded by the Apache 

You can check the IP adress and the Apache logs by calling
```
docker logs -f  
```

PHP application
---
The Apache is configured to serve files located in directory /www/public . By default an index.php and a phpinfo.php has been placed into /www/public resp. /www .

If you want to build the container with your own application sources, please copy the files to the ./www directory on the host system or modify the Dockerfile accordingly.

You get more flexibility by mounting a directory from the host system to the container durin runtime. See the following example:
```
docker run -d -v /home/jan/workspaces/zf2-helloworld:/www zend/php:7.0
```
This command will start a container with a ZF2-Helloworld application - located on the host system in /home/jan/workspaces/zf2-helloworld. The files have been mounted in the container to the /www directory.

Thanks to this, you can now modify the application code with your preferred IDE on the host system and you see the effect immediately in the Docker container.

Running PHP CLI
---
To use the CLI, just launch the container with a shell, e.g. `/bin/bash` using
the interactive (`-i`) and allocate a psuedo-TTY (`-t`):

```
docker run -it zend/php:7.0 /bin/bash
```

At this point you will be a bash prompt inside the container:

```
root@25fbe3b15212:/# php -v
PHP 7.0.0-dev (cli) (built: Jul  9 2015 19:10:39)
Copyright (c) 1997-2015 The PHP Group
Zend Engine v3.0.0-dev, Copyright (c) 1998-2015 Zend Technologies
root@25fbe3b15212:/#
```

To share code, you can use a volume, or `-v`:

```
docker run -it -v /destination:/host/path zend/php:7.0 /bin/bash
```

This will mount the path `/host/path` from the host, to `/destination` inside
the container.

Troubleshooting
---
If you encouter some issues with downloading files from archive.ubuntu.com during the built, please check the file /etc/default/docker and make sure that the directive DOCKER_OPTS is not commented. Obviously Docker has some problems in DNS resultion in specific versions. In DOCKER_OPTS one can specify multiple dns servers which are then used during the build. Please make sure that the docker service is being restarted so that changes can take effect.


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)