# 讯飞语音JavaWeb语音合成解决方案

O(∩_∩)O哈哈~ 自己脑抽了 xufei_msc拼错了，兄弟们 1核 1G的云服务器 经不住折腾啊，CPU爆表，服务又挂了。

## 在线语音合成
将文字信息转化为声音信息，给应用配上“嘴巴”。我们提供了众多极具特色的发音人（音库）供您选择。其合成音在音色、自然度等方面的表现均接近甚至超过了人声。这种语音合成体验，达到了真正可商用的标准

讯飞的语音合成还是很牛P的，不但有基础发音人，还有精品发音人、特色发音人、明星发音人，当然你如果有特殊要求还可以定制。

这里我们选择基础发音人做简单的JavaWeb集成测试，因为其他选项还要申请，想想还是算了，等流程走通再说。

## 平台环境
JDK1.7、Tomcat8、Eclipse、讯飞JDK、win+[ffmpeg](https://ffmpeg.zeranoe.com/builds/ "ffmpeg")(测试)、Linux+Docker+[ffmpeg](https://ffmpeg.org/download.html#release_3.4 "ffmpeg")(生产)

说明：讲真，Win平台下ffmpeg安装使用还是很轻松的，直接下载压缩包免安装，JAVA直接调用执行命令即可。Linux下各种依赖编译能把你的小机器跑死，并且还各种编译错误，然后就果断使用了Docker，唯一头疼的是，这个环境真干净，各种命令不支持，当然这也是Docker的优点。

## 流程图

![输入图片说明](https://gitee.com/uploads/images/2018/0306/111728_8384fd0a_87650.png "讯飞语音合成.png")

## Web集成

讯飞为我们提供了简单的SDK，[科大讯飞MSC开发指南-Java](https://www.kancloud.cn/iflytek_sdk/msc_java/299245 "科大讯飞MSC开发指南-Java")。当然，前提你要有一个讯飞的账号，注册、创建应用什么的这里就不赘述了，只要最后能获取到一个APP_ID就可以。



### Win+ffmpeg(测试)

- 讯飞语音合成需要动态链接库支持，根据自己的系统把msc64.dll或者msc32.dll放到指定的目录，可以使用System.getProperty("java.library.path")查看，放置到任意目录即可。

- 根据自己的系统下载对应的[ffmpeg](https://ffmpeg.zeranoe.com/builds/ "ffmpeg")，解压即可，直接调用bin目录下的ffmpeg.exe即可。- 

### Linux+Docker+ffmpeg(生产)

#### 获取ffmpeg镜像
```
docker pull jrottenberg/ffmpeg
```
#### 创建并运行容器
```
docker run -it --name app_ffmpeg -p 8080:8080 -v /home/app_ffmpeg/:/mnt/app/  --entrypoint='bash' jrottenberg/ffmpeg
```
注意：Docker容器中，各种yum、wget以及vim是不存在的，所以大都数配置通过宿机获取然后同步复制到容器中。

#### 安装配置JDK

甲骨文给弄的必须认证下载了，这里我们自行下载并手动上传到/home/app_ffmpeg目录下。

```
# 复制配置文件到宿机
docker cp 4f131c866092:/etc/profile  /home/app_ffmpeg/
```
编辑profile，追加以下配置
```
#set java environment
JAVA_HOME=/mnt/app/jdk1.7.0_80
JRE_HOME=/mnt/app/jdk1.7.0_80/jre
CLASS_PATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar:$JRE_HOME/lib
PATH=$PATH:$JAVA_HOME/bin:$JRE_HOME/bin
export JAVA_HOME JRE_HOME CLASS_PATH PATH
```
```
# 复制配置文件到容器
docker cp /home/app_ffmpeg/profile 4f131c866092:/etc/
```

进入容器，生效配置
```
# 进入容器
docker exec -it app_ffmpeg  bash
# 使配置生效
source /etc/profile
# 检查JDK是否安装成功
java -version
```

#### 安装配置Tomcat

如果tomcat启动卡主不动

找到jdk1.x.x_xx/jre/lib/security/java.security文件，在文件中找到securerandom.source这个设置项，将其改为：
```
securerandom.source=file:/dev/./urandom
```

如果tomcat输出中文乱码
```
locale
locale -a
LANG=C.UTF-8  (有的是zh_CN.UTF-8，不过我在本地没发现这种编码)
source /etc/profile
```

#### 配置讯飞动态库
根据自己的系统版本，分别把libmsc32.so 或者 libmsc64.so 上传到/lib/ 和 /lib64/ 目录。


## 演示地址

http://xunfei.52itstyle.com/xufei_msc/ (兄弟们 1核 1G的云服务器 经不住折腾啊，CPU爆表，服务又挂了。)


![输入图片说明](https://gitee.com/uploads/images/2018/0306/145954_5096e26b_87650.png "123_2.png")

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)