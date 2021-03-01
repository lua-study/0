# WDA v1.2.3 
支持通过附件的url地址提交预览任务

### ** :tw-1f3ee: 注意：与开源版WCP集成请选用v1.2.2版本，新版本不保证兼容WCP** 

### 使用方式
1. 使用WDA服务前，需要先安装openoffice，必须安装在默认目录下，不要修改安装目录（如果必须修改目录则需要手动配置wda的openoffice启动命令）
2. web主模块为wda-web 可部署于tomcat7下
3. 启动服务后访问http://127.0.0.1:8080/wda（如端口为8080）
4. http://127.0.0.1:8080/wda/submit.jsp地址提交附件，可通过本磁盘路径或远程附件的URL地址来提交预览文件转换任务
5. http://127.0.0.1:8080/wda/index.jsp地址用来访问预览文件，key为生成预览任务时填写的key或远程资源附件的URL地址
![1.提交预览文件转换任务](https://images.gitee.com/uploads/images/2020/0423/144233_4aabb114_24089.png "提交预览任务.png")
![2.完成提交](https://images.gitee.com/uploads/images/2020/0423/144255_58c6db21_24089.png "提交后.png")
![3.访问预览文件](https://images.gitee.com/uploads/images/2020/0423/144314_e9f3bce2_24089.png "访问预览文件.png")
![4.默认有多种预览方式，可选一种方式进行预览](https://images.gitee.com/uploads/images/2020/0423/144333_850a9081_24089.png "查看预览文件.png")
### 注意
- 在web-inf/lib下是项目依赖的jar，有些jar文件需要手动导入
- 需要在服务器上安装openoffice服务，测试环境使用的是openoffice4，启动wda服务器注意先在config.properties中配置openoffice4的启动命令


### 配置文件docTypeConf.xml
![输入图片说明](http://git.oschina.net/uploads/images/2015/1129/184440_e50ee859_24089.png "在这里输入图片标题")

- conf/files:被转换为的文件类型 exname为支持的文件类型名称 filename为生成文件名filename的path参数为文件相对路径
- conf/types:文件转换关系对照
- conf/types/name:源文件后缀名
- conf/types/target:目标文件类型，可以生成多种,需要与conf/files/file/exname一致/

				
### 配置文件config.properties
![输入图片说明](http://git.oschina.net/uploads/images/2015/1129/184507_16248aba_24089.png "在这里输入图片标题")

- config.file.dir.path:文件存储地址，需要配置到webroot下
- config.server.openoffice.cmd:openoffice的soffice服务启动命令
- config.rmi.port:rmi绑定端口
							
### RMI调用
```
WdaAppInter personService = (WdaAppInter) Naming.lookup("rmi://127.0.0.1:8888/wda");
personService.generateDoc("1234", new File("D:\\doc\\1.docx"));
```
### com.farm.wda.inter.WdaAppInter
```
/**
     * 开始生产WEB文档
     *
     * @param key
     *            文档关键字，后续通过它调用相关资源
     * @param file
     *            原文件
     * @param htmlinfo
     *            被显示的html信息（如文件名称等）
     * @throws ErrorTypeException
     * @throws RemoteException
     */
    public void generateDoc(String key, File file, String htmlinfo) throws ErrorTypeException, RemoteException;

    /**
     * 开始生产WEB文档
     *
     * @param key
     *            文档关键字，后续通过它调用相关资源
     * @param file
     *            原文件
     * @param fileTypeName
     *            扩展名
     * @param htmlinfo
     *            被显示的html信息（如文件名称等）
     * @throws ErrorTypeException
     * @throws RemoteException
     */
    public void generateDoc(String key, File file, String fileTypeName, String htmlinfo)
            throws ErrorTypeException, RemoteException;

    /**
     * 获得可以被转换的文件类型
     *
     * @return
     */
    public Set  getSupportTypes() throws RemoteException;

    /**
     * 文档是否已经生成完毕
     *
     * @param key
     * @return
     * @throws ErrorTypeException
     */
    public boolean isGenerated(String key, String doctype) throws ErrorTypeException, RemoteException;

    /**
     * 文档是否有日志记录
     *
     * @param key
     * @return
     * @throws ErrorTypeException
     */
    public boolean isLoged(String key) throws RemoteException;

    /**
     * 删除日志（通过日志判断是否生成过文档时，可以通过此方法重新生成文档）
     *
     * @param key
     * @return
     * @throws ErrorTypeException
     */
    public void delLog(String key) throws RemoteException;

    /**
     * 获得日志地址
     *
     * @param key
     * @return
     */
    public String getlogURL(String key) throws RemoteException;

    /**
     * 获得文档文本字符串
     *
     * @param key
     * @return
     * @throws ErrorTypeException
     */
    public String getText(String key) throws ErrorTypeException, RemoteException;

    /**
     * 获得文档信息字符串
     *
     * @param key
     * @return
     * @throws ErrorTypeException
     */
    public String getInfo(String key) throws ErrorTypeException, RemoteException;

    /**
     * 获得在线文档浏览的URL
     *
     * @param key
     * @param exname
     * @return
     * @throws ErrorTypeException
     */
    public String getUrl(String key, String docType) throws ErrorTypeException, RemoteException;
```
### 演示
演示地址：[http://www.wcpdoc.com/webspecial/home/Pub2c909b2b65e0f2850165e0fb5600002a.html)

在wcp中集成了wda的功能，通过wcp的连接展示wda系统

![输入图片说明](http://git.oschina.net/uploads/images/2015/1126/113716_0338142e_24089.png "在这里输入图片标题")

如图，点击预览后进入wda系统

![输入图片说明](http://git.oschina.net/uploads/images/2015/1126/113548_d2957986_24089.png "在这里输入图片标题")


### 开源项目推荐
	
> WCP:知识管理系统 [https://gitee.com/macplus/WCP](https://gitee.com/macplus/WCP)

> WDA:文件转换组件（附件在线预览）[https://gitee.com/macplus/WDA](https://gitee.com/macplus/WDA)

> WTS:在线答题系统 [https://gitee.com/macplus/WTS](https://gitee.com/macplus/WTS)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)