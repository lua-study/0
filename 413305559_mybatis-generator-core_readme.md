#mybatis-generator-core
使用说明：
启动入口：org.mybatis.generator.api.StartUp

generatorConfigA ：配置文件，直接生成在当前工具中的ibatisData目录下，用于测试

generatorConfigB：配置文件，直接生成在所制定的实际工程目录下，用于开发

注意：需要修改generatorConfigA、generatorConfigB文件中绝对路径为你使用的真实路径；如：targetPackage、targetProject、jdbcConnection、classPathEntry等参数



以上工具修改过源码，修改如下：

1：将原有实体类生成的英文注释修改为数据库中的中文注释


2：将原有生成的Dao接口后面的Mapper更改为Dao;如：UserMapper  修改为：UserDao;


3:生成的配置文件和Dao中去除insert方法和updateById方法,因为insertSelective和updateByPrimaryKeySelective完全可以满足我们的需求


4：强制生成的所有文件格式为UTF-8

5.将生成的Mapper修改为Dao，更适合国内的开发环境

6.为生成的Dao方法中添加中文注释

7.将原有Example相关示例类修改为Param

8.增加分页插件，自动生成分页SQL

9.注释掉使用不到的接口

10.增加分页插件和BaseDao插件
   ```
		 
			 
			  
			 
			  
		 
		
		 
			 
			  
		 
```
   注：如果需要使用，将这两个配置到generatorConfig.xml中即可；BaseDao文件不是自动生成的，需要手动将提供的BaseDao.java文件复制到自己对应的目录
      BaseDao.java文件目录：```org.mybatis.generator.codegen.mybatis3.javamapper.elements.BaseDao;```

示例：
![输入图片说明](http://git.oschina.net/uploads/images/2016/1114/182955_f1e5b91c_303236.png "在这里输入图片标题")

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)