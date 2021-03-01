#  SpringBatch 示例模板工程 

## 主要技术：
    spring boot
    spring MVC
    spring batch
    spring data JPA
    spring data redis
    mysql


## 工程结构：
    project:
        sbin    #启动脚本
        src   #源文件
            assembly   #assembly插件打包 package.xml 文件目录
            main
                java java代码目录
                    com.sample.springbatch   #代码主目录
                        config   #项目配置目录
                        controller
                        job   #spring batch job相关代码目录
                            config      #job的基础配置目录
                            dao
                            demo        #demo批量作业目录
                            exception   #job中指定抛出的异常类
                            listenter   #job监听的基础类
                            mapper
                            sample      #job示例目录
                            service     #批量作业服务类  启动 暂停 停止
                        model
                        repository
                        scheduling      #作业调度
                        service
                        utils
                        RootApplication #启动文件
                resources    #配置资源文件目录
                    druid    #druid 配置
                    jobdata  #作业数据文件目录
                    static   #静态资源目录
                    templates #模板目录
            test    #test 目录
        pom.xml

## 示例：



## 参考：
    javaConfig示例：
        https://github.com/codecentric/spring-batch-javaconfig
        https://keyholesoftware.com/2015/06/29/spring-batch-javaconfig

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)