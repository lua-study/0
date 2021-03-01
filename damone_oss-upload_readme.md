# oss-upload

#### 介绍
阿里云 OSS  文件上传

#### 安装教程

1. 安装 golang 开发环境， 版本大于1.5

2. 下载 阿里云 oss SDK
```sh
go get github.com/aliyun/aliyun-oss-go-sdk/oss
```
3. 下载 config
```sh
go get github.com/larspensjo/config
```
4. 交叉编译 upload
```sh
GOOS=linux      GOARCH=arm      go build -o upload-arm-linux        upload.go
GOOS=linux      GOARCH=amd64    go build -o upload-amd64-linux      upload.go
GOOS=windows    GOARCH=amd64    go build -o upload-amd64-windows    upload.go
```

#### 使用说明
1. 指令帮助
```sh
 ./upload-amd64-windows  -h
Usage of E:\project\viti\oss-upload\upload-amd64-windows:
  -c string
        General configuration file (default "config.ini")
  -d    When upload finished, delete local file
  -w string
        Upload work directory (default "./")
```

2. 参数 -c 指定 配置文件，默认 config.ini 文件， 配置内容如下：
```ini
[upload]
device_id       =  
oss_end_point   =  
oss_bucket      =  
oss_access_id   =  
oss_access_key  =  
```

3. 参数 -w 指定上传的本地目录， 默认当前目录

4. 参数 -d 指定上传完成后是否删除本地文件
```sh
./upload  -c data/passengers.ini  -w video/ -d
Transfer video//20190105_14-23-43_0.json Started, ConsumedBytes: 0, TotalBytes 29505.
Transfer video//20190105_14-23-43_0.json Data, ConsumedBytes: 29505, TotalBytes 29505, 100%.Transfer video//20190105_14-23-43_0.json Started, ConsumedBytes: 29505, TotalBytes 29505.
Upload 0: 20190105_14-23-43_0.json status: true
Upload video//20190105_14-23-43_0.json finished, to delete it
Transfer video//20190105_14-23-43_0.log Started, ConsumedBytes: 0, TotalBytes 11507.
Transfer video//20190105_14-23-43_0.log Data, ConsumedBytes: 11507, TotalBytes 11507, 100%.Transfer video//20190105_14-23-43_0.log Started, ConsumedBytes: 11507, TotalBytes 11507.
Upload 1: 20190105_14-23-43_0.log status: true
Upload video//20190105_14-23-43_0.log finished, to delete it
Transfer video//20190105_14-24-00_0.json Started, ConsumedBytes: 0, TotalBytes 36071.
Transfer video//20190105_14-24-00_0.json Data, ConsumedBytes: 36071, TotalBytes 36071, 100%.Transfer video//20190105_14-24-00_0.json Started, ConsumedBytes: 36071, TotalBytes 36071.
Upload 2: 20190105_14-24-00_0.json status: true
Upload video//20190105_14-24-00_0.json finished, to delete it
Transfer video//20190105_14-24-00_0.log Started, ConsumedBytes: 0, TotalBytes 13837.
Transfer video//20190105_14-24-00_0.log Data, ConsumedBytes: 13837, TotalBytes 13837, 100%.Transfer video//20190105_14-24-00_0.log Started, ConsumedBytes: 13837, TotalBytes 13837.
Upload 3: 20190105_14-24-00_0.log status: true
Upload video//20190105_14-24-00_0.log finished, to delete it
Transfer video//20190105_14-24-00_1.json Started, ConsumedBytes: 0, TotalBytes 35924.
Transfer video//20190105_14-24-00_1.json Data, ConsumedBytes: 35924, TotalBytes 35924, 100%.Transfer video//20190105_14-24-00_1.json Started, ConsumedBytes: 35924, TotalBytes 35924.
Upload 4: 20190105_14-24-00_1.json status: true
Upload video//20190105_14-24-00_1.json finished, to delete it
Transfer video//20190105_14-24-00_1.log Started, ConsumedBytes: 0, TotalBytes 13783.
Transfer video//20190105_14-24-00_1.log Data, ConsumedBytes: 13783, TotalBytes 13783, 100%.Transfer video//20190105_14-24-00_1.log Started, ConsumedBytes: 13783, TotalBytes 13783.
Upload 5: 20190105_14-24-00_1.log status: true
Upload video//20190105_14-24-00_1.log finished, to delete it

```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)