# clism-be

#### 项目介绍

The back-end part for clism.

2018夏季Dorahacks创新大赛，项目clism的后端接口部分。

## 响应

#### 当请求成功时，返回以下内容

+ Response 200

        {
            "success": 1,
            "data": {
                ...
            }
        }

#### 当请求失败时，返回以下内容

+ Response 200

        {
            "success": 0,
            "err_msg": "报错信息"
        }

## 接口列表

[图像风格迁移](#post_image) `POST {base_url}/api/image`

## 接口详情

  

### 图像风格迁移 `POST {base_url}/api/image`

+ Request

        {
            "image": "图像数据，base64编码，支持jpg和png格式，图像最好不要过大"
            "style": "迁移图像的风格类型编号，具体见风格类型表"
        }

+ Response 200

        {
            "success": 1,
            "data": {
                "image": "图像风格迁移完毕的风格图像，base64编码"
            }
        }

## 风格类型表

| 类型编号 | 风格名称 |
| :---: | :---: |
| 1 | cubist |
| 2 | denoised_starry |
| 3 | feathers |
| 4 | mosaic |
| 5 | scream |
| 6 | udnie |
| 7 | wave |


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)