   

# Capturer

### 说明

Capturer 可以截取任意网站上的内容，即使这些内容是由异步加载得到。没有 UI，一条命令搞定所有。

支持自定义分辨率截取、完整页面截取、输出文件或Base64编码字符串。

### 安装

保证本地有 `nodeJS` 环境。

`git clone` 本仓库。

根目录执行 `npm install` 安装依赖。

根目录执行 `node capture.js -u http://www.google.com` 即可在 `output` 文件夹中生成图片文件。

### 参数

`-u` 必须，需要截取的 URL 地址。

`-size` 可选，需要截取的图像大小，格式必须为 `width*height`，默认为 `1280*720`。

`-o` 可选，图像输出格式，值有两种： `file` 为输出文件（默认此参数），`base64` 为输出图片经过 base64 编码后的字符串。

### 开源协议

遵循 [MulanPSL1.0](https://license.coscl.org.cn/MulanPSL/) 开源协议。


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)