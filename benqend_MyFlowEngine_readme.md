支持以下类型

事件:启动事件、结束事件

网关:并行网关、排它网关、包容网关

顺序流:有条件顺序流、无条件顺序流

任务:ServiceTask任务





--------使用方法--------

1)通过spring来构造MyEngine单例


2)解析流程

        // 解析
        Resource resource = null;

        resource = new DefaultResourceLoader().getResource("engine.xml");

        ProcessDefinition processDefinition = engine.parse(resource);


3)部署流程生成实例

            ProcessInstance processInstance = engine.deploy(processDefinition);


4)运行实例

            engine.run(processInstance);



---TODO

1)内存使用上可以进一步减少内存开销

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)