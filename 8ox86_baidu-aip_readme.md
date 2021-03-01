# composer 安装PHP SDK

添加以下到你的composer.json中：


```
    "repositories": {
        "baidu/aip" : {
          "type": "git",
          "url": "https://gitee.com/8ox86/baidu-aip.git"
        }
    },
```



```
"baidu/aip": "dev-master"
```


最后看起来大概像：
```json
    "repositories": {
        "packagist": {
            "type": "composer",
            "url": "https://packagist.phpcomposer.com"
        },
        "baidu/aip" : {
          "type": "git",
          "url": "https://gitee.com/8ox86/baidu-aip.git"
        }
    },
    "require": {
        "php": ">=7.1.0",
        "baidu/aip": "dev-master"
    }

```



## 目录结构
```
  ├── AipOcr.php                // OCR
  ├── AipNlp.php                // NLP
  ├── AipFace.php               // 人脸
  ├── AipImageCensor.php        // 图像审核
  ├── AipImageClassify.php      // 图像识别
  ├── AipImageSearch.php        // 图像搜索
  ├── AipKg.php                 // 知识图谱
  ├── AipSpeech.php             // 语音
  └── lib
      ├── AipHttpClient.php        //内部http请求类
      ├── AipBCEUtil.php           //内部工具类
      └── AipBase                  //Aip基类
```

**支持 PHP版本：5.3+**

**安装步骤如下：**

1. 下载PHP SDK。

2. 复制```Aip*.php```以及```lib/*```到工程。

3. require_once '对应服务';


# 使用文档

参考[官方网站](http://ai.baidu.com/docs#/Begin/top)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)