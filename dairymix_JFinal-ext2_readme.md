# JFinal-ext2

基于JFinal 2.0加入一些kit，它们有

1. 扩展JFinalConfig=> JFinalConfigExt

	1.1 给每一个app设置一个name；

	1.2 从配置文件中获取文件的保存路径；

	1.3 获取devmode；

	1.4 打包DruidPlugin和ActiveRecordPlugin；

	以上让你的config更加轻便

2. 加入ActionExtentionHandler
	更方面的伪静态处理

3. 加入 NotFoundActionInterceptor 当找不到对应的 action 时，fire 404

4. com.jfinal.ext2.kit

	3.1 DateTimeKit;

	3.2 DDLKit;

	...

5. com.jfinal.ext2.validate.ValidatorExt

	默认开启短路，校验失败403

6. 加入多个文件上传的FileRenamePolicy
	
	6.1 CustomNameFileRenamePolicy 自定义文件名称
	6.2 CustomParentDirFileRenamePolicy 自定义上级目录名称
	6.3 DateRandomFileRenamePolicy 按照时间分割目录
	6.4 RandomFileRenamePolicy 随机文件名称


Demo ： [http://git.oschina.net/brucezcq/JFinal-Ext2-Demo](http://git.oschina.net/brucezcq/JFinal-Ext2-Demo)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)