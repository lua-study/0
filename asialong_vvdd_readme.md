# VVDD (vagrant + virtualbox + docker + development)

author：william

## 一、准备
```
1、安装virtualbox ,官网https://www.virtualbox.org/
2、安装vagrant ,官网https://www.vagrantup.com/
3、git clone https://github.com/asialong/vvdd.git
```

## 二、安装环境
```
1、vagrant up
> 以下几点可选
2、vagrant ssh
    切换到root用户
    cd ~
    mkdir .ssh
    cd .ssh
    touch authorized_keys
    ssh-keygen -t rsa
    cat id_rsa.pub >> authorized_keys
    复制id_rsa的内容
```
        修改/etc/ssh/sshd_config
        PermitRootLogin yes
        PasswordAuthentication yes
        PubkeyAuthentication yes
        systemctl restart sshd.service
    退出虚拟机
    在当前目录新建id_rsa，粘贴刚才的内容，保存
```
3、将Vagrantfile打开并将以下两行的#去掉，保存
    #config.ssh.username = "root"
    #config.ssh.private_key_path = "./id_rsa"
4、vagrant reload
5、vagrant ssh 输入密码：vagrant 后回车进入
```
## 三、按需安装容器
### 使用composer
**我们建议在主机HOST中使用composer，避免PHP容器变得庞大**。
1. 在主机创建一个目录，用以保存composer的配置和缓存文件：
    ```
    mkdir ~/composer
    ```
2. 打开主机的 `~/.bashrc` 或者 `~/.zshrc` 文件，加上：
    ```
    composer () {
        tty=
        tty -s && tty=--tty
        docker run \
            $tty \
            --interactive \
            --rm \
            --user $(id -u):$(id -g) \
            --volume ~/composer:/tmp \
            --volume /etc/passwd:/etc/passwd:ro \
            --volume /etc/group:/etc/group:ro \
            --volume $(pwd):/app \
            composer "$@"
    }

    ```
3. 让文件起效：
    ```
    source ~/.bashrc
    ```
4. 开启容器
    ```
    cd /www
    cp docker-compose-sample.yml docker-compose.yml
    cp env.sample .env
    docker-compose up -d
    ```
5. （可选）如果提示需要依赖，用`--ignore-platform-reqs --no-scripts`关闭依赖检测。
6. （可选）第一次使用 composer 会在 ~/composer 目录下生成一个config.json文件，可以在这个文件中指定国内仓库，例如：
    ```
    {
        "config": {},
        "repositories": {
            "packagist": {
                "type": "composer",
                "url": "https://mirrors.aliyun.com/composer/"
            }
        }
    }

    ```
	或者
	```
	composer config -g repo.packagist composer https://mirrors.aliyun.com/composer/
	```
7. 如果navicat工具连不上mysql,进入mysql容器：
	```
	use mysql;
	select user,host,plugin from user;
	ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '123456';
	update user set host='%' where user='root';
	GRANT ALL PRIVILEGES ON *.* TO 'root'@'%';
	select user,host,plugin from user;
	flush privileges;
    ```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)