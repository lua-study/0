#JFinal_Authority

    采用 @Jfinal2.0 @Jfinal-Ext @Redis @Shrio @EhCache @Gson_ 
    @Easyui @Bootstarp  @Beetl @Druid @ECharts @HightChats @Anguarjs @Amazeui_ @FIS @Jade 等最新技术  
    可快速集成需要的功能到项目 
    本项目不断更新中 
    分支 master anguarjs版本    
    分支 easyui 已完事不再更新 
    这个项目的目的是为了学习 所以运用的都是最新的技术 从部署到运行都是一个学习的过程   

#AnguarJs 主分支
 
  界面 使用 @Amazeui_ 后台模版  
  更好的界面 更好的前端工作流程 最新的技术实践  
   anguarjs版本 已基本完工  
  响应式布局  

  访问地址： http://115.29.187.86:8081/ 

  登录 账号 密码  admin@admin.com  123456
  

  
  


# Easyui 分支
   easyui 版本 权限界面参考  @SyPro  
   分支 easyui 已完事不再更新 

  访问地址： http://115.29.187.86:8080/ 
  
  登录 账号 密码  admin	 123456
  
  



# easyui 分支部署

  切换到 easyui 分支查看


# anguarjs 分支部署 
  
  更新到JDK8 

  eclipse 直接导入项目  import->General-> Existing Project into workspace  
  
  建议使用 eclipse-for EE 运行 
  最新版本 使用maven 部署 导入后执行 maven install     jfinal-authority
  然后直接运行tomcat 或者用jetty运行 
  注意 eclipse 最新版自带maven 插件 如果没有请自行安装

  如果 找不到部分jar 需要用项目中的setting.xml 替换原因的maven 配置文件(可选)
  具体可看项目里面的启动说明
  
  更新具体部署说明 WIKI   部署说明  
  ----------------------------------------------------------------------------- 
  
  如果要修改前端页面代码需要先部署前端构建工具
  1. 安装 nodejs  并设置环境变量 在cmd 里面运行 npm 看看是否好使
  2. npm install -g fis3   
  3. npm install bower
  4. bower install 
  5. 进入 web-src/admin 目录 运行 fis3 release  (会提示需要选安装相关插件 npm install 安装即可) 部署前端工程到java-web 项目的webapp目录  


  如果有问题可以查看 fis 文档进行解决


# Docker 一键部署 
   
  1.安装好docker 环境
  2.进入项目目录运行脚本   build.sh -anaguar
  



# anguarjs 分支预览

  ![Screenshot 21](http://git.oschina.net/jayqqaa12/JFinal_Authority/raw/master/Screenshot/21.png "Screenshot 21")    
  ![Screenshot 22](http://git.oschina.net/jayqqaa12/JFinal_Authority/raw/master/Screenshot/22.png "Screenshot 22")    
  ![Screenshot 23](http://git.oschina.net/jayqqaa12/JFinal_Authority/raw/master/Screenshot/23.png "Screenshot 23")    
  ![Screenshot 25](http://git.oschina.net/jayqqaa12/JFinal_Authority/raw/master/Screenshot/25.png "Screenshot 25")    
  ![Screenshot 26](http://git.oschina.net/jayqqaa12/JFinal_Authority/raw/master/Screenshot/26.png "Screenshot 26")    







 
## 捐赠
如果您喜欢本项目  
认为本项目确实给您带来方便和帮助非常感谢  
您的捐赠，是我们前进的动力 

支付宝捐赠帐号 jayqqaa12@yahoo.com.cn

扫描二维码捐赠
![Screenshot 12shu-zfb](http://git.oschina.net/jayqqaa12/JFinal_Authority/raw/master/Screenshot/12shu-zfb.png "Screenshot 12shu-zfb")    

 


#其他开源项目  
# abase-reader android 开源阅读器   
# Abase android快速开发工具  

#关于作者 @12叔  

#联系方式 jfinalAuthority 交流群 173286972  


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)