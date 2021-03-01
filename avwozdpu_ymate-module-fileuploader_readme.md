### YMP-FileUploader

> 文件上传及资源访问服务模块，特性如下：
> 
> - 支持文件指纹匹配，秒传；
> - 支持图片文件多种规则等比例压缩；
> - 支持视频文件截图；
> - 支持上传文件`ContentType`白名单过滤；
> - 支持主从负载模式配置；
> - 支持自定义响应报文内容(如:百度编辑器文件上传成功响应JSON报文结构)；
> - 支持自定义扩展文件存储策略；
> - 支持跨域上传文件及用户身份验证；

#### Maven包依赖

     
         net.ymate.module 
         ymate-module-fileuploader 
         1.0-SNAPSHOT 
     

### 模块配置参数说明

    #-------------------------------------
    # module.fileuploader 模块初始化参数
    #-------------------------------------
    
    # 节点标识符, 默认值: unknown
    ymp.configs.module.fileuploader.node_id=
    
    # 缓存名称前缀, 默认值: ""
    ymp.configs.module.fileuploader.cache_name_prefix=
    
    # 缓存数据超时时间, 可选参数, 数值必须大于等于0, 否则将采用默认
    ymp.configs.module.fileuploader.cache_timeout=
    
    # 是否开启代理模式, 默认值: false
    ymp.configs.module.fileuploader.proxy_mode=
    
    # 代理服务基准URL路径(若开启代理模式则此项必填), 必须以'http://'或'https://'开始并以'/'结束, 如: http://www.ymate.net/fileupload/, 默认值: 空
    ymp.configs.module.fileuploader.proxy_service_base_url=
    
    # 上传文件存储根路径, 默认值: ${root}/upload_files
    ymp.configs.module.fileuploader.file_storage_path=
    
    # 静态资源引用基准URL路径, 必须以'http://'或'https://'开始并以'/'结束, 如: http://www.ymate.net/static/resources/, 默认值: 空(即不使用静态资源引用路径)
    ymp.configs.module.fileuploader.resources_base_url=
    
    # 是否允许自定义缩略图尺寸, 默认值: false
    ymp.configs.module.fileuploader.allow_custom_thumb_size=
    
    # 缩略图尺寸列表, 该尺寸列表在允许自定义缩略图尺寸时生效, 若列表不为空则自定义尺寸不能超过此范围, 如: 600_480、1024_0 (0表示等比缩放, 不支持0*0), 默认值: 空
    ymp.configs.module.fileuploader.thumb_size_list=
    
    # 缩略图清晰度, 如: 0.70f, 默认值: 0f
    ymp.configs.module.fileuploader.thumb_quality=
    
    # 允许上传的文件ContentType列表, 如: image/png|image/jpeg, 默认值: 空, 表示不限制
    ymp.configs.module.fileuploader.allow_content_types=

#### 示例代码：

- 上传文件，以POST方式请求URL地址：

        http://localhost:8080/uploads/push
    
    > 参数说明：
    >
    > - file: 上传文件流数据；
    > - type: 指定请求结果处理器，若未提供则采用默认，可选值：`fileupload`、`baidu` 

- 文件指纹匹配，以POST方式请求URL地址：

        http://localhost:8080/uploads/match
    
    > 参数说明：
    >
    > - hash: 文件哈希值(MD5)，必选参数；
    
    返回值：若匹配成功则返回该资源访问URL地址；
    
        {"ret":0, "matched":true, "data":"http://localhost:8080/uploads/resources/image/6146aaafbadb1f3ada6b12190e8c4771"}

- 文件资源访问，以GET方式请求URL地址：

        http://localhost:8080/uploads/resources/{type}/{hash}

    > 参数说明：
    >
    > - type: 文件类型，必选参数，可选值：`image`、 `video`、`audio`、`text`、`application`、`thumb`
    > - hash: 文件哈希值(MD5)，必选参数；
    >
    > **注**：若需要强制浏览器下载资源，只需在请求参数中添加`?attach`即可；

#### One More Thing

YMP不仅提供便捷的Web及其它Java项目的快速开发体验，也将不断提供更多丰富的项目实践经验。

感兴趣的小伙伴儿们可以加入 官方QQ群480374360，一起交流学习，帮助YMP成长！

了解更多有关YMP框架的内容，请访问官网：http://www.ymate.net/

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)