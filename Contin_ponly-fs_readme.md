# Ponly-FS (Ponly-FileSystem)
***
[TOC]
## 概述
	Ponly FS 提供一个对常见文件系统(本地文件系统/FTP/SFTP/OSS)统一访问的 API 接口,其核心接口只有一个 FileSystem 接口定义
## 快速入门
	这里提供个简单的例子, 创建一个文件并读取信息
```
// 创建一个从 ftp 读取文件的文件系统 uri
// String ftpUri = "ftp://user:password@host";

// 创建一个基于本地文件系统, 以 d:/fs 为根目录的文件系统
String fsUri = "local:///d:/fs/";
FileSystem fs = FileSystems.getFileSystem(fsUri);

// 在该文件系统中创建一个 dir/hello.txt, 如果存在则覆盖
OutputStream out = fs.create("dir/hello.txt", true);
PrintStream printOut = new PrintStream(out);
printOut.append("Hello FS !");
printOut.flush();
printOut.close();

// 读取 dir/hello.txt 文件内容
InputStream in = fs.open("dir/hello.txt");
String text = IOUtils.toString(in, Charset.forName("UTF-8"), true);
System.out.println(text);

// 查看文件状态
FileView stat = fs.stat("dir/hello.txt");
System.out.println("路径:" + stat.getPath());
System.out.println("所有人:" + stat.getOwner());
System.out.println("大小:" + stat.getLength());
System.out.println("最后修改时间:" + stat.getLastModifiedTime());
```
	从以上例子可以看出, 如果需要从不同的文件系统读取, 只需要修改 fsUri即可

## FileSystem 核心方法
| 方法 | 说明 |
|--------|--------|
| create | 创建一个新的文件输出流 |
| open | 打开一个文件输入流 |
| stat | 获取文件信息 |
| ls | 获取文件/目录下所有文件信息 |
| exists | 获取给定的文件是否存在 |

## FileSystems 工具类
	FileSystems 工具类提供一个从 uri 来解析创建 文件系统实例的快捷操作, 可以通过 getFileSystem  (uri) 来获取
### FSURI 说明
	FSURI 格式为: schema://[user[:password]@][:port]/path
    具体支持情况如下:
| 文件系统 | schema | 样例 |
|--------|--------|--------|
| 本地文件| local/file | local:///d:/dir, local:///mnt/dir |
| FTP | ftp | ftp://vacoor:passwd@127.0.0.1:99 |
| SFTP | sftp | sftp://vacoor:passwd@127.0.0.1 |
| 阿里云 OSS | aliyun | aliyun://accessId:accessKey@bucket.endpoint/path, aliyun://accessId:accessKey@oss-ch-sh.oss-cn-shanghai.aliyuncs.com |
| 腾讯云 COS | qcloud | qcloud://secretId:secretKey@bucket.region/path, qcloud://secretId:secretKey@bucketsh-1256188765.ap-shanghai |

### 不通过 URI 传递账号密码 及传递更多信息
	对于某些情况下,可能不希望通过 uri 来传递信息, 此时可以通过以下两个方法来传递这些信息
    getFileSystem(uri, user, password)/getFileSystem(uri, props)
```
	FileSystem.getFileSystem("sftp://127.0.0.1", "vacoor", "password")

    Properties props = new Properties();
    props.setProperty("user", "vacoor");
    props.setProperty("password", "password");
	FileSystem.getFileSystem("sftp://127.0.0.1", props)
```

## 更多说明
	额，没有更多了。
    考虑增加 “七牛云存储” 支持

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)